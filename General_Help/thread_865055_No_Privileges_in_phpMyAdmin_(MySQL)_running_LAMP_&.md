---
title: "No Privileges in phpMyAdmin (MySQL) running LAMP &amp; webmin"
date: 2008-07-20
forum: General Help
---

### Post by tvor on 2008-07-20
I have successfully installed LAMP and Webmin. I intent to use it for only local Joomla installation testing on my PC. All running happily, including phpMyAdmin, but there, I have no privileges to create new database. During LAMP setup I have been asked for root user name and this works with no password while login to phpMyAdmin.

Also I'm unable to modify MySQL Database Server through Webmin as is says "> DBI connect failed : Access denied for user ''@'localhost' to database 'mysql' I have tried to run mysql_install_db , as suggested in[http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html")but made no difference :-( Any complex ideas with simple solution are always welcome! Thank you very much.

---

### Post by bruno.vitorino on 2008-11-16
Have you tried to run mysql_secure_installation after mysql_install_db?

---

### Post by Francewhoa on 2009-06-21
To be able to create new database in phpMyAdmin you must login as ROOT. To do so.
1. Go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
2. Type in username
      root

Password is usually your Ubuntu root password/administrator password.

---

### Post by bobski60 on 2011-10-02
lol went all over the web to get that answer lol thanks.... why go all over the web only to find it here.
I did try searching but got all sorts of answers that I didnt want lol..
THANKS again

---

### Post by trueblue71 on 2011-10-27
> **Onopoc said:**
> To be able to create new database in phpMyAdmin you must login as ROOT. To do so.
1. Go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
2. Type in username
      root

Password is usually your Ubuntu root password/administrator password.
Thank you!! I've been searching for hours and this ended up being the solution.

---

