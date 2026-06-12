---
title: "Troubling installing updates"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by xoppaw on 2009-03-16
I am having some trouble doing any updates on my computer. When I do a sudo apt-get update it retrieves all the new packages, but when I do a sudo apt-get update this is what happens:

> 
maddox@3036-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  dash dkms firefox-3.1 firefox-3.1-branding libpurple-bin libpurple-dev libpurple0 pidgin pidgin-data pidgin-dev xulrunner-1.9.1
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.5kB/14.2MB of archives.
After this operation, 750kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main dkms 2.0.20.4-0ubuntu2.1 [55.5kB]
Fetched 55.5kB in 1s (46.9kB/s)
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1404 package `openprinting-ppds':
 `Suggests' field, syntax error after reference to package `foomatic-fifiles'
E: Sub-process /usr/bin/dpkg returned an error code (2)
maddox@3036-laptop:~$

when i do a sudo dpkg-reconfigure -a i get:

> 
maddox@3036-laptop:~$ sudo dpkg-reconfigure -a
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 1404 package `openprinting-ppds':
 `Suggests' field, syntax error after reference to package `foomatic-fifiles'
/usr/sbin/dpkg-reconfigure: acl is not installed
maddox@3036-laptop:~$


I'm not new to Ubuntu, but this is a new error that I haven't ran into before, so TIA for any suggestions. 

-xoppaw

---

### Post by xoppaw on 2009-03-18
no suggestions yet? 
well then i suppose it will be time for a re-install.

---

