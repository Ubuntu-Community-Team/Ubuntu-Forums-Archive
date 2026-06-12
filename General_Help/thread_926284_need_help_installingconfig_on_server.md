---
title: "need help installing/config on server"
date: 2008-09-21
forum: General Help
---

### Post by lahp on 2008-09-21
hey its me again for those who remeber me i have come along way ina few hours and i am now installing mysql its installed i just need to config i dont know who to get it working with my phpadmin? any help

---

### Post by cariboo on 2008-09-21
First make sure mysql is running, in a terminal type:

```
ps ax | grep mysql
```

If it is running, you should get an output that looks like this:

```
 ps ax | grep mysql
 9686 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 9807 ?        Sl     0:16 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 9808 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
13605 pts/0    R+     0:00 grep mysql
```

If mysql is running, the next thing to do is to try and access the mysql console. In the same terminal type:

```
mysql -u root -p
```

Enter the password you set when you installed mysql, and if everything works right you should be at a mysql command prompt. To exit the console type \q.

To use phpmyadmin, open firefox and in the address bar enter:

```
http://localhost/phpmyadmin
```

Enter root for the user name and the password you created when you installed mysql to login. you can now play with your new database.

Jim

---

