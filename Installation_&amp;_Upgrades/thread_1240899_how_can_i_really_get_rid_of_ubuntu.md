---
title: "how can i really get rid of ubuntu??"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by yagamihachi on 2009-08-15
i'm dual-booting ubuntu and xp. and i want to install windows 7 after i delete ubuntu. i really can't get rid of ubuntu. help please! i'm using MSI wind U100+

---

### Post by mostafa178 on 2009-08-15
Boot into the ubuntu Live environment from the CD. Open terminal and type "sudo gparted" and delete the Ubuntu partition.

---

### Post by Partyboi2 on 2009-08-15
Hi, you can boot a Ubuntu live cd and open gparted (System>Admin>Partition Editor) and remove the Ubuntu partition(s). Then boot the windows cd and go to the recovery console and type
```
fixmbr
``` then reboot.

---

