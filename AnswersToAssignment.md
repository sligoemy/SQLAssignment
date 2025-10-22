
# SET UP
## Creating the tables 
	CREATE TABLE customers (
	customer_id INT IDENTITY(1,1) PRIMARY KEY,
	full_name VARCHAR(50) NOT NULL,
	email VARCHAR(50) UNIQUE,
	join_date DATE NOT NULL
	);

	CREATE TABLE products (
	product_id INT IDENTITY(1,1) PRIMARY KEY,
	product_name VARCHAR(50) NOT NULL,
	category VARCHAR(50) NOT NULL,
	price INTEGER NOT NULL
	);


	CREATE TABLE orders (
	order_id INT IDENTITY(1,1) PRIMARY KEY,
	customer_id INTEGER NOT NULL REFERENCES customers(customer_id),
	order_date DATE NOT NULL,
	total_amount INTEGER NOT NULL
	);


	CREATE TABLE order_items (
	order_item_id INT IDENTITY(1,1) PRIMARY KEY,
	order_id INTEGER NOT NULL REFERENCES orders(order_id),
	product_id INTEGER NOT NULL REFERENCES products(product_id),
	quantity INTEGER NOT NULL,
	line_total INTEGER NOT NULL
	);


	CREATE TABLE loyalty_points (
	customer_id INTEGER NOT NULL REFERENCES customers(customer_id),
	points_earned INTEGER NOT NULL,
	transaction_date DATE NOT NULL,
	source VARCHAR(50) NOT NULL
	);
	
This creates five tables namely customers, products, orders, order_items, loyalty_points tables.


## Inserting Data Into Tables
	-- -----------------------------
	-- Table: customers
	-- -----------------------------
	INSERT INTO customers 
	(full_name, email, join_date)
	VALUES
	('Alice Johnson', 'alice.johnson@example.com', '2023-01-15'),
	('Brian Smith', 'brian.smith@example.com', '2023-02-20'),
	('Chinwe Okafor', 'chinwe.okafor@example.com', '2023-03-05'),
	('David Lee', 'david.lee@example.com', '2023-03-18'),
	('Emeka Nwosu', 'emeka.nwosu@example.com', '2023-04-12'),
	('Fatima Bello', 'fatima.bello@example.com', '2023-05-25'),
	('George Adewale', 'george.adewale@example.com', '2023-06-07'),
	('Hannah Kim', 'hannah.kim@example.com', '2023-07-14'),
	('Ibrahim Musa', 'ibrahim.musa@example.com', '2023-08-22'),
	('Jessica White', 'jessica.white@example.com', '2023-09-30'),
	('Kemi Adebayo', 'kemi.adebayo@example.com', '2023-10-10'),
	('Leo Fernandez', 'leo.fernandez@example.com', '2023-11-05'),
	('Mariam Yusuf', 'mariam.yusuf@example.com', '2023-11-20'),
	('Nathan Okeke', 'nathan.okeke@example.com', '2023-12-01'),
	('Olivia Brown', 'olivia.brown@example.com', '2023-12-15');

	-- -----------------------------
	-- Table: products
	-- -----------------------------
	INSERT INTO products 
	(product_name, category, price) 
	VALUES
	('Wireless Mouse', 'Electronics', 4500),
	('Bluetooth Speaker', 'Electronics', 12000),
	('Smart Lamp', 'Home', 8000),
	('Cookware Set', 'Home', 15000),
	('Formal Shirt', 'Fashion', 7000),
	('Sneakers', 'Fashion', 12000),
	('Green Tea', 'Groceries', 1500),
	('Phone Case', 'Electronics', 2500),
	('Backpack', 'Fashion', 9000),
	('LED TV 32\"', 'Electronics', 55000),
	('Hair Dryer', 'Beauty', 6000),
	('Coffee Maker', 'Home', 20000),
	('Sunglasses', 'Fashion', 8000),
	('Rice Cooker', 'Home', 12000),
	('T-shirt', 'Fashion', 4000),
	('Water Bottle', 'Home', 2000),
	('Gaming Keyboard', 'Electronics', 15000),
	('Running Shorts', 'Fashion', 5000),
	('External HDD', 'Electronics', 20000),
	('Powerbank', 'Electronics', 8000);

	-- -----------------------------
	-- Table: orders
	-- -----------------------------
	INSERT INTO orders 
	(customer_id, order_date, total_amount) 
	VALUES
	(1, '2023-01-20', 16500),
	(2, '2023-02-25', 26500),
	(3, '2023-03-10', 10500),
	(4, '2023-03-22', 23000),
	(5, '2023-04-15', 7000),
	(6, '2023-05-30', 18000),
	(7, '2023-06-10', 1500),
	(8, '2023-07-20', 59000),
	(9, '2023-08-25', 12000),
	(10, '2023-09-05', 55000),
	(11, '2023-10-12', 6000),
	(12, '2023-11-10', 22000),
	(13, '2023-11-25', 16000),
	(14, '2023-12-05', 5000),
	(15, '2023-12-18', 35000);

	-- -----------------------------
	-- Table: order_items
	-- -----------------------------
	INSERT INTO order_items 
	(order_id, product_id, quantity, line_total) 
	VALUES
	(1, 1, 2, 9000),
	(1, 7, 5, 7500),
	(2, 2, 2, 24000),
	(2, 8, 1, 2500),
	(3, 5, 1, 7000),
	(3, 7, 1, 1500),
	(3, 16, 1, 2000),
	(4, 4, 1, 15000),
	(4, 3, 1, 8000),
	(5, 5, 1, 7000),
	(6, 6, 1, 12000),
	(6, 11, 1, 6000),
	(7, 7, 1, 1500),
	(8, 10, 1, 55000),
	(8, 15, 1, 4000),
	(9, 9, 1, 9000),
	(9, 7, 2, 3000),
	(10, 10, 1, 55000),
	(11, 11, 1, 6000),
	(12, 12, 1, 20000),
	(12, 16, 1, 2000),
	(13, 14, 1, 12000),
	(13, 15, 1, 4000),
	(14, 18, 1, 5000),
	(15, 17, 1, 15000),
	(15, 19, 1, 20000);

	-- -----------------------------
	-- Table: loyalty_points
	-- -----------------------------
	INSERT INTO loyalty_points 
	(customer_id, points_earned, transaction_date, source) 
	VALUES
	(1, 150, '2023-01-21', 'Order'),
	(1, 50, '2023-02-05', 'Promotion'),
	(2, 300, '2023-02-26', 'Order'),
	(3, 100, '2023-03-11', 'Order'),
	(3, 20, '2023-03-12', 'Referral'),
	(4, 200, '2023-03-23', 'Order'),
	(5, 50, '2023-04-16', 'Order'),
	(6, 180, '2023-05-31', 'Order'),
	(7, 10, '2023-06-11', 'Order'),
	(8, 190, '2023-07-21', 'Order'),
	(9, 120, '2023-08-26', 'Order'),
	(10, 500, '2023-09-06', 'Order'),
	(11, 70, '2023-10-13', 'Promotion'),
	(12, 220, '2023-11-11', 'Order'),
	(13, 90, '2023-11-26', 'Order'),
	(14, 30, '2023-12-06', 'Order'),
	(15, 250, '2023-12-19', 'Order');

Please note that since primary keys as set as IDENTITY(1,1) i.e. automatically assign IDs to each rows,  all Ids as given were removed from all tables apart from loyal_points table.


# ANSWERS TO ASSIGNMENT

## Question 1
## Count the total number of customers who joined in 2023.

	SELECT 
	COUNT(customer_id) as 'Count of Customers'
	FROM customers
	WHERE YEAR(join_date)=2023

## Question 2
## For each customer return customer_id, full_name, total_revenue (sum of total_amount from orders). Sort descending.
	
	SELECT 
	c.customer_id,
	c.full_name,
	SUM(total_amount) AS total_revenue


	FROM customers c
		LEFT JOIN orders o 
		ON c.customer_id = o.customer_id

	GROUP BY c.customer_id, full_name 

	ORDER BY total_revenue DESC

## Question 3 
## Return the top 5 customers by total_revenue with their rank.

	with Total_Revenue as 
	(SELECT
	c.full_name, 
	SUM(o.Total_amount) as Total_Revenue,
	RANK() OVER(ORDER BY (SUM(o.total_amount)) DESC) as rEV_Rank


	FROM customers c
	INNER JOIN orders o 
	ON c.customer_id = o.customer_id 

	GROUP BY full_name
	) 
	SELECT 
	full_name, 
	Total_Revenue, 
	Rev_Rank

	FROM Total_Revenue

	WHERE rEV_Rank <= 5

## Question 4
## Produce a table with year, month, monthly_revenue for all months in 2023 ordered chronologically.

	SELECT
	YEAR(Order_date) AS Year, 
	MONTH(order_date) as Month,
	SUM(Total_Amount) as Monthly_Revenue

	FROM orders

	WHERE YEAR(Order_Date) = 2023
	GROUP BY YEAR(Order_Date), MONTH(order_date)

## Question 5
## Find customers with no orders in the last 60 days relative to 2023-12-31 (i.e., consider last active date up to 2023-12-31). Return customer_id, full_name, last_order_date.


	SELECT
	c.customer_id,
	c.full_name,
	MAX(order_date) as Last_order_date


	FROM orders o
	LEFT JOIN customers c
	ON o.customer_id = c.customer_id 

	GROUP BY c.customer_id, full_name

	HAVING (DATEDIFF(day, Max(order_date), '2023-12-31')) > 60

## Question 6
## Calculate average order value (AOV) for each customer: return customer_id, full_name, aov (average total_amount of their orders). Exclude customers with no orders.

	SELECT 
	c.customer_id,
	c.full_name,
	AVG(o.Total_Amount) as AOV

	FROM customers c 
	INNER JOIN orders o
	ON c.customer_id = o.customer_id

	GROUP BY c.customer_id, c.full_name

	HAVING SUM(Total_Amount) IS NOT NULL 

## Question 7 
## For all customers who have at least one order, compute customer_id, full_name, total_revenue, spend_rank where spend_rank is a dense rank, highest spender = rank 1

	WITH Total_Rev as 
	(SELECT 
	c.customer_id, 
	c.full_name,
	SUM(o.Total_Amount) as Total_Revenue

	FROM customers c
	LEFT JOIN orders o
	ON c.customer_id = o.customer_id 
	
	GROUP BY full_name, c.customer_id
	)
	SELECT 
	customer_id, 
	full_name,
	Total_Revenue,
	DENSE_RANK() OVER (order by total_revenue desc) as DenseRank

	FROM Total_Rev

	WHERE Total_revenue is not null

## Question 8
## List customers who placed more than 1 order and show customer_id, full_name, order_count, first_order_date, last_order_date

	SELECT
	c.customer_id,
	c.full_name,
	COUNT(o.order_id) as order_count,
	MIN(o.order_date) as first_order_date,
	MAX(o.order_date) as last_order_date

	FROM customers c
	INNER JOIN orders o
	ON c.customer_id = o.customer_id

	GROUP BY c.customer_id, c.full_name

	HAVING COUNT(o.order_id) > 1

## Question 9
## Compute total loyalty points per customer. Include customers with 0 points.

	SELECT
	c.customer_id, 
	c.full_name, 
	SUM(l.points_earned) AS loyalty_point

	FROM customers c 
	LEFT JOIN loyalty_points l 
	ON c.customer_id = l.customer_id

	GROUP BY c.customer_id, c.full_name

	ORDER BY loyalty_point DESC  

## Question 10
## Assign loyalty tiers based on total points: Bronze below 100; Silver: 100–499; Gold above  500  

	WITH tier_solutions AS (
    	SELECT 
        customer_id, 
        SUM(points_earned) AS Total_Points_Earned,
        CASE 
            WHEN SUM(points_earned) < 100 THEN 'Bronze'
            WHEN SUM(points_earned) BETWEEN 100 AND 499 THEN 'Silver'
            WHEN SUM(points_earned) >= 500 THEN 'Gold'
        END AS tier
    	
	FROM loyalty_points
    	GROUP BY customer_id
	)
	SELECT
    	tier,
    	COUNT(*) AS tier_count,
    	SUM(Total_Points_Earned) AS total_points_earned
	
	FROM tier_solutions
	
	GROUP BY tier
	
	ORDER BY total_points_earned DESC;


## Question 11 
## Identify customers who spent more than ₦50,000 in total but have less than 200 loyalty points. Return customer_id, full_name, total_spend, total_points.

	WITH customersx as (
	SELECT 
	customer_id,
	full_name

	FROM customers
	), 

	ordersx as (
	SELECT
	customer_id, 
	SUM(total_amount) as Total_Revenue
	FROM orders
	group by customer_id
	), 

	loyaltyx as (
	SELECT 
	customer_id, 
	SUM(points_earned) as loyalty_point

	FROM loyalty_points 

	GROUP BY customer_id
	)

	SELECT 
	c.customer_id,
	c.full_name,
	o.Total_revenue AS Total_Spend, 
	l.loyalty_point 

	FROM customersx c
	LEFT JOIN ordersx o
		ON c.customer_id = o.customer_id
	LEFT JOIN loyaltyx l 
		ON c.customer_id = l.customer_id

	where Total_Revenue > 50000 AND loyalty_point < 200

## Question 12 	
## Flag customers as churn_risk if they have no orders in the last 90 days (relative to 2023-12-31) AND are in the Bronze tier. Return customer_id, full_name, last_order_date, total_points.
	
	with orders_90Days as (
	SELECT
	c.customer_id,
	c.full_name,
	MAX(order_date) as Last_order_date

	FROM orders o
	LEFT JOIN customers c
	ON o.customer_id = c.customer_id 


	GROUP BY c.customer_id, full_name

	),
	customer_tier as (
	SELECT 
	customer_id,
	SUM(points_earned) as total_points,
	CASE    WHEN SUM(points_earned) < 100 THEN 'Bronze'
        	WHEN SUM(points_earned) between 100 and 499 THEN 'Silver'
        	WHEN SUM(points_earned) >= 500 THEN 'Gold'
        	END AS tier 
	FROM loyalty_points

	GROUP BY customer_id

	)
	SELECT 
	ct.customer_id,
	os.full_name,
	ct.total_points,
	os.Last_order_date,
	ct.tier

	FROM customer_tier ct 
	left join orders_90Days os
	ON ct.customer_id = os.customer_id

	WHERE  DATEDIFF(day, os.last_order_date, '2023-12-31') > 90 AND tier = 'Bronze'

##END 
