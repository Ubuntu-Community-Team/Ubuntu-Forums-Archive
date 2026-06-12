---
title: "kernel security upgrade fails on depmod"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by dukeinlondon on 2009-03-29
A security upgrade of the kernel is leaving my computer a bit stumped : it freeze gnome hard on depmod. switching to a virtual console, I see plenty of ata errors.

the update manager recommends to use dpkg --configure -a to finish the interupted operation but that only reproduces the problem....

Is there a way out ?

---

### Post by dukeinlondon on 2009-04-01
figured it out :

To get dpkg unstuck I ran

sudo dpkg --remove --pending

---

