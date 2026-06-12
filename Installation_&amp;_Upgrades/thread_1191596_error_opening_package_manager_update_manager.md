---
title: "error opening package manager update manager"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by devananda on 2009-06-19
in jaunty,,osystem .
eee pc 1000h 

since my internet connection suddenly was,interrupt for some time..
now the connection is back ,,but i cant acces my package manager or update manager..
i got the following message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

i need help to solve this issue!!!!!!!!!!!!!!!
thanks a lot

---

### Post by devananda on 2009-06-19
is this a bug???

---

### Post by Therion on 2009-06-19
No, it's not a bug.  Try selecting a different server or do updates via the Terminal:

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by scales on 2009-06-19
maybe open up a terminal and type
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

in that order

---

### Post by devananda on 2009-06-19
i got the same error again
;
~$ sudo aptitude update
[sudo] password for ryeknow: 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
  

anything else i can do to solve this??

---

### Post by devananda on 2009-06-19
it wont work with the commands
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

i just got the same error message:(

---

### Post by devananda on 2009-06-19
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
:icon_frown:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid-backports_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'




so it seems to be a bug!!!!!!
i cant acces any progrms like package manager,update manager

---

### Post by devananda on 2009-06-19
> **devananda said:**
> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
:icon_frown:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid-backports_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'




so it seems to be a bug!!!!!!
i cant acces any progrms like package manager,update managerpls help meeee

---

### Post by raymondh on 2009-06-19
> **devananda said:**
> pls help meeee

Devananda ... there is a reason why we do our best not to double post.  

See your other thread (of the same issue .... 'major failure of software management system) as tgilati4 has a valuable input for you there.

Hope that helps you.  Peace.

---

