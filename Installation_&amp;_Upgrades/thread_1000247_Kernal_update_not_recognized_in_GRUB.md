---
title: "Kernal update not recognized in GRUB"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2008-12-02
I recently upgraded from 2.6.27-7 to 2.6.27-9 however it did not regenerate my grub boot list to show the new kernel, probably since I manually edited the entries to look neater, how can I do this manually?

---

### Post by lemming465 on 2008-12-03
*gksu gedit /boot/grub/menu.lst*, clone the -7 entry, and change the -7 to -9.  You'll have to change both the kernel and the initrd.  Double check that the kernel and initrd you specified actually exist in /boot, and you should be all set.

---

