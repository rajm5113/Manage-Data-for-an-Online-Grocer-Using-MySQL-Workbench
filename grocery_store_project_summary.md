
# Grocery Store Inventory and Sales Analysis Project

---

## **Project Overview**
**Tools Used**: MySQL Workbench, Excel/CSV, SQL  
**Goal**: To build a relational database from raw grocery data and use SQL to generate insights that support sales and inventory decisions.

---

## **Task 1: Design a Relational Database**
- Reviewed the original dataset (`GreenspotDataset.csv`)
- Identified 5 core entities:
  - `products`
  - `vendors`
  - `customers`
  - `sales`
  - `inventory`
- Created an EER diagram in MySQL Workbench
- Set primary keys and foreign key relationships
- Normalized the structure to 3NF to eliminate redundancy

---

## **Task 2: Build Database Tables**
- Used MySQL Workbench's Forward Engineer feature to generate SQL `CREATE TABLE` statements
- Created tables with defined primary keys, data types, and constraints
- Confirmed table creation in the live database environment (`mydb` schema)

---

## **Task 3: Load Sample Data**
- Cleaned and separated the original CSV into:
  - `products.csv`
  - `vendors.csv`
  - `customers.csv`
  - `sales.csv`
  - `inventory.csv`
- Used the Table Data Import Wizard to import each file into its corresponding table
- Verified the data using `SELECT *` queries in MySQL Workbench

---

## **Task 4: Write SQL Queries**
Wrote and executed SQL queries to explore and analyze the database:

1. **View all products**  
```sql
SELECT * FROM products;
```

2. **Sales made on a specific date**  
```sql
SELECT * FROM sales WHERE sale_date = '2022-05-12';
```

3. **Total quantity sold per product**  
```sql
SELECT product_id, SUM(quantity) FROM sales GROUP BY product_id;
```

4. **Join sales with products to get product names**  
```sql
SELECT p.description, SUM(s.quantity) 
FROM sales s 
JOIN products p ON s.product_id = p.product_id 
GROUP BY p.description;
```

5. **Join inventory with vendors to show supplier info**  
```sql
SELECT v.name, i.product_id, i.quantity_on_hand, i.purchase_date 
FROM inventory i 
JOIN vendors v ON i.vendor_id = v.vendor_id 
ORDER BY v.name;
```

---

## **Conclusion / Highlights**
- Built a fully normalized relational database from scratch
- Cleaned and loaded real-world data into MySQL
- Wrote and executed SQL queries to extract business insights
- Demonstrated proficiency in SQL fundamentals: `SELECT`, `JOIN`, `GROUP BY`, filtering, and importing CSV data
- Final database is well-structured, query-ready, and practical for real business use
