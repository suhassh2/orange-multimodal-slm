# orange-multimodal-slm
# Multimodal Fine-Tuning with Small Language Models (SLMs)

## Overview

This project demonstrates **multimodal fine-tuning** using a Small Language Model (SLM) for an image-to-text task.
A BLIP image captioning model was fine-tuned using the **RICO Screen2Words** dataset.

The goal is to generate captions describing UI screens.

---

## Dataset

Dataset used:

RICO Screen2Words
https://huggingface.co/datasets/rootsautomation/RICO-Screen2Words

The dataset contains mobile application screenshots paired with captions describing the interface.

Example caption:
"pop up displaying calendar to select date"

---

## Base Model

Base model used:

BLIP Image Captioning Base
https://huggingface.co/Salesforce/blip-image-captioning-base

BLIP is a multimodal model capable of generating text descriptions from images.

---

## Fine-Tuning Method

Fine-tuning was performed using **LoRA (Low Rank Adaptation)**.

LoRA allows efficient fine-tuning by training a small number of parameters while keeping most of the base model frozen. This reduces GPU memory usage and speeds up training.

---

## Training Configuration

GPU: NVIDIA Tesla T4
Epochs: 1
Batch Size: 4
Learning Rate: 2e-5
Training Samples: 500

The model was trained using Hugging Face Transformers and PEFT.

---

## Hugging Face Model

The trained model is available on Hugging Face:

https://huggingface.co/suhas2468/rico-blip-lora-model

This repository contains the fine-tuned model and processor required for inference.

---

## Example Inference

```python
from transformers import pipeline

pipe = pipeline(
    "image-to-text",
    model="suhas2468/rico-blip-lora-model"
)

result = pipe("example_image.png")
print(result)
```

---

## Repository Structure

orange-multimodal-slm

* orange_multimodal_training.ipynb → Training notebook
* README.md → Documentation

---

## How to Run

1. Clone the repository
2. Install dependencies

```
pip install transformers datasets peft accelerate bitsandbytes
```

3. Run inference using the trained model.

---

## Conclusion

This project demonstrates a complete multimodal fine-tuning pipeline including:

* dataset loading
* preprocessing
* LoRA fine-tuning
* training on a T4 GPU
* model deployment to Hugging Face
* reproducible code in a GitHub repository
