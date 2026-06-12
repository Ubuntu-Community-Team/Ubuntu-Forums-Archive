---
title: "installing programs"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by David87 on 2009-04-21
I'm having trouble installing programs in Ubuntu. For some reason whenever I go to Add/Remove and ask it to reload the list of programs it comes up with:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone please translate that into english? How do I fix the problem so I can install programs?

---

### Post by Partyboi2 on 2009-04-22
Hi, do as it suggests, open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

### Post by dmm1983 on 2009-04-22
i agree with the above post
i have i had to use this command many times myself.
Fixes the problem that occurred.

---

### Post by JK3mp on 2009-04-22
Never had that exact problem... but obviously you should usually do what it tells you to do to fix it if you wanna fix it ;)

---

