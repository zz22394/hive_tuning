# hive_tuning

hive work flow
![Hive work flow](workflow/DataETL.png)

## 00. Table status list up
List up status for all the 400 tables in CATS project.

* table name
* location (s3 path)
* Store type (TXT / ORC)
* partition used
* partition number
* if or not in the list of (Tables with too many Paritions)
* if or not managed table
* count(*)


## 11. Convert the CDP unmanaged table into managed table

Goal: improve count(*) / aggreation functions' performance

```sql
CREATE TABLE source_table_1_managed
AS select * from source_table_1 
```

## 12. Convert the small files/text files into ORC files

### Original table is managed table:

```sql
CREATE TABLE source_table_1_orc
    STORED AS ORC
AS select * from source_table_1 
```

### Original table is external table:

```sql
CREATE EXTERNAL TABLE source_table_1_orc
    STORED AS ORC
AS select * from source_table_1 
```

## 13. Merge partitions

### Original table is managed table:

TBD
