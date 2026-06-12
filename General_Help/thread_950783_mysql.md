---
title: "mysql"
date: 2008-10-17
forum: General Help
---

### Post by charanpreethu on 2008-10-17
can anybody tell me how to install mysql

---

### Post by Ryadt on 2008-10-17
```
sudo apt-get install mysql-client-5.0
```

---

### Post by charanpreethu on 2008-10-17
what is the difference between mysql client and mysql server??

---

### Post by Ryadt on 2008-10-17
The mysql server is like a program where you store and manage all your databases. The mysql-client is like a program that allows you to write to the database.

---

### Post by charanpreethu on 2008-10-17
then i have to install both to create & manage a database rite???

---

### Post by ww711 on 2008-10-17
mysql client - is a tool for manipulating databases through a graphical interface, e.g. running querys, connecting to and managing databases, etc

mysql server - is where the data is stored and returns information to the querys that were made to the database(s).

---

### Post by ww711 on 2008-10-17
> **charanpreethu said:**
> then i have to install both to create & manage a database rite???

You can manage a sql server through the mysql commandline; using a mysql client is optional.

---

### Post by cariboo on 2008-10-17
When you install mysql-server, mysqlclient is one of the dependancies. 

Jim

---

### Post by Paul41 on 2008-10-17
You can also manage mysql with phpmyadmin.

---

