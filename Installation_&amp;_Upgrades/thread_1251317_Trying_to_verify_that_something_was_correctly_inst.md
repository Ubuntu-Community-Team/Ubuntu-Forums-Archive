---
title: "Trying to verify that something was correctly installed..."
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by 6 Theorem on 2009-08-27
Hello all,

I installed expat from source, and I am trying to verify that it installed correctly. Here is some confusing output from my command line:

> entropy@VonNeumann:~$ sudo apt-get install expat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
expat is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
entropy@VonNeumann:~$ whereis expat
expat:

I don't plan on working with expat directly, but I am trying to install a library that depends on it (and it refuses to install, don't know why).

So I guess my question is, is it normal for whereis to sometimes not be able to locate things? If so, is there another way I can ensure that expat is functional?

Thanks!

---

### Post by ajgreeny on 2009-08-27
I don't know, but I wonder if **whereis** needs ```
sudo updatedb
```just like **locate** before it will find the files for the package that I assume is very newly installed.

---

### Post by 6 Theorem on 2009-08-27
I think I figured it out. Apparently the package it needed was called "libexpat-dev." Hm

---

