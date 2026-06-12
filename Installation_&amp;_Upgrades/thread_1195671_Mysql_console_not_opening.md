---
title: "Mysql console not opening"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by bjindal on 2009-06-24
hi

I installed Xampp on ubuntu. Everything works fine but i am not able to open console for mysql.

I did the following to open the console for Mysql which has no password.

bhavana@bhavana-desktop:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bhavana@bhavana-desktop:~$ 

Why is this happening?Plz give a solution.
Plz help me.

Thanks in advance.
Bhavana

---

### Post by dsavi on 2009-06-24
A quick googling of your error reveals that you could have another SQL server running on the same port, or that it is denying connections from ips other than localhost.

Here's a quote from another forum that could solve your problem:
[http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_-2.html](http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_-2.html)
> Hi there,

In my case I solved the problem:
***
050817 22:34:22 Can't start server: Bind on TCP/IP port: Cannot assign requested address
050817 22:34:22 Do you already have another mysqld server running on port: 3306 ?
***

in the following manner:

Edit the file /etc/mysql/my.conf and find the section for bind-address and enter there your IP address.
I hope that helps. :)

---

### Post by bjindal on 2009-06-25
Hi

Thanks a lot I m able to run my Mysql console

I did this and it worked:

sudo /opt/lampp/bin/mysql -u root -p

Bhavana

---

