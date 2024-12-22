# LawAi: Fine-Tuned LLaMA-3.1 8B Model for Indian Legal Texts

**LawAi** is a fine-tuned version of the LLaMA-3.1 (8B) model, specifically tailored for Indian legal contexts. Leveraging the datasets "Alok2304/Indian_Law_Reformatted_Dataset_v2.0" and "kshitij230/Indian-Law," this model provides high-quality understanding and generation capabilities for legal texts.

---

## 🛠️ Model Details

- **Base Model:** [LLaMA-3.1 (8B)](https://huggingface.co/models)
- **Fine-Tuned Datasets:**
  - [Alok2304/Indian_Law_Reformatted_Dataset_v2.0](https://huggingface.co/datasets/Alok2304/Indian_Law_Reformatted_Dataset_v2.0)
  - [kshitij230/Indian-Law](https://huggingface.co/datasets/kshitij230/Indian-Law)
- **Model Name:** LawAi
- **Primary Task:** Legal text comprehension and generation
- **Training Objective:** Improve performance on Indian legal text processing, including case summarization, statute analysis, and legal argument generation.

---

## 🔍 Features

- Supports **text generation** and **comprehension** for Indian legal contexts.
- Handles diverse legal text types, including statutes, case law, and legal arguments.
- Provides robust support for tasks like summarization, Q&A, and legal text drafting.

---



## 📦 how to run ?


```code
if False:
    from unsloth import FastLanguageModel
    model, tokenizer = FastLanguageModel.from_pretrained(
        model_name = "lawai_model",
        max_seq_length = max_seq_length,
        dtype = dtype,
        load_in_4bit = load_in_4bit,
    )
    FastLanguageModel.for_inference(model) 
# alpaca_prompt = You MUST copy from above!

inputs = tokenizer(
[
    alpaca_prompt.format(
        "What is a penal code?", # instruction
        "", # input
        "", # output
    )
], return_tensors = "pt").to("cuda")

from transformers import TextStreamer
text_streamer = TextStreamer(tokenizer)
_ = model.generate(**inputs, streamer = text_streamer, max_new_tokens = 128)
```

### output:
```text
<|begin_of_text|>Below is an instruction that describes a task or a question. Write a response that appropriately completes the request.

### Instruction:
What is a penal code?

### Response:
A penal code is a comprehensive set of laws that defines criminal offenses and prescribes punishments for them. It outlines the various crimes that are considered illegal and punishable by law, including offenses against the state, public order, and individual rights. The penal code is an essential component of the legal system in many countries, providing a framework for the enforcement of criminal justice.<|end_of_text|>
```
