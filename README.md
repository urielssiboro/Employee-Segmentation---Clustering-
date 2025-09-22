# Employee Segmentation with K-Means Clustering

## Business Problem
The company has over 3,000 employees across different departments, age groups, and performance levels.  
Currently, HR evaluates employees individually, without identifying broader patterns in the workforce.  
This creates several challenges:
- **Retention Risk**: High-performing employees may leave if not recognized properly.  
- **Performance Gaps**: Some groups underperform but still consume resources.  
- **Compensation Misalignment**: Bonuses and salaries may not reflect actual contribution.  
- **Overtime Imbalance**: Some employees work excessive overtime, risking burnout.  

**Goal**: Segment employees into **4 distinct groups (clusters)** to help HR design targeted policies for retention, performance improvement, and compensation alignment.

---

##  Approach

### 1. Data Preparation
- **Handled missing values**:
  - Filled `bonus_percentage` and `overtime_hours` with `0`.
  - Dropped rows with nulls in `age`, `years_experience`, and `weekly_hours`.
  - Replaced missing `department` with special values.
- **Handled outliers**:
  - Removed unrealistic ages (`<18` or `>70`).
  - Removed extreme weekly hours (`>80`).
  - Kept natural business outliers (e.g., very high income or overtime).

### 2. Feature Engineering
- **Encoding**:
  - One-hot encoding for categorical variables.
  - Ordinal encoding for ordered categories (education, contract type, etc.).
- **Scaling**:
  - Used **RobustScaler** (resistant to outliers).
- **Dimensionality Reduction**:
  - Applied **PCA** with 15 components, retaining ~96% of variance.

### 3. Clustering
- Used **KMeans** algorithm.
- Determined optimal `k=4` using:
  - **Elbow Method**.
  - **Silhouette Score**.
- Assigned each employee to one of four clusters.

### 4. Cluster Profiling
- Created summaries for each cluster using:
  - **Numeric features** (age, experience, income, overtime, performance).
  - **Categorical features** (gender, marital status, city, education, department, income class).
- Visualized clusters using:
  - PCA scatter plot.
  - Cluster size bar chart.
  - Boxplots for key features (income, performance, overtime).

---

## Key Findings

- **Cluster 0**: Senior high earners with high overtime but moderate performance.  
- **Cluster 1**: Young high performers with strong performance but lower income.  
- **Cluster 2**: Steady mid-level employees with stable performance but low bonuses.  
- **Cluster 3**: Low-income, weaker performers with lighter overtime.  

---

## Business Recommendations
- **Cluster 0**: Reduce overtime and provide skill refresh programs.  
- **Cluster 1**: Offer career development and performance-based incentives to retain them.  
- **Cluster 2**: Adjust bonus policy to reward steady performance and provide upskilling.  
- **Cluster 3**: Provide targeted training and mentoring; consider role rotation.  

---

## How to Run

### Prerequisites
Install dependencies:
```bash
pip install pandas numpy scikit-learn seaborn matplotlib
