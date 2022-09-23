# Datagrid 8(Infinispan) sql-cache-store
This repository aims to demonstrate the sql-cache-store feature of Datagrid 8 and show 3 approaches with examples of different types of bases such as Oracle and Postgresql, and their deployment in Openshift.

## Prepare Openshift

* Create a namespace
  
  ```shell script
  oc new-project <your namespace>
  ```

* Install Datagrid(infinispan) Operator

    From Openshift Operator Hub, search for Datagrid Operator, and install it. 

  ![](/images/InstallDatagridOperator.png)

## Prepare databases

* PostgreSQL
  
  From Openshift console, click in "+Add" button and following click in Database like image bellow:

  ![](/images/InstallPostgreSQL1.png)

  Select PostgreSQL template and create on instantiate template:

  ![](/images/InstallPostgreSQL2.png)

  Fill in the username and password fields and click create:

  ![](/images/InstallPostgreSQL3.png)

  Wait for deployment complete and login on postgre pod terminal and login with following command:

  ```shell script
  psql -h 0.0.0.0 -d sampledb -U user
  ```
  Create a table for query-jdbc-store:

  ````shell script
  CREATE TABLE _keys(
      _id SERIAL NOT NULL,
      _key VARCHAR(50) NOT NULL,
      _value VARCHAR(50) NOT NULL,
      PRIMARY KEY ( _id )
  );
  
  ```

  Insert a record or more with this command:

  ````shell script
  INSERT INTO _keys(_key,_value) VALUES('99999999999','omelo@redhat.com');
  ```

  Run the command below to check if the records were inserted:
  
  ````shell script
  SELECT * FROM _keys;
  ```

  Logout from terminal and back to Openshift Console.

* Oracle

## Prepare pv with the database drivers

## Install Datagrid Cluster

## Create protobuff schemas for caches

## Create caches
