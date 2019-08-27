Project: Data Lakes with Hadoop, Spark and s3 
===================================



Pre-requisites
--------------

- Hadoop
- AWS
- Spark
- S3

Getting Started
---------------

To get started, open a console window and type "python etl.py"

You'll need to create an iam user and a S3 bucket

Support
-------

- AWS iam: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html
- AWS S3: https://aws.amazon.com/s3/


The purpose of this database in the context of the startup, Sparkify, and their analytical goals.
-------

A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

As their data engineer, I am tasked with building an ETL pipeline that extracts their data from S3, processes them using Spark, and loads the data back into S3 as a set of dimensional tables. This will allow their analytics team to continue finding insights in what songs their users are listening to.

An explanation of the files in the repository
-------

I Created the etl.py file. It pulls in data from an s3 bucket and transformes and loads the data into another s3 bucket. The dl.cfg file requires a aws access key and secret access key that you get when creating th iam user in AWS.

Please see table schema below:
-------

### Song data file schema
root
 |-- artist_id: string (nullable = true)
 |-- artist_latitude: double (nullable = true)
 |-- artist_location: string (nullable = true)
 |-- artist_longitude: double (nullable = true)
 |-- artist_name: string (nullable = true)
 |-- duration: double (nullable = true)
 |-- num_songs: long (nullable = true)
 |-- song_id: string (nullable = true)
 |-- title: string (nullable = true)
 |-- year: long (nullable = true)
 
### Long data file schema
 root
 |-- artist: string (nullable = true)
 |-- auth: string (nullable = true)
 |-- firstName: string (nullable = true)
 |-- gender: string (nullable = true)
 |-- itemInSession: long (nullable = true)
 |-- lastName: string (nullable = true)
 |-- length: double (nullable = true)
 |-- level: string (nullable = true)
 |-- location: string (nullable = true)
 |-- method: string (nullable = true)
 |-- page: string (nullable = true)
 |-- registration: double (nullable = true)
 |-- sessionId: long (nullable = true)
 |-- song: string (nullable = true)
 |-- status: long (nullable = true)
 |-- ts: long (nullable = true)
 |-- userAgent: string (nullable = true)
 |-- userId: string (nullable = true)

### Song table schema
root
 |-- song_id: string (nullable = true)
 |-- title: string (nullable = true)
 |-- artist_id: string (nullable = true)
 |-- year: long (nullable = true)
 |-- duration: double (nullable = true)
 
 ### Artist table schema
 root
 |-- artist_id: string (nullable = true)
 |-- artist_name: string (nullable = true)
 |-- artist_location: string (nullable = true)
 |-- artist_latitude: double (nullable = true)
 |-- artist_longitude: double (nullable = true)
 
  ### User table schema
 root
 |-- userId: string (nullable = true)
 |-- firstName: string (nullable = true)
 |-- lastName: string (nullable = true)
 |-- gender: string (nullable = true)
 |-- level: string (nullable = true)
 
 ### Time table schema
 root
 |-- ts: long (nullable = true)
 |-- hour(time_stamp): integer (nullable = true)
 |-- dayofmonth(time_stamp): integer (nullable = true)
 |-- weekofyear(time_stamp): integer (nullable = true)
 |-- month(time_stamp): integer (nullable = true)
 |-- year(time_stamp): integer (nullable = true)
 |-- date_format(time_stamp, EEEE): string (nullable = true)
 
 
  ### Plays table schema
 root
 |-- ts: long (nullable = true)
 |-- userid: string (nullable = true)
 |-- level: string (nullable = true)
 |-- song_id: string (nullable = true)
 |-- artist_id: string (nullable = true)
 |-- sessionid: long (nullable = true)
 |-- location: string (nullable = true)
 |-- useragent: string (nullable = true)