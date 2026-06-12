---
title: "[SOLVED] Cannot create mysql database - help please"
date: 2008-09-25
forum: General Help
---

### Post by mamboze on 2008-09-25
I've struggled with this problem for a couple of days and I've run out of ideas. I've installed (and done a re-install) of Mysql server and client using sudo apt-get mysql.

This has given me the user account of roy@localhost with no password set
user name = roy and no password will get me into the MySQL Administrator

But
roy@prospero:~$ mysqladmin -u 'roy' create dummydb
mysqladmin: CREATE DATABASE failed; error: 'Access denied for user ''@'localhost' to database 'dummydb''

I don't know why ''@'localhost' is denied, this is not the user account that MySQL Administrator refers to.
I've tried variations on this command but have been unable to create a database. 
Any help would be very much appreciated. I'm desperate.

---

### Post by eggdeng on 2008-09-25
If you haven't set a root password, you should be able to login to mysql as root
```
mysql -uroot
```
to create your databases and grant privileges to users.

---

### Post by cariboo on 2008-09-25
You have mysql running so all you really need to set up your user properly. You shouldn't run a user without a password. THe user you created probably doesn't have enough privileges to create a database. To get around this problem try in the mysql console:

```
mysql -u root -p
```

To enter the mysql console. Use the password you created when you installed mysql. Now to give your user privileges to create a database:

```
grant all privileges on *.* to roy@'localhost
identified by 'password' with grant option;
```

Just in case you need remote access:

```
grant all privileges on *.* to roy@'%'
identified by 'password' with grant option;
```

Now roy should be able to do anything that root can.

Jim

---

### Post by indytim on 2008-09-25
After you have your password etc. squared away from the above threads, make it easy on yourself and install phpMyAdmin (it's in the repositories).  Gives you a nice web-bsed interface for administering your MySQL databases.

IndyTim

---

### Post by DrMega on 2008-09-25
> **indytim said:**
> After you have your password etc. squared away from the above threads, make it easy on yourself and install phpMyAdmin (it's in the repositories).  Gives you a nice web-bsed interface for administering your MySQL databases.

IndyTim

Or even easier, I have an app called "MySQL Query Browser" installed, which again is in the repositories. It took pretty much no setting up and gives you a nice GUI to the backend db.

---

### Post by mamboze on 2008-09-25
Hi all,

Thanks for the help.
Using the suggested commands:

roy@prospero:~$ mysql -uroot
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
roy@prospero:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
roy@prospero:~$ mysql -u roy -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 34
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> gran all privileges on *.* to new@'localhost
    '> gran all privileges on *.* to new@'localhost;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'gran all privileges on *.* to new@'localhost
gran all privileges on *.* to new@'' at line 1
mysql> grant all privileges on *.* to new@'localhost
    '> identified by 'password' with grant option; 
    '> 

mysql hangs at this point

It seems I don't have a root account. MySQL Administrator shows
user: roy   host: localhost. 

I'm not sure where to go from here.

---

### Post by eggdeng on 2008-09-26
```
roy@prospero:~$ mysql -u root -p
Enter password:
```
This would suggest that the root password is set. If you don't know it, you will have to reset it [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html]("http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html")
Alternatively & probably simpler & easier, just remove mysql and reinstall the LAMP package from Synaptic. Synaptic-> Edit-> Mark Packages by Task-> check LAMP Server & Apply. You will be asked to supply a root password during the install.

---

### Post by mamboze on 2008-09-26
At last, success. Following the 'last resort' method at the end of 
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
From the console: 
sudo apt-get --purge remove mysql-server mysql-common mysql-client
sudo apt-get install mysql-server mysql-common mysql-client

this put up an input screen which allowed me to set user and password. Synaptic did not do this

Since I had no data to worry about, this method was a no-brainer. 

Thanks to you all, I'm grateful for your help, individually and collectively. 

I love the Ubuntu forums, they express so well the ideals of cooperation and mutual help.

---

