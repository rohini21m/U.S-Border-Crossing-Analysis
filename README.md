SELECT TOP (1000) [Port Name]
      ,[State]
      ,[Port Code]
      ,[Border]
      ,[Date]
      ,[Measure]
      ,[Value]
      ,[Latitude]
      ,[Longitude]
      ,[Point]
  FROM [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]

  --No.of people entered on Dec 05
select COUNT(*) as 'People Entered'
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
where Date='Dec-05'


select COUNT(*) as 'Avg_Entry_Count'
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
group by Date
-- top ten states 
select State,[Port Name],Value
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
where Value is NOT NULL
Order by Value DESC
-No.of people crossing on border per a day
select Avg(CAST([Value] as Decimal(9,2))) as 'Avg_Entry_Count'
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]

--Top 10 Ports with high crossing density 
select top 10 [Port Code],[Port Name],State,Value,Date
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
order by Value DESC

-- Port with Least No.of people entering US.& Canada& u.s Mexico
select [Port Code],[Port Name],State,Value,Border
from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
where Value<10

-- Count of people entering through various measures types
select Count(*) as 'People Entering',Measure from [U.S Crossing border].[dbo].[Border_Crossing_Entry_Data]
group by Measure



  
  
  
