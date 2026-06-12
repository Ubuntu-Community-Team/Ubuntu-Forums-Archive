---
title: "Mysql Woes"
date: 2008-09-20
forum: General Help
---

### Post by Symbit on 2008-09-20
Hello,

I have installed mysql recently, and are having a serious issue with it.

I installed using "sudo apt-get install mysql-server-5.0", and it appeared to install with out issue.

However, when I try to login to my sql, I cannot create a database.

When I type "mysql" into the terminal, it goes to a prompt. But when I try a command like > create database mystuff;" I get "ERROR 1044 (4200): Access denied for user ''@'localhost' to database 'mystuff'

Nor can I login as root using > mysql -u root -p then  typing in my root password.

To my knowledge, I never knowingly set up a user nor password for mysql.

What can I do to get this to work?

Thanks!

---

### Post by mb_webguy on 2008-09-20
MySQL didn't ask you for a root password when you installed it?

Try reinstalling using Synaptic, and pay attention to any pop-ups.

If that doesn't work, try "sudo dpkg-reconfigure mysql-server-5.0"

---

### Post by Symbit on 2008-09-20
> **mb_webguy said:**
> MySQL didn't ask you for a root password when you installed it?

Try reinstalling using Synaptic, and pay attention to any pop-ups.

If that doesn't work, try "sudo dpkg-reconfigure mysql-server-5.0"

The first time that I installed MySQL, it did NOT ask me to input a root password.

However, when I ran "sudo dpkg-reconfigure mysql-server-5.0", it did ask me for a password for root.

Thank you mb_webguy!

---

