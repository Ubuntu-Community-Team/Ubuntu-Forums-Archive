---
title: "MySQL - lost root password"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by bzarr on 2009-03-18
Hi, hopefully someone can help me with this...

Whilst trying to get my web server to talk to my database server I have somehow managed to revoke all permissions to the mysql database. Thankfully I haven't yet migrated the data onto it, so I won't lose anything, but how do I reinstall MySQL and set new users/permissions?

I am running Ubuntu 8.10 (Ibex) Server, LAMP + SSH install with no GUI except phpmyadmin.

Thanks in advance!

---

### Post by upchucky on 2009-03-18
assuming the mysql password you set is different from the root password of ubuntu.

do sudo apt-get remove mysql then do sudo apt-get install mysql, this time write the password down that it asks you to set when it installs. make sure this password is not the same as ubuntu root password.

---

### Post by bzarr on 2009-03-18
Hi, thanks for replying...

I've tried this (although with mysql-server, not mysql as it doesn't find that), it'll happily do the removal and the installation, but on install does not ask for a new password.

And yes, the password is different to the system root password.

Hmmm...

---

### Post by upchucky on 2009-03-18
it should have asked you to set a password on the original install?

an apt-get remove --purge mysql-server should remove all files, and hopefully let the password file be recreated on a new install

someone either here or at linux questions.org should be able to tell you where the password file is created if needed.

unfortunately i no longer have mysql on my system so i can't look for it.

---

### Post by bzarr on 2009-03-18
Just gave that a try, no luck either, but does appear to do more of the installation after doing sudo apt-get install mysql-server again.

However, this time i'm getting a different error trying to access mysql from the command line:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Any ideas? Or should I hunt for the password file?

---

