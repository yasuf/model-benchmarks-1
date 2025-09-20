# Receipt Total Extraction Model Benchmarks

A benchmarking project comparing vision-language models for extracting total amounts from receipt images.

## Overview

This repository evaluates the performance of different vision-language models on the task of extracting total amounts from receipt images. The project currently benchmarks:

- **Microsoft Moondream2** (`vikhyatk/moondream2`) - A general-purpose vision-language model
- **IBM Granite Docling** (`ibm-granite/granite-docling-258M`) - A specialized document understanding model

## Dataset

The evaluation uses a dataset of 200+ receipt images with ground truth labels:
- **Location**: `images/receipt_dataset/`
- **Format**: JPG images with corresponding CSV labels
- **Labels**: `labels.csv` contains filename and total amount pairs
- **Sample images**: Additional receipt examples in the `images/` directory

## Models Evaluated

### 1. Microsoft Moondream2
- **Model ID**: `vikhyatk/moondream2`
- **Revision**: `2025-06-21`
- **Type**: General vision-language model
- **Device**: Optimized for Apple Silicon (MPS)

### 2. IBM Granite Docling
- **Model ID**: `ibm-granite/granite-docling-258M`
- **Type**: Specialized document understanding model
- **Size**: 258M parameters

## Installation

### Prerequisites
- Python 3.11
- pipenv (recommended) or pip

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yasuf/model-benchmarks-1
cd model-benchmarks-1
```

2. Install dependencies using pipenv:
```bash
pipenv install
pipenv shell
```

Or using pip:
```bash
pip install transformers torch pillow accelerate pandas ipykernel
```

## Usage

### Running Benchmarks

Open the Jupyter notebook:
```bash
jupyter notebook models_benchmarks.ipynb
```

### Evaluation Process

The evaluation:
- Loads receipt images from the dataset
- Prompts models with: *"What is the total amount of the receipt? Return only the amount with the currency symbol, no other text."*
- Compares model predictions against ground truth labels
- Calculates accuracy metrics
- Provides detailed per-image results

### Sample Evaluation Size

By default, the evaluation runs on 100 images. Modify the `evaluation_size` variable to test on more or fewer samples.

## Results

The benchmark provides:
- **Per-image accuracy**: Real-time accuracy updates during evaluation
- **Final accuracy**: Overall model performance percentage
- **Detailed logging**: Model predictions vs. ground truth for each image

## Acknowledgments

- Receipt dataset [ExpressExpense](https://expressexpense.com/blog/free-receipt-images-ocr-machine-learning-dataset/)
