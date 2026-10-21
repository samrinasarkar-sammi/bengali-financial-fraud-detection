# Bengali Financial Fraud Text Classification

Research project exploring machine learning and deep learning for classifying Bengali-language accounts of suspected fraud involving bKash mobile financial services.

## Overview

Mobile financial scams are often described in short, informal Bengali texts. This project investigates text preprocessing, feature extraction and classification methods for distinguishing the dataset's two annotated categories: **Fraud** and **Partial Fraud**.

The source texts include fraud-related comments and experiences collected by team members from online platforms. They should not all be interpreted as original SMS messages sent by scammers.

## My contribution

I am **Samrina Sarkar Sammi**. My contributions to this collaborative project were:

- Coding the text-processing and classification experiments.
- Working on the experimental analysis and documenting the methodology and results.
- Writing sections of the research manuscript.

**Dataset collection and labelling were carried out by other team members.** I do not claim authorship of their data-collection work.

The related Research Square preprint does not list me as an author. This portfolio describes my implementation and manuscript-writing contribution; the preprint's author list is preserved in the reference below.

## Dataset

The working file supplied for this project has the following structure:

| Item | Description |
| --- | --- |
| Working filename | `Bkash Fraud Analysis.csv` |
| Records | 520 |
| Text column | `Comments` |
| Label column | `Label` |
| Fraud | 260 records |
| Partial Fraud | 260 records |
| File encoding | UTF-16 |
| Separator | Tab (`\t`), despite the `.csv` extension |

These counts describe the supplied working file before any further cleaning or filtering. The related preprint describes a 500-record dataset. The relationship between the working file and the final experimental subset needs to be checked against the original notebooks.

### What the labels mean

The team draft describes **Fraud** as accounts of successful deception or unauthorised financial loss. **Partial Fraud** includes unsuccessful attempts and other reported unauthorised-access situations. These are the team's operational labels and have some conceptual overlap.

This is therefore **not a verified fraud-versus-legitimate-message dataset**. The label definitions and ambiguous cases should be reviewed before extending the work.

### Data access

The original dataset is not redistributed with this README. Public release requires confirmation of the team's sharing permissions and a review of identifying information in the texts. The preprint's licence should not be assumed to license the separate dataset or source code.

If you have authorised access to the original working file, it can be read with:

```python
from pathlib import Path
import pandas as pd

dataset_path = Path("data") / "Bkash Fraud Analysis.csv"
df = pd.read_csv(dataset_path, encoding="utf-16", sep="\t")

print(df.shape)
print(df["Label"].value_counts())
```

## Methods explored

The research draft documents the following approaches. Their exact implementation and parameters should be checked against the accompanying code.

### Text preparation

- Duplicate and short-text filtering.
- Bengali text cleaning and punctuation handling.
- Stopword removal and stemming experiments.
- TF-IDF features, including n-gram experiments, for classical classifiers.
- Tokenisation and sequence preparation for neural models.

### Models

| Family | Models documented in the draft |
| --- | --- |
| Classical machine learning | Logistic Regression, Decision Tree, Random Forest, Multinomial Naive Bayes, K-Nearest Neighbours, RBF Support Vector Machine and SGD classifier |
| Deep learning | CNN, LSTM and BiLSTM |
| Hybrid architectures | CNN-LSTM and CNN-BiLSTM |

### Evaluation

The draft describes held-out evaluation using accuracy, precision, recall, F1-score and confusion matrices. It describes an 80/20 train/test split for the classical models and additional validation during neural-model training.

Before presenting a reproducible benchmark, the code should establish the exact filtered dataset, label encoding, random seed, split indices and validation procedure. Text vectorisers and tokenisers must be fitted on training data only.

## Results and reproducibility

This README does not present the historical manuscript scores as independently reproduced results. The draft contains inconsistencies between some model labels, tables and narrative summaries. No experiment notebooks were available during preparation of this README.

Verified results should be added after checking the original code or rerunning the experiments, with:

- The number of records used after preprocessing.
- The split strategy, random seed and test-set size.
- Accuracy and explicitly identified macro or weighted F1.
- Per-class precision and recall, and a confusion matrix.
- Dependency versions and instructions matching the actual repository files.

## Limitations

- The working dataset is small, so scores may vary substantially across train/test splits.
- Labels may overlap and require clearer annotation guidelines.
- Online comments about scams differ from real incoming transaction messages.
- Bengali spelling variation and informal language complicate preprocessing.
- Stronger evidence would require repeated stratified evaluation, duplicate checks and testing on an independent dataset.

This is an exploratory research project, not a deployed financial-fraud prevention system. It has no official affiliation with bKash.

## Related preprint

Sharun Akter Khushbu, Fariha Tasmin Jaigirdar, Adnan Anwar and Ohidujjaman Tuhin. **Be Aware of Your Text Messages: Fraud Attempts Identification Based on Semantic Sequential Learning for Financial Transactions through Mobile Services in Bangladesh.** Research Square, version 1, 2024.

- [Read the preprint](https://www.researchsquare.com/article/rs-4659691/v1)
- [DOI: 10.21203/rs.3.rs-4659691/v1](https://doi.org/10.21203/rs.3.rs-4659691/v1)

Research Square identifies this version as a preprint that has not been peer reviewed by a journal. The preprint is shared under CC BY 4.0; that licence does not by itself establish the release terms for this repository's code or data.

## Acknowledgements

Thanks to the team members responsible for collecting and labelling the dataset, and to the research collaborators and supervisors involved in the wider study.

## Contact

**Samrina Sarkar Sammi**

- [GitHub](https://github.com/samrinasarkar-sammi)
- [Portfolio](https://samrinasarkar-sammi.github.io/)
- [Email](mailto:samrinasarkar@gmail.com)
