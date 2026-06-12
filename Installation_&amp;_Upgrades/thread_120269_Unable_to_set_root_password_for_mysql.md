---
title: "Unable to set root password for mysql"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by [nordis] on 2006-01-21
Hi all Ubuntu fans.
I'm running Breezy, and I was going to setup a geeklog site.
But I can't connect to my mysql server.
I've followed some of the tips on this forum but with no luck.
All I get is:
```

nordis@ubuntu:~$ telnet 127.0.0.1 3306
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
H#HY000Host '127.0.0.1' is not allowed to connect to this MySQL serverConnection closed by foreign host.

```
or:
```
nordis@ubuntu:~$ mysql --protocol=tcp -hlocalhost -uroot -p
Enter password: (this should be my root passwd)
ERROR 2005 (HY000): Unknown MySQL server host 'localhost' (1)

```
or:
```
root@ubuntu:/home/nordis# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
Enter current password for root (enter for none):
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Enter current password for root (enter for none):

```

I can't login to phpmyadmin or webmin, but I can su to get root access in bash.

If I can't get access to mysql I'll go back to gentoo or debian.

---

