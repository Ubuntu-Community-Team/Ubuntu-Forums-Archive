---
title: "MySQL Question"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by neolev on 2005-12-17
Hey i'm trying to access MySql database once i install it via

sudo apt-get install mysql-server

Once installed....i am trying to access the server via

mysql -u root mysql

returns:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

also tried:

mysql -u root -p mysql
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

Still cant access the database anyone have any ideas??

Neolev

---

### Post by joshuapurcell on 2005-12-17
Did you make sure the server is started? Type:> ps -ef | grep mysql

---

### Post by Moobert on 2005-12-17
[QUOTE=neolev]Hey i'm trying to access MySql database once i install it via

sudo apt-get install mysql-server

Once installed....i am trying to access the server via

mysql -u root mysql

returns:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

also tried:

mysql -u root -p mysql
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

Still cant access the database anyone have any ideas??

Neolev[/QUOTE]

first login using:
```

mysql -u root

```

then set a new password by:

```

set password for root@localhost = password('xxxxxxx');
flush privileges;
quit;

```

Then log back in using:

```

mysql -p -u root

```

enterng the password you just set, you need to then setup normal database users, see:

[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

I'd also look into installing phpmyadmin, it gives you great web based admin for all things mysql.

---

