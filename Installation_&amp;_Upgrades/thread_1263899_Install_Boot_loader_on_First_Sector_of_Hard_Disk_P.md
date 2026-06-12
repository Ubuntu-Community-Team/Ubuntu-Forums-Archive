---
title: "Install Boot loader on First Sector of Hard Disk Partition"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by anieruddha on 2009-09-11
Hi

I dont want to install the bootloader on MBR, instead of I wanna install the boot loader on first sector of hard-disk partition, can I do this with Ubuntu 9.04 and if it is possible, how? and how i boot the ubuntu after installation.

---

### Post by creiss on 2009-09-11
grub-install /dev/xxx1 for example. You need to supply you own boot partition there, tho.
But how will you boot into Ubuntu then?

-Chris.

---

### Post by imhotep59 on 2009-09-11
If you have a dual boot you can install EasyBCD in Windows and it will let you boot choose to boot Windows or Ubuntu
Follow this link
[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

---

