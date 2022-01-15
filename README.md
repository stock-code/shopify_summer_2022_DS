## Shubham Gajera 
# shopify_summer_2022_DS
This repo is for Shoipify data science intern role analysis challenge.


## Question 1a.
### Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.
* When using the AOV, calculation done with average order amount without taking into account the number of pairs of shoes purchased in each transaction.
* there are some transactions that are extream/outliers/error:The 17 indentical transactions that included 2000 purchases each are driving up the AOV.

## Question 1b.: 
### What metric would you report for this dataset?
* As far as I think because of some unsual extream data points we should calculate our AOV according to **Median**, which give more better overview of each transactions and will not affect with extreame cases or outliers.

## Question 1c.:
### What is its value?
* I would say **284** is more reasonable value defined by median of datasat for AOV compare to 3145.128 which lead by extrme points/outliers.

## Question 2a.
### How many orders were shipped by Speedy Express in total?
* Answer: 54

* SELECT COUNT(*)
FROM Orders AS o, Shippers AS s
WHERE o.ShipperId = s.ShipperId AND ShipperName = "Speedy Express";

## Question 2b.
### What is the last name of the employee with the most orders?
* Answer: Handel
(10 orders)

* SELECT c.CustomerName, COUNT(*) AS Count
FROM Orders AS o, Customers AS c
WHERE o.CustomerID = c.CustomerID
GROUP BY o.CustomerID
ORDER BY Count DESC
LIMIT 1;

## Question 2c.
### What product was ordered the most by customers in Germany?
* Answer: Boston Crab Meat
(ProductID: 40, TotalQuantity: 160)

* SELECT p.ProductID, p.ProductName, SUM(Quantity) AS TotalQuantity
FROM Orders AS o, OrderDetails AS od, Customers AS c, Products AS p
WHERE c.Country = "Germany" AND od.OrderID = o.OrderID AND od.ProductID = p.ProductID AND c.CustomerID = o.CustomerID
GROUP BY p.ProductID
ORDER BY TotalQuantity DESC
LIMIT 1;
