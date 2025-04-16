# Titanic Survival Analysis & Prediction
End‑to‑end data‑science pipeline that transforms the Titanic passenger manifest into
business‑ready insights and a production‑grade machine‑learning model.

---

## 📑 Table of Contents
1. [Project Motivation](#project-motivation)
2. [Dataset](#dataset)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [Feature Engineering](#feature-engineering)
5. [Modeling](#modeling)
6. [Results](#results)
7. [Dashboard](#dashboard)
8. [Project Structure](#project-structure)
9. [Quick Start](#quick-start)
10. [Future Work](#future-work)
11. [License & Acknowledgements](#license--acknowledgements)
12. [Hebrew Summary](#hebrew-summary-סיכום-בעברית)

---

## Project Motivation
> *“Women and children first”* is the best‑known anecdote from the Titanic tragedy,  
> but does the data back it up?  
>
> This project answers that question and builds a predictive model that estimates a
> passenger’s chance of survival based on their attributes.

Goals:
* Validate historical claims using data (gender & age gaps).
* Build interpretable and high‑performance classifiers.

---

## Dataset
* **Source:** [Kaggle – Titanic: Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic)
* **Rows:** 891 passengers  |  **Target:** `Survived`
* **Key Features:** Age, Sex, Passenger Class, Fare, Embarkation Port, Family relations.

---

## Exploratory Data Analysis
* Survival rates segmented by **sex**, **age groups**, **passenger class**, **family size** and **embarkation port**.
* Correlation heatmap reveals strong negative correlation between `class` (1 = First) and survival.
* Custom dashboard quantifies the **55 % gender gap** and **21 % child–adult gap** in survival rates.

<p align="center">
  <img src="assets/dashboard.png" width="600">
</p>

---

## Feature Engineering
| Feature | Description | Reason |
|---------|-------------|--------|
| `FamilySize` | `SibSp + Parch + 1` | Captures social support on board. |
| `AgeGroup`  | Floor division by 5 → 0–5, 5–10… | Smoother age signal. |
| One‑Hot Encoding | `Sex`, `Embarked` | Converts categories to numeric. |

---

## Modeling
| Step | Details |
|------|---------|
| **Split** | Stratified 70 / 30 train‑test. |
| **Baseline** | Logistic Regression (`max_iter=1000`). |
| **Advanced** | Random Forest (`n_estimators`, `max_depth`, etc.). |
| **Hyper‑Parameter Tuning** | `GridSearchCV` (5‑fold). |
| **Metrics** | Accuracy, Precision, Recall, F1, ROC‑AUC, Average Precision. |
| **Visuals** | Confusion matrices, ROC & PR curves (see `figures/`). |

---

## Results
| Model | Accuracy | ROC‑AUC | F1 | AP (PR) |
|-------|----------|---------|----|---------|
| Logistic Regression | 0.80 | 0.85 | 0.79 | 0.83 |
| Logistic Regression (Tuned) | 0.81 | 0.84 | 0.80 | 0.84 |
| Random Forest | 0.82 | 0.86 | 0.80 | 0.84 |
| **Random Forest (Tuned)** | **0.84** | **0.87** | **0.82** | **0.86** |

**Take‑away:** The tuned Random Forest offers the best trade‑off between recall and precision, with an ROC‑AUC of 0.87.

---

## Dashboard
An explanatory dashboard (Tableau) highlights:

* **Gender Gap:** 74 % women vs 19 % men survived.  
* **Age Gap:** 58 % children vs 37 % adults survived.  
* Interactive panels can be ported to Streamlit for live demos.

---
