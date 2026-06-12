---
title: "gdebi installs fail"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by SonnHalter on 2009-03-21
when ever i try to install a deb file it tells me Error: Wrong architecture 'i386'

but that is my architecture. I have an intel processor. 

getting really annoying

---

### Post by prshah on 2009-03-21
> **SonnHalter said:**
> Error: Wrong architecture 'i386'


You may be trying to install i386 on a X_64 capable system (64bit ; Eg., Core2 Duo) or vice versa.

To check what architecture you are using, open a terminal (Applications-Accessories-Terminal) and give the command```
uname -m
```

---

