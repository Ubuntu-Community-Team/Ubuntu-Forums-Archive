---
title: "Installation step failed: select and install software using alternate CD"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by josno on 2009-04-27
I've tried to install both kubuntu and ubuntu on my Athlon X2 4200+ with 2GB RAM using the alternate CD (I'm putting my 2 200GB disks in RAID 1) and have hit the same problem - the installation fails on installing software. The iso files' MD5 checksums match and the CD I'm using checks out, but the install console says there's a Hash Sum mismatch in usbutils (for both CDs...). Any idea what the problem might be?

---

### Post by josno on 2009-04-27
I managed to solve this problem by manually installing the package: switching to a terminal using alt+f2, chrooting into /target, editing the sources.list to use the mirrors and not the cdrom (installing vim first), doing an ```
aptitude install usbutils
``` and then re-running the install software step.

---

