# 🛒 Market Basket Analysis with Apriori Algorithm

This project performs **Market Basket Analysis** using the **Apriori algorithm** to discover frequent itemsets and generate association rules. It helps understand purchasing patterns — for example, "Customers who bought milk also bought bread."

---

## 📌 Project Objective

To identify frequent item combinations and generate association rules from transactional purchase data using:
- `Apriori` algorithm from `mlxtend`
- Metrics like `support`, `confidence`, and `lift`

---

## 🧾 Dataset

The input dataset is expected in a **long format**, like:

| single_transaction | itemDescription |
|--------------------|-----------------|
| 1                  | Milk            |
| 1                  | Bread           |
| 2                  | Butter          |
| 2                  | Bread           |

This is converted into a binary one-hot encoded matrix using `pd.crosstab()`.

---

## ⚙️ Methodology

1. **Data Preprocessing**
   - Clean missing or irrelevant values
   - Create a basket matrix using `pd.crosstab()`
   - Convert quantities to binary (0/1) using a custom encoding function

2. **Frequent Itemset Mining**
   - Use `mlxtend.frequent_patterns.apriori` with a chosen `min_support`
   - Generate frequent itemsets

3. **Association Rule Mining**
   - Use `mlxtend.frequent_patterns.association_rules`
   - Filter rules using metrics like `lift`, `confidence`, and `support`

---

## 🧪 Example Code

```python
from mlxtend.frequent_patterns import apriori, association_rules

# Find frequent itemsets
frequent_itemsets = apriori(basket_input, min_support=0.01, use_colnames=True)

# Generate rules
rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1)

# Display rules
rules.head()

