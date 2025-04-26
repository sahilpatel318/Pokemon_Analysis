# Pokémon Analysis

What is Pokémon? [Pokémon Introduction by Official Pokémon Channel](https://www.pokemon.com)

* Analysis of Pokémon dataset to explore stats, types, and trends across generations.
* Used Python and Jupyter Notebook for data cleaning, exploratory analysis, and visualization.
* Visualized various insights using bar charts, line graphs, and heatmaps.
* Created advanced metrics such as Pokémon efficiency ratios and battle strengths.

---

## Why Analyze Pokémon Data?

* Pokémon data contains a wealth of information, from basic stats like `HP` and `Attack` to types and Legendary status.
* By analyzing this data, we can uncover interesting insights about Pokémon design and their performance characteristics.
* This project serves as a fun and educational demonstration of data analysis techniques.

---

# Data Cleaning

Before diving into the analysis, the dataset was cleaned to ensure accurate and consistent results:

### **Steps in Data Cleaning**
1. **Handling Missing Values**:
   - The column `Type 2` had missing values for Pokémon with only one type. These were filled with `"None"`.
   - Example:
     ```python
     df['Type 2'] = df['Type 2'].fillna('None')
     ```

2. **Standardizing Column Names**:
   - Renamed columns to make them consistent and easy to use (e.g., `Sp. Atk` → `Sp_Atk`).
     ```python
     df.columns = df.columns.str.replace(' ', '_')
     ```

3. **Removing Duplicates**:
   - Verified the dataset for duplicate entries to ensure no Pokémon were listed twice.

4. **Type Conversion**:
   - Ensured numeric columns (`HP`, `Attack`, etc.) were of the correct data type for statistical calculations.

5. **Adding Derived Columns**:
   - Created new columns like `"Rarity"` to classify Pokémon as `Legendary` or `Common`:
     ```python
     df['Rarity'] = df['Legendary'].apply(lambda x: 'Legendary' if x else 'Common')
     ```

---

# Analysis

### **Total Pokémon by Type**
```python
type_counts = df['Type 1'].value_counts()
type_counts.plot.bar()

average_stats = df.groupby('Type 1').mean()
sns.heatmap(average_stats, annot=True, cmap='coolwarm')
