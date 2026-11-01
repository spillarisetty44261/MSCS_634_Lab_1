# MSCS 634 – Lab 1: Data Visualization, Preprocessing, and Statistical Analysis



## Purpose

The purpose of this lab is to explore a dataset using visualizations, clean and prepare it with preprocessing techniques, and describe it using statistical measures in a Jupyter Notebook.

## Dataset

I used the BigMart Sales dataset from Kaggle. It contains 2013 sales data for products sold in 10 BigMart stores, with 8,523 rows and 12 columns. The main variable analyzed is Item_Outlet_Sales.

## Files

- `MSCS_634_Lab_1.ipynb` – Jupyter Notebook with all code, outputs, and explanations
- `data/bigmart_sales.csv` – original dataset
- `data/bigmart_sales_cleaned.csv` – dataset after handling missing values
- `data/bigmart_sales_preprocessed.csv` – dataset after outlier removal, data reduction, scaling, and discretization
- `screenshots/` – screenshots of the required outputs

## Key Insights

**Visualizations**
- Sales are right-skewed: most items sell under 3,000, but some sell up to about 13,000.
- There is a positive relationship between price (MRP) and sales.
- Supermarket Type 3 has the highest average sales (about 3,694) and Grocery Stores have the lowest (about 340).
- The line plot shows a big drop in 1998 because the only outlet opened that year is a Grocery Store.
- Tier 3 locations make the largest share of total sales (41.1%).

**Statistical Analysis**
- The mean of sales (2,181.29) is higher than the median (1,794.33), which confirms the right skew.
- Sales have a large spread, with a standard deviation of 1,706.50 and an IQR of 2,267.05.
- `Item_MRP` has the strongest correlation with sales (0.57). The other numeric columns have weak or almost no correlation with sales.

## Challenges and Decisions

- Missing values: `Item_Weight` (1,463 missing) and `Outlet_Size` (2,410 missing) had missing data. Dropping rows would have removed almost half of the dataset, so I filled `Item_Weight` with the mean and `Outlet_Size` with the mode.
- Inconsistent labels: `Item_Fat_Content` had different names for the same category ("LF", "low fat", "reg"), so I combined them into "Low Fat" and "Regular".
- Outliers: The IQR method found 186 outliers in sales. I removed them, which reduced the dataset to 8,337 rows. These may be real high-selling items, so for the statistical analysis I used the cleaned dataset with all rows.
- Data reduction: I dropped `Item_Identifier` and `Outlet_Identifier` because they are only ID codes.
- Zero visibility: Some items have an `Item_Visibility` of 0, which does not make sense for a product that is sold. I noted this as a possible data quality issue.
