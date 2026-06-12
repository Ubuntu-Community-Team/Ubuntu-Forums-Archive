---
title: "Problems update manager"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by devananda on 2009-05-22
in my ubuntu 9.4 eeepc 1000ha..
when i enter the update manager and start updating the programs its stopped by this
sign::

error

: dpkg was interruEpted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone help me plesae
:confused:

---

### Post by theozzlives on 2009-05-22
Go to applications > Accessories > Terminal and type:
```
sudo dpkg --configure -a
```

---

### Post by devananda on 2009-05-22
thank you now it seems  to be working great:p

---

