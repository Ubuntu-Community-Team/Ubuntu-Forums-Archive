---
title: "mysql error - ahh"
date: 2008-10-22
forum: General Help
---

### Post by Dthorton15 on 2008-10-22
I have googled - searched forums - searched this forum I cant ever seem to find a fix for this 

```
samiam@webserver10:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run         /mysqld/mysqld.sock' (2)

```
How can I fix this?

---

### Post by cariboo on 2008-10-22
You have to use the username and password you setup when you installed mysql. The default is root, so use root as the user and the password you set on installation eg:

```
mysql -u root -p
```

Enter the password when asked and it should result in this:

```
 mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 701
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
```

If you need a graphical interface, phpmyadmin a web based interface is available in the repositories

Jim

---

### Post by Dthorton15 on 2008-10-23
when i type ```
mysql -u root -p
```i put in my password and get this ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```I am totally lost as how to fix this.

---

