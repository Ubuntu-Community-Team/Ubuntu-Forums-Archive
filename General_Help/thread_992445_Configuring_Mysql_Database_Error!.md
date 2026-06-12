---
title: "Configuring Mysql Database Error!"
date: 2008-11-24
forum: General Help
---

### Post by waloshin on 2008-11-24
Every time i enter this command : mysql -u root -p

I get this error when i enter my password: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


What i am trying to do is configure a blank database for a SMF forum install, and the problems I ave ran across so far is turning my hair grey!

---

### Post by reality1011 on 2008-11-24
sudo /etc/init.d/mysql start

Then try to do what you are doing

---

