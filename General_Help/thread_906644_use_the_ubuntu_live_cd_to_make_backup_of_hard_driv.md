---
title: "use the ubuntu live cd to make backup of hard drive"
date: 2008-08-31
forum: General Help
---

### Post by washable mist on 2008-08-31
is there a way for my to create a backup of a hard drive onto another drive while using the ubuntu live cd.

---

### Post by washable mist on 2008-08-31
anyone got an idea

---

### Post by cariboo on 2008-08-31
You can use dd or partimage to make a copy of your hard drive, you will have to install partimage, it will run in ram as anything you install from the livecd will only work for that session. To use dd in a terminal:

```
dd if=/dev/sda1 of=/dev/sdb1
``` 

The above are only examples you will have to substitute your devices in the string. Partimage has a ncurses based gui, everything is pretty obvious.

Jim

---

