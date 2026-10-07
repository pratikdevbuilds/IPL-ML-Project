# IPL ML Project — Toss Match Outcome Prediction

## Overview

This project uses IPL match data from **2008–2024** to build a machine learning classification model that predicts whether the **toss winner also wins the match**.

> **Important:** This is a **post-toss prediction task** because toss-related features are included. It is not a pre-toss match-winner prediction system.

## Objective

- `True` → toss winner also won the match
- `False` → toss winner did not win the match

## Dataset

- Period: **2008–2024**
- Matches: **1,095**
- Main inputs: season, city, match type, venue, teams, toss winner and toss decision

## Workflow

```text
IPL Dataset
   ↓
Data Cleaning
   ↓
EDA
   ↓
Feature Selection
   ↓
One-Hot Encoding
   ↓
Train/Test Split
   ↓
Logistic Regression
   ↓
Decision Tree
   ↓
Model Evaluation
   ↓
Model Saving/Loading
   ↓
New Match Prediction
```

## Models

### Logistic Regression
Used as a baseline classification model.

### Decision Tree
An unrestricted Decision Tree was tested first.

### Final model
The best tested version in this project is:

```python
DecisionTreeClassifier(max_depth=9, random_state=42)
```

| Metric | Result |
|---|---:|
| Training Accuracy | 65.64% |
| Testing Accuracy | 57.53% |
| Majority-class baseline | 51.14% |

The final model performs somewhat better than the baseline, but its predictive performance is still limited.

## Features

The model uses:

- Season
- City
- Match type
- Venue
- Team 1
- Team 2
- Toss winner
- Toss decision

Post-match information such as the actual winner, result, player of the match and result statistics is excluded from the model inputs.

## Model Saving

```python
joblib.dump(dt_model_9, "ipl_toss_match_model.pkl")
```

The saved model can be loaded with:

```python
loaded_model = joblib.load("ipl_toss_match_model.pkl")
```

## Example Prediction

The notebook includes an example using a 2024 Mumbai match at Wankhede Stadium between Mumbai Indians and Chennai Super Kings, with Mumbai Indians as the toss winner choosing to field.

The saved model predicted:

```text
Toss winner will NOT win the match
```

## Project Structure

```text
IPL-ML-Project/
│
├── data_load.ipynb
├── ipl_toss_match_model.pkl
├── matches_2008-2024.csv
├── README.md
└── .gitignore
```

## Skills Demonstrated

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Data cleaning
- Exploratory Data Analysis
- Feature selection
- One-hot encoding
- Train/test splitting
- Logistic Regression
- Decision Trees
- Classification metrics
- Confusion matrix
- Model saving/loading with Joblib
- End-to-end ML workflow

## Limitations

This is a learning and portfolio project. A testing accuracy of 57.53% is not strong enough for reliable real-world prediction.

No-result matches also require special care because they do not have a match winner.

## Author

**Pratik Patidar**  
B.Tech CSE Student | AI/ML Enthusiast
