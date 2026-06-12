---
title: "sysnaptic package manager problem"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by billgr17 on 2009-04-04
sysnaptic package manager doesnt open !!
it says :

An error occurred

The following details are provided:
-----------------------------------------------------------------------
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
-----------------------------------------------------------------------
what did i need to do ?
plz help
i cant install anything !!!!!!!!!!!

](*,)

---

### Post by Kevbert on 2009-04-04
Please go to Applications-Accessories-Terminal and enter
```
sudo dpkg --configure -a
```
Enter your login password when prompted (it won't be displayed when you type it in).
If you get additional errors please post back.

---

### Post by billgr17 on 2009-04-04
it works again :)
thnx a lot man  !!!!!!!!!!!!!!!!!!!

---

