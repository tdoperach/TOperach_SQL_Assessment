# TOperach_SQL_Assessment
For PMG Graduate Leadership Program Technical Assesment

* Question #1 Generate a query to get the sum of the clicks of the marketing data​

  >Select SUM(clicks) AS 'Clicks' 
  >FROM marketing_data

* Question #2 Generate a query to gather the sum of revenue by store_location from the store_revenue table​

>SELECT store_location, 
>SUM(revenue) AS 'Revenue'
>FROM store_revenue 
>GROUP BY store_location

* Question #3 Merge these two datasets so we can see impressions, clicks, and revenue together by date and geo. Please ensure all records from each table are accounted 
for.​

>SELECT marketing_data.date,
>marketing_data.geo,
>marketing_data.impressions,
>marketing_data.clicks,
>store_revenue.brand_id,
>store_revenue.revenue
>FROM marketing_data
>FULL JOIN store_revenue ON store.revenue.date = marketing_data.date AND RIGHT(store.revenue.store_location,2) = marketing_data.state

* Question #4 In your opinion, what is the most efficient store and why?​

Revenue Per Click by state:
CA: $759
NY: $972
TX: $1,001
MN: Unknown

Texas would be the more efficient store as it has the highest revenue per click at $1,001. Revenue per click would be the best metric to show efficiency as it shows the how much "bang for your buck" the stores are getting per click. However, Minnesota is unknown, as it is missing from the store revenue table, so there is a possibility it is the most efficient store.

* Question #5 (Challenge) Generate a query to rank in order the top 10 revenue producing states​
 
>SELECT TOP 10 store_location, 
>SUM(revenue) AS 'Revenue'
>FROM store_revenue 
>GROUP BY store_location
ORDER BY SUM(Revenue) DESC  
