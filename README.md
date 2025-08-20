# eReader Adoption Prediction

## 📌 Project Overview
This project explores customer adoption behavior for a new eReader using historical purchasing and browsing data.  

The original dataset was provided in two parts:
- **Training set** – contained both features (e.g., age, gender, website activity) and the target (`Tablet_Adoption`).
- **Scoring set** – contained only features, mimicking a **real-world scenario** where businesses want to predict adoption for future customers without yet knowing the outcomes.

In practice, while the scoring set can be used to generate predictions, it does not allow us to calculate accuracy (since true labels are unknown). To properly evaluate model performance, we performed a **train/test split** on the training data.

---

## 🛠 Methods
1. **Data Preprocessing**
   - Converted categorical variables to categorical/factor type.
   - One-hot encoded categorical predictors for modeling.
   - Target variable (`Tablet_Adoption`) converted to categorical codes.

2. **Modeling**
   - Decision Tree Classifier (`max_depth=5`) used for interpretability.
   - Training dataset split into 70% training / 30% testing (stratified).
   - Evaluated using accuracy, confusion matrix, and classification report.

3. **Evaluation**
   - Compared training vs testing accuracy.
   - Analyzed class-level performance.

---

## 📊 Results
- **Training Accuracy:** ~68%  
- **Test Accuracy:** ~56%  

This gap indicates mild overfitting, common in decision trees. The model performed best at predicting **Late Majority** adopters, while struggling most with distinguishing **Early Adopters** vs **Early Majority**.

### Confusion Matrix (with Class Labels)
|                        | Predicted: Early Adopter | Predicted: Early Majority | Predicted: Innovator | Predicted: Late Majority |
|------------------------|--------------------------|---------------------------|-----------------------|--------------------------|
| **Actual: Early Adopter**  | 132 | 46 | 16 | 11 |
| **Actual: Early Majority** | 40  | 117 | 9  | 20 |
| **Actual: Innovator**      | 40  | 1   | 52 | 5  |
| **Actual: Late Majority**  | 11  | 18  | 4  | 139 |

### Key Insights
- **Late Majority** predictions were strongest (recall ~71%).  
- **Early Adopters** often misclassified as **Early Majority**, reflecting overlap between these groups.  
- **Innovators** are underrepresented, making them more difficult to predict accurately.  

---

## 💡 Recommendations
- In a real-world marketing setting:
  - Focus campaigns on **Late Majority** customers where predictions are most reliable.
  - Treat **Early Adopters** and **Early Majority** as a blended target segment until more discriminative features are available.
  - Collect additional behavioral data (e.g., purchase recency, engagement metrics) to improve recall for Innovators and Early Adopters.
- For stronger performance, consider **ensemble methods** such as Random Forests or Gradient Boosting.

---

## 📂 Repository Contents
- `notebook.ipynb` → Jupyter Notebook with full workflow (exploration, preprocessing, modeling, evaluation, recommendations).  
- `README.md` → Project summary and results.  
- `Scoring_with_Predictions.csv` → Predictions generated for scoring dataset.

---

## 🚀 Next Steps
This project provided a foundation for supervised classification using decision trees.  
Future improvements could include:
- Testing ensemble models (Random Forest, XGBoost) for higher accuracy.
- Adding feature engineering to better capture user behavior.
- Applying cross-validation for more robust evaluation.
