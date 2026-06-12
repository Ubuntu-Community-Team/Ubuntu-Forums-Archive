---
title: "pre-built kernels for different types of 386 processors"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by aajax on 2009-02-25
My experience with Debian (most current version being 3.1/Sarge) is that there are pre-built kernel packages that can be installed depending on the kind of CPU actually installed on the computer.  This especially included kernel packages that supported symmetric multiprocessors (SMP).  I don't see any such thing for Ubuntu.  How are such customizations handled in Ubuntu?  Is it possible that users have to compile their own kernel to get SMP support?

---

### Post by deepclutch on 2009-02-25
SMP support is already there in generic kernel.look at /boot/config-`uname -r` file.

---

