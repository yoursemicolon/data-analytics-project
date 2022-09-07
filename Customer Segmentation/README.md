# Machine Learning Project Report - Amanda Rozi Kurnia
## Project Domain: Customer Segmentation using RFM Analysis and K-Means Clustering
### Background
All businesses or business entities, be they small, medium or large businesses, must have customers or customers. The customer has a specific character, for example an adult woman (over 17 years old). But actually these characteristics can be further divided in more detail based on professions, for example housewives and career women. And it is still further divided in more detail based on total spending for a year, province of residence, and others.

The more we recognize the characteristics of our customers, the easier it will be for us to innovate products with these character needs and conduct marketing communications. This process of dividing customer characteristics is called customer segmentation. If this process is carried out on the customer data that we have manually, it will be difficult and time consuming, especially with large amounts and variations of data.

Dividing a customer base into particular groups with similar characteristics such as demogprahics or behaviours can help the company to market to those customers more effectively. These customer segmentation groups can also be used to begin discussion of building a marketing persona.

Luckily, there are currently many automation processes for customer segmentation using various machine learning algorithms. Two of them are k-means and k-modes. This project will focus on understanding K-Means algorithm and RFM analysis with a practical approach using the Python programming language.

### Reason
Here are some main reasons why does company need customer segmentation:
* Targeted marketing messages to the right people – Without customer segmentation, marketing can be like throwing out a wide net and seeing what comes back.
* Focuses on the most profitable customers. This is because we’re targeting potential customers who are interested in our product, or customers who typically repurchase. 
* It can improve customer service. We will gain a better understanding of our customers. With this in mind, we can personalise our marketing approach.

### Existing Result
A lot of studies about customer segmentation using machine learning have been done. In one research from [(N. Patankar et al, 2021)](https://www.researchgate.net/publication/356756320_Customer_Segmentation_Using_Machine_Learning), authors segmented company's customers data with the help of K-means clustering machine learning algorithm. This study also proves that the dividing customers on the basis of behavioral characteristics is a better solution for existing customer segmentation problem and K-means clustering algorithm is identified as a good choice for this approach.

References:
* [Customer Segmentation Using Machine Learning](https://www.researchgate.net/publication/356756320_Customer_Segmentation_Using_Machine_Learning)
* [Customer Segmentation using RFM Model and K-Means Clustering](https://www.sciencegate.app/document/10.3233/apc210200)

## Business Understanding
A primary goal for any company and business is to understand their targeted customers. How their customers operate and use their products or services since each customer may use a company products or services differently. The problem we're trying to solve is to define these type of customers.

### Problem Statements
Based on the condition above, company will develop a customer segmentation system to answer these following problems: 
- How recently customer buy the products?
- How often customer buy the products?
- How much did a customer buy the products?

### Goals
- Filter customers into various groups to help company identifies potential customers to do a more profitable business

### Solution statements
- Combining RFM Analysis with K-Means clustering algorithm. To understand the behavior of the customer, RFM metrics plays a vital role as frequency and monetary value affect a customer's lifetime value and recency affects retention, a measure of engagement. On the other side, K-Means helps to answer vital question like who are the best customers, who contribute to churn rate etc. Thus, we will do an in-depth analysis using those two method.
- Using clustering performance evaluation metrics to evaluate the K-Means model

## Data Understanding
We will use actual transactions from UK retailer that can be downloaded from [Kaggle dataset](https://www.kaggle.com/datasets/carrie1/ecommerce-data?datasetId=1985). Typically e-commerce datasets are proprietary and consequently hard to find among publicly available data. However, The UCI Machine Learning Repository has made this dataset containing actual transactions from 2010 and 2011. The dataset is maintained on their site, where it can be found by the title "Online Retail". This is a transactional data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail.The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

### The variables in the E-commerce dataset are as follows:
- InvoiceNo: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation.
- StockCode: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
- Description: Product (item) name. Nominal.
- Quantity: The quantities of each product (item) per transaction. Numeric.
- InvoiceDate: Invoice Date and time. Numeric, the day and time when each transaction was generated.
- UnitPrice: Unit price. Numeric, Product price per unit in sterling.
- CustomerID: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
- Country: Country name. Nominal, the name of the country where each customer resides.

### Explanatory Data Analysis (EDA)
To know a little more about the data before starting to implement RFM analysis and machine learning algorithms, we created a few EDA plots. We will explore about: 
* Total number of columns and rows
* Missing values
* Duplicate values
* Negative values
* Data consistency
* Basic statistics for quantitive variables 

**Columns and Rows**
This dataset consists of:
- 8 columns (features/variables)
- 541.909 rows (records)

[insert image here eda-1]

**Missing Values**
Only 2 columns have missing values: CustomerID (135.080 or 24.93%) and Description (1.454 or 0.27%). It is interesting to note that ∼ 25% of the entries are not assigned to a particular customer. With the data available, it is impossible to impute values for the user and these entries are thus useless for the current exercise. So, we exclude them from the dataframe.
[insert image here eda-2]

**Duplicate Values**
There are 5.225 (1%) duplicate rows dan we remove them from the dataframe.
[insert image here eda-3]

**Negative Values**
Quantity column has 8.872 negative values. Some of these are associated with cancelled orders. Thus, we remove them before further analysis.
[insert image here eda-4]

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
