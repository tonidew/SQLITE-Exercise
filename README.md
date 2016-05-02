# SQLITE-Exercise

**1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.**
```SQL
SELECT FirstName, LastName, CustomerId, Country
FROM Customer
WHERE Country != "USA"
```

**2. Provide a query only showing the Customers from Brazil.**
```SQL
SELECT FirstName, LastName, Country
FROM Customer
WHERE Country = "Brazil"
```

**3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.**
```SQL
SELECT c.FirstName, c.LastName, i.InvoiceId, i.InvoiceDate, c.Country
FROM Invoice i
INNER JOIN Customer c
WHERE Country = 'Brazil';
```
**4. Provide a query showing only the Employees who are Sales Agents.**
```SQL
SELECT FirstName, LastName, EmployeeId, Title
FROM Employee e 
WHERE Title is 'Sales Support Agent'
```

**5. Provide a query showing a unique list of billing countries from the Invoice table.**
```SQL
SELECT DISTINCT BillingCountry
FROM Invoice i
```

**6. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.**
```SQL
SELECT e.LastName, e.FirstName, e.Title, i.InvoiceId
FROM Employee e
INNER JOIN Customer c
on c.SupportRepId = e.EmployeeId
INNER JOIN Invoice i
on c.CustomerId = i.CustomerId
WHERE Title is 'Sales Support Agent'
```

**7. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.**
```SQL
SELECT c.FirstName, c.LastName, c.Country, i.Total, e.FirstName, e.LastName
FROM Customer c
INNER JOIN Employee e
on e.EmployeeId = c.SupportRepId
INNER JOIN Invoice i
on i.CustomerId = c.CustomerId
WHERE Title is 'Sales Support Agent'
```

**8a. How many Invoices were there in 2009 and 2011?** 
```SQL
Query for 2009 invoices:
Answer: 83

SELECT COUNT(InvoiceDate)
FROM Invoice i
WHERE InvoiceDate BETWEEN '2009-01-01' AND '2010-01-08';

Query for 2011 invoices:
Answer: 83

SELECT COUNT(InvoiceDate)
FROM Invoice i
WHERE InvoiceDate BETWEEN '2011-01-02' AND '2012-01-01';
```
**8b. What are the respective total sales for each of those years?**
```SQL
Query for 2009:
Answer: 449.46
SELECT COUNT(i.InvoiceDate), SUM(i.Total)
FROM Invoice i
WHERE InvoiceDate BETWEEN '2009-01-01' AND '2010-01-08';

Query for 2011:
Answer: 469.58
SELECT COUNT(InvoiceDate), SUM(i.Total)
FROM Invoice i
WHERE InvoiceDate BETWEEN '2011-01-02' AND '2012-01-01';
```

**9.Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.**
```SQL
SELECT COUNT(i.InvoiceLineId)
FROM InvoiceLine i
WHERE i.InvoiceId = 37;
```

**10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY**
```SQL
SELECT  i.InvoiceId, COUNT(i.InvoiceLineId)
FROM InvoiceLine i
GROUP BY InvoiceId;
```

**11.Provide a query that includes the track name with each invoice line item.**
```SQL
SELECT i.InvoiceLineId, i.InvoiceId, i.TrackId, i.UnitPrice, i.Quantity, t.Name
FROM InvoiceLine i
INNER JOIN Track t
on t.TrackId = i.TrackId;
```
**12.Provide a query that includes the purchased track name AND artist name with each invoice line item.**
```SQL

**13.Provide a query that shows the # of invoices per country. HINT: GROUP BY**
```SQL
SELECT COUNT(InvoiceId), BillingCountry
FROM Invoice
GROUP BY BillingCountry;
```
**14. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resulant table.**
```SQL

```
**15.Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.**
```SQL
SELECT 
t.Name AS "Songs", a.Title AS "Album", g.Name AS "Genre", m.Name AS "Media"
FROM Track t
INNER JOIN Album a
ON a.AlbumId = t.AlbumId
INNER JOIN Genre g
ON g.GenreId = t.GenreId
INNER JOIN MediaType m
ON m.MediaTypeId = t.MediaTypeId;
```
**16.Provide a query that shows all Invoices but includes the # of invoice line items.**


