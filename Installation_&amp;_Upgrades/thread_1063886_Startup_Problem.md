---
title: "Startup Problem"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Prakash, B.S. on 2009-02-08
Installed Ubuntu 8.10 on a second hard disk of 40 GB hard drive (partitioned it into a 20GB '/', and a 1 Gb '/boot' and a 1 GB 'swap' partition, rest as free,formatted with ext 3 file system)intel 845 chipset, 512 MB Ram, Intel Celeron 2.13 Ghz Processor with windows XP on another 80 GB hard drive (dualbooting with ubuntu). Installation went fine, after restart login user name and password were asked and given. Then screen goes black nothing is seen. Please help. This is the first time i am installing a linux OS on my PC.

---

### Post by uidb4056 on 2009-02-08
> **Prakash, B.S. said:**
> Installed Ubuntu 8.10 on a second hard disk of 40 GB hard drive (partitioned it into a 20GB '/', and a 1 Gb '/boot' and a 1 GB 'swap' partition, rest as free,formatted with ext 3 file system)intel 845 chipset, 512 MB Ram, Intel Celeron 2.13 Ghz Processor with windows XP on another 80 GB hard drive (dualbooting with ubuntu). Installation went fine, after restart login user name and password were asked and given. Then screen goes black nothing is seen. Please help. This is the first time i am installing a linux OS on my PC.

You can test in two ways:

1. When boot menu appears press 'e' key on the first option, then move with down arrow to line starting with 'kernel' and press 'e' key again, go to end of line with the right arrow and delete the words 'quiet' and 'splash'. Then press 'intro' and 'b' key to continue booting. This will produce verbose boot where you can see if some errors happens and probably you will get your login screen and desktop. If it happens you have to update the repository and check also in Administration-Hardware Drivers for proprietary graphics driver enabling it if exists. The change in the boot menu is temporary and you have to repeat until the problem is fixed. If you want to make the change permanent you need to edit the file menu.lst under /boot/grub.

2. You can choose from boot menu the recovery mode option, this will lead you to a menu where yo can choose something like 'terminal with network' choose it and run apt-get update and apt-get upgrade (prefix with sudo if needed). Also you can run from menu other useful options.

---

### Post by Prakash, B.S. on 2010-09-10
Thanks, found the whole thing confusing so i have deleted Ubuntu using GParted, and have now installed 10.04.1 onto a 2 GB Pendrive and another problem comes up.

---

