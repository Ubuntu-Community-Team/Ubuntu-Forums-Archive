---
title: "error in installayion"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by janagarraja on 2009-08-25
hi

when i install ubuntu after windows xp as dual boot

i had an error after partition

the error is Input/Output error on /sda/dev

what can i do to overcome this without formatting my entire hard disk

thanks

---

### Post by dstew on 2009-08-25
That error implies a corrupt file system or disk hardware problem. Boot a Live CD, open a terminal window, and do```
fsck -r /dev/sda1
```for example to check the first partition on /dev/sda1.

---

