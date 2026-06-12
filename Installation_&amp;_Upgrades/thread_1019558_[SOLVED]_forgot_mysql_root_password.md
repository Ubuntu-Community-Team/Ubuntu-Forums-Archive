---
title: "[SOLVED] forgot mysql root password"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2008-12-23
I am just creating mysql database......... first i gave the password as 'manager' ..... .

But when i tried to install drupal it asked me to create a new database when i tried it gave error as shown. I entered the password correctly.
what should i do now ????????

code:

root@chinmaya:/home/chinmaya# mysqladmin -u username -p create database1
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'username'@'localhost' (using password: YES)'

Help me please.......!!!!!!!

---

### Post by chinmaya_n on 2008-12-24
ohhhhhhh !!!!!!

That was my mistake ......... i should have entered "root" in the place of username and the password as i gave the first time !!!!!

I got it !!!!!!

---

