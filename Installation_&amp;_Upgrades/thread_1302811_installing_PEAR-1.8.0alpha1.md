---
title: "installing PEAR-1.8.0alpha1"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2009-10-27
I want to install new pear becouse i have v1.6.1

requires PEAR Installer (version >= 1.8.0alpha1), installed version is 1.6.1


mitjab@server:~$ sudo pear install PEAR-1.8.0alpha1
Ignoring installed package pear/PEAR
Nothing to install

the same with v1.9.0

sudo pear install PEAR-1.9.0
Ignoring installed package pear/PEAR
Nothing to install
You have new mail in /var/mail/mitjab

How can i install it?

---

### Post by martrn on 2009-10-27
what do you get when you type the following at a terminal :

> dpkg-query -l 'pear*'
apt-cache search pear* | grep pear

---

