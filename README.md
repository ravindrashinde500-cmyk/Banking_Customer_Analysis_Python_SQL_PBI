#🧾 Banking Customer Analysis – Accounts and Portfolio Management

_Analyzing customer credit profiles and transaction patterns to support data-driven loan approval and risk assessment decisions using SQL, Python, and Power BI._

---

## 📌Table of Contents
- <a href="#overview">Overview</a>
- <a href="#business-problem">Business Problem</a>
- <a href="#dataset">Dataset</a>
- <a href="#tools--technologies">Tools & Technologies</a>
- <a href="#project-structure">Project Structure</a>
- <a href="#data-cleaning--preparation">Data Cleaning & Preparation</a>
- <a href="#exploratory-data-analysis-(eda)">Exploratory Data Analysis (EDA)</a>
- <a href="#dashboard">Dashboard</a>
- <a href="#how-to-run-this-project">How to Run This Project</a>
- <a href="#key-insights">Key Insights</a>
- <a href="#conclusion">Conclusion</a>
- <a href="#future-work">Future Work</a>
- <a href="#author--contact">Author & Contact</a>

---

<h2><a class="anchor" id="overview"></a>Overview</h2>

- Analysed banking customer segmentation, account types, investments, and risk profiles to support money-lending decisions.
- Built an end-to-end data pipeline using SQL (ETL), Python (analysis and hypothesis testing), and Power BI (visualisation).

---

<h2><a class="anchor" id="business-problem"></a>Business Problem</h2>

- Develop a basic understanding of risk analytics in banking and financial services, and understand how data is used to minimise the risk of         losing money while lending to customers.

- With the help of our dashboards, which are created using Power BI's latest tool, the company makes decisions based on the applicant's profile, such as whether the applicant is likely to repay the loan, approve the loan, or not.

- **Customer Risk Profiling** :
   - Analyse customer demographics, income levels, account behaviour, and credit history to classify customers into low, medium, and high-risk          categories before lending decisions.

- **Loan Eligibility Assessment** :
   - Use historical customer and transaction data to evaluate repayment capacity and determine loan eligibility, reducing the probability of default.

- **Portfolio Risk Monitoring** :
   - Track loan portfolio performance across customer segments and account types to identify risk concentration and proactively manage potential        losses.

- **Data-Driven Credit Decisions**:
   - Leverage data analytics and statistical techniques to support objective lending decisions, minimising human bias and improving approval            accuracy.

- **Early Warning & Risk Mitigation**:
   - Identify early risk indicators such as delayed payments, declining balances, or high leverage to enable timely corrective actions and reduce       non-performing assets (NPAs).

---

<h2><a class="anchor" id="dataset"></a>Dataset</h2>
- <a href= "https://github.com/ravindrashinde500 cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Banking.xlsx">Dataset</a>

- Multiple CSV files are located in /data/ folder.

- **The database consists of tables** : Banking Relationship, Client-Banking, Gender, Investment Advisor, and Period.

- This dataset primarily contains information about bank details and various client details, which are organised into multiple tables that are       interlinked through keys, including primary keys and foreign keys. 

- Summary table created from ingested data and used for analysis.

---

<h2><a class="anchor" id="tools--technologies"></a>Tools & Technologies</h2>
  
  - SQL (Common Table Expressions, Joins, Filtering)
  - Python (Pandas, Matplotlib, Seaborn)
  - Power BI (Interactive Visualisations)
  - GitHub

---   

<h2><a class="anchor" id="project-structure"></a>Project Structure</h2>

```
banking-customer-analysis/
│
├── README.md
├── .gitignore
├── requirements.txt
├── banking customer Report.pdf
│
├── notebooks/                  # Jupyter notebooks
│   ├── exploratory_data_analysis.ipynb
│   ├── banking_analysis.ipynb
│
├── scripts/                    # Python scripts for ingestion and processing
│   ├── banking_script.py
│   
│
├── dashboard/                  # Power BI dashboard file
│   └── banking_pbi_dashboard.pbix
```

---

<h2><a class="anchor" id="data-cleaning--preparation"></a>Data Cleaning & Preparation</h2>

- Created a new column, Engagement Timeframe, in the client-banking column, which tells about the timeline of the clients in banks.
```
    - Engagement Timeframe =
    - SWITCH (TRUE (),
    - ‘Clients – Banking’ [Engagement Days] < 365  “< 1 Year”,
    - ‘Clients – Banking’ [Engagement Days] < 1825 “< 5 Year”,
    - ‘Clients – Banking’ [Engagement Days] < 3650 “< 10 Year”,
    - ‘Clients – Banking’ [Engagement Days] < 7300 “< 10 Year”,
    - “>20 Years”)
```
- Created a new column, Engagement Days, in the Client-Banking table, showing how many days the client spent with the bank from the date of          joining the bank.
```
    - Engagement Days =
    - DATEDIFF (‘Clients – Banking [Joined Bank], TODAY (), DAY)
```
- Created bins for the Estimated Income < 100000 as low and < 300000 as Mid with the column named as Income Band in the Clients-Banking table.
```
    - Income Band =
    - SWITCH (TRUE (),
    - ‘Clients – Banking [Estimated Income], < 100000, “Low”,
    - ‘Clients – Banking [Estimated Income], < 300000, “Mid”,
    -  “High”)
 ```

---

<h2><a class="anchor" id="exploratory-data-analysis-(eda)"></a>Exploratory Data Analysis (EDA)</h2>

- Customer demographics and income levels significantly influence loan uptake and default risk, with higher loan-to-income ratios showing  increased risk.

- Savings account holders form the majority of customers, while those with multiple account types demonstrate lower credit risk.

- Customers with diversified investments exhibit better repayment behaviour and lower default probabilities.

- High-risk customer segments contribute disproportionately to potential losses, emphasising the need for risk-based lending strategies.

- Strong correlations were identified between credit scores, repayment behaviour, and default probability, supporting data-driven credit decisions.

---

<h2><a class="anchor" id="dashboard"></a>Dashboard</h2>

- The dashboard was built using the following tools and technologies:-

  - **Power BI Desktop** : Main data visualisation platform used for report creation.
  
  - **Power query** : Data transformation and cleaning layer, reshaping and preparing the data.
 
  - **Dax(Data Analysis Expressions)** : Used for calculated measures, dynamic visuals, and conditional logic.
  
  - **Data Modelling** : Relationship established among tables(resorts, snow, and data_dictionary) to enable                         cross-filtering and aggregation.
  
  - **File Format** :.pbix for development and .png for dashboard previews.

   - <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/banking_pbi_dashboard.pbix">Banking Customer_PBI_Dashboard</a>

   - <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Home.png">Home</a>

   - <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Loan_Analysis.png">Loan_Analysis</a>

   - <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Deposit_Analysis.png">Deposit_Analysis</a>

   - <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Summary.png">Summary</a>
   
---

<h2><a class="anchor" id="how-to-run-this-project"></a>"How to Run This Project</h2>

1. **Clone the repository** :
```bash
- `git clone https://github.com/yourusername/banking-customer-analysis.git`
```

2. **Load the CSVs and ingest into the database** :
```bash
- `python scripts/ingestion_db.py`
```

3. **Create banking summary table** :
```bash
- `python scripts/get_banking_summary.py`
```

4. **Open and run notebooks** :
```
 - `notebooks/exploratory_data_analysis.ipynb`
 - `notebooks/banking_customer_analysis.ipynb`
```

5. **Open Power BI Dashboard** :
```
   - `dashboard/banking_customer_dashboard.pbix`
```

- **Open Power BI Dashboard**: <a href= "https://github.com/ravindrashinde500-cmyk/Banking_Customer_Analysis_Python_SQL_PBI/blob/main/Banking_PBI_Dashboard.pbix">Banking_Customer_Dashboard</a>

---

<h2><a class="anchor" id="key-insights"></a>Key Insights</h2> 

- With these dashboards, banks can easily know the total loan amount and all other things about a particular investor.

- It also helps determine which type of banks have a greater number of clients, as we can see that private banks have a greater number of clients,   so it can help other banks build their strategies to increase clients. 

- It also provides insights into which nationality has the highest bank loans. 

- It provides information about various types of amounts involved in different types of accounts held by investors.

---

<h2><a class="anchor" id="conclusion"></a>Conclusion</h2>

- Empowered by the latest data visualisation techniques, Power BI dashboards are among the most effective resources for use in the banking sector. 

- As outlined in this write-up, a banking operations dashboard in Power BI can be developed to key banking-related metrics and KPIs.

---

<h2><a class="anchor" id="future-work"></a>Future Work</h2>

- Incorporate real-time transaction data to enable dynamic risk scoring and early warning systems.

- Enhance risk assessment by integrating external credit bureau data and alternative data sources.

- Develop risk-based pricing models to align interest rates with customer risk profiles.

---

<h2><a class="anchor" id="author--contact"></a>Author & Contact</h2>

- Ravindra Shinde
- Data Analyst
- 📧 Email: ravindra.shinde500@gmail.com
- 🔗[linkedin](https://www.linkedin.com/in/ravindrashinde0815/)
