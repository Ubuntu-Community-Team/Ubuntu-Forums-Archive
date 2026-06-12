---
title: "XAMPP won't connect."
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-01-17
I have installed xampp it start very well I can connect to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) 
I have installed Mysql Administrator and Msql querry Browser using synactic
but I can not connect to the mysql db true Administrator or querry Browser.
On the console I am getting the following error
when I use mysql
I get the following error
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
After long time googling here I am

---

### Post by TANGO! on 2009-01-17
I'm having the exact same problem.  After lots of googling and searching for possible solutions in this forums, and reading the Mysql manuals.  Help please...

Bumpity

---

### Post by kranny on 2009-01-17
Hi,

The problem here i think might be that the mysql-browser doesnt find the correct sock file it is searching for.There should be some place to change configuration for mysql-query-browser.But here is a quick fix.

Create /var/run/mysqld directory
Create soft link for mysql.sock from xampp directory

```
sudo ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock
```

---

### Post by TANGO! on 2009-01-17
Awesome, that did it for me!!!

Thank you very very much hoboy, I didn't have to get into editing the my.cnf file.:D

I can't find the "thx" thingy here in the forum... can only the starter of the thread give thanks?

---

### Post by kranny on 2009-01-18
The reply was given by me tango:P:P
Btw the mods removed thanks giving option recently.

---

### Post by hoboy on 2009-01-18
Thanks you are genius, my problem is solved.

---

### Post by TANGO! on 2009-01-18
Oopsies, you're right, a million thanks Kranny! I'm sure the post will help lots of other people in the future.

---

### Post by kaqfa on 2011-03-26
Thank you for the solution, it works for me :)

---

