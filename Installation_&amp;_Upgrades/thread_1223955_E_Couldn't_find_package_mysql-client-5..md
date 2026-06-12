---
title: "E: Couldn't find package mysql-client-5."
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by kronicle on 2009-07-26
i made a fresh install of ubuntu 7.04 (Feisty Fawn) and i need to get the following
packages installed on it, apache2-mpm-prefork php5 php5-mysql mysql-server-5.0 mysql-client-5.
so i run the command 

sudo apt-get install apache2-mpm-prefork php5 php5-mysql mysql-server-5.0 mysql-client-5.0 .

and this is what i get in return

ubuntu@ubuntu:~$ sudo apt-get install apache2-mpm-prefork php5 php5-mysql mysql-server-5.0 mysql-client-5.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql-client-5.

but i am able to use apt-get to install the other packages individually except mysql-client-5.

really need ur help.

---

### Post by kronicle on 2009-07-27
seems no one is willing to help,
how do want us to have interest
in linux if the experienced users are
not willing to help us the newbies?????????

---

### Post by Soul-Sing on 2009-07-27
> i made a fresh install of ubuntu 7.04 (Feisty Fawn) and i need to get the following

Hi, ubuntu 7.04, even the server-edetion, is not very long supported anymore afaik.
I recommend to install ubuntu 8.04.(3) or the 9.04 edition, if you want a fresh install.

---

### Post by Soul-Sing on 2009-07-27
```
ubuntu@ubuntu:~$ sudo apt-get install apache2-mpm-prefork php5 php5-mysql mysql-server-5.0 mysql-client-5.
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql-client-5.
```

try: ```
sudo apt-get install apache2-mpm-prefork php5 php5-mysql mysql-server-5.0 mysql-client-5
```
without the "dot" at the end.

---

