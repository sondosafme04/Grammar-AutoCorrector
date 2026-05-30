# English Grammar AutoCorrector (NLP Project)

An end-to-end Natural Language Processing (NLP) project for detecting and correcting English grammatical errors using Deep Learning.

The project compares two different architectures:

1. CNN-BiLSTM
2. T5-small Transformer

The system is trained on the C4_200M Synthetic Grammatical Error Correction Dataset and deployed using Streamlit.

---

## Project Overview

Grammatical Error Correction (GEC) is an NLP task that automatically detects and fixes grammar mistakes in text.

Example:

Input:
```
she go to school yesterday
```

Output:
```
she went to school yesterday
```

This project implements and compares:

- A custom CNN-BiLSTM model
- A pre-trained Transformer model (T5-small)

---

## Dataset

### C4_200M Synthetic GEC Dataset

Dataset contains pairs of:

- Incorrect sentences (Source)
- Corrected sentences (Target)

For computational efficiency:

- Only the first shard was used
- First 100,000 samples were loaded

Dataset format:

| Source | Target |
|----------|----------|
| she go school | she goes to school |
| i has a car | i have a car |

---

## Project Pipeline

### 1. Data Collection

- Load dataset
- Select first shard
- Limit data to 100K samples

### 2. Data Exploration (EDA)

- Sentence length analysis
- Distribution visualization
- Statistical summaries

### 3. Data Preprocessing

Applied:

- Lowercasing
- Whitespace normalization
- Train/Validation/Test split

Split ratio:

- Train: 80%
- Validation: 10%
- Test: 10%

---

## Model 1: CNN-BiLSTM

Architecture:

```
Embedding
   ↓
Conv1D
   ↓
MaxPooling
   ↓
Bidirectional LSTM
   ↓
Fully Connected Layer
   ↓
Output Vocabulary
```

### Components

- Embedding Layer
- CNN Feature Extraction
- Max Pooling
- Bidirectional LSTM
- Dense Output Layer

### Advantages

- Learns local grammatical patterns
- Captures contextual information
- Lightweight compared to Transformers

---

## Model 2: T5-small Transformer

T5 treats grammar correction as a text-to-text task.

Example:

Input:

```
fix grammar: she go to school yesterday
```

Output:

```
she went to school yesterday
```

### Features

- Pre-trained Transformer
- Transfer Learning
- Attention Mechanism
- Better language understanding

---

## Training

### CNN-BiLSTM

- Optimizer: Adam
- Loss Function: CrossEntropyLoss
- Epochs: 10

### T5-small

Fine-tuned using Hugging Face Transformers.

---

## Evaluation Metrics

The models were evaluated using:

### BLEU Score

Measures similarity between generated text and reference text.

Higher is better.

### Exact Match Accuracy

Measures percentage of perfectly corrected sentences.

Higher is better.

---

## Results

The project compares:

| Metric | CNN-BiLSTM | T5-small |
|----------|----------|----------|
| BLEU Score | Evaluated | Evaluated |
| Accuracy | Evaluated | Evaluated |
| Training Time | Recorded | Recorded |

### Observation

T5-small achieved superior grammatical correction performance due to its pre-trained Transformer architecture and contextual understanding.

---

## Deployment

The best-performing model was deployed using Streamlit.

Run locally:

```bash
streamlit run app.py
```

---

## Technologies Used

### Programming Language

- Python

### Libraries

- PyTorch
- Transformers
- Hugging Face Datasets
- Evaluate
- Scikit-learn
- NumPy
- Pandas
- Matplotlib
- Streamlit
- NLTK

---

## Project Structure

```
.
├── nlp-grammar.ipynb
├── app.py
├── cnn_bilstm_grammar.pt
├── t5_grammar_best/
├── README.md
└── requirements.txt
```

---

## Future Improvements

- Use larger Transformer models (T5-base, FLAN-T5)
- Train on full C4_200M dataset
- Add grammar error highlighting
- Deploy on cloud platforms
- Support multiple languages

---

## Conclusion

This project demonstrates how Deep Learning can be applied to Grammatical Error Correction (GEC).

The comparison between CNN-BiLSTM and T5-small shows the effectiveness of Transformer-based models in understanding and correcting grammatical errors, making T5-small the preferred solution for deployment.

---

## Author

NLP Graduation Project

English Grammar AutoCorrector
