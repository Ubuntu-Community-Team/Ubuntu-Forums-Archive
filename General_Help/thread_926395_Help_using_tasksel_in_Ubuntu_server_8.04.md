---
title: "Help using tasksel in Ubuntu server 8.04"
date: 2008-09-21
forum: General Help
---

### Post by wakelagger on 2008-09-21
when ever i try to install something from tasksel i get this message

debconf: DbDriver "config": could not write /var/cache/debconf/sonfig.dat-net: Permission denied
tasksel: debconf failed to run

im rather new to linux so it is possible i just did something stupid on install but any help is good.
thank you

---

### Post by jpkotta on 2008-09-23
Try running it as root.  Only root can write to that directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

