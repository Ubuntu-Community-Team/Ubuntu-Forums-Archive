---
title: "upgrate to 9.4 with live cd"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by royaflash on 2009-06-23
hellow and be linux

i have ubuntu 8.10 on my system and i want upgrate to 9.4
ican?

i want upgrate without alternate version 

thanks

---

### Post by dsavi on 2009-06-23
If you upgrade with a CD, all the system files are removed but your home directory (/home/*username*) is kept. That means that any programs you installed that do not come with Jaunty will be removed and you will have to install them again.

If you want to keep the programs, you can open a terminal and type in
```
update-manager -c
```
And it will guide you nicely through installing the new system.

---

