---
title: "Real Problem: How to create a boot cd for a Wubi installation"
date: 2008-11-08
forum: General Help
---

### Post by uncaspi on 2008-11-08
I just want a boot cd which only boot Ubuntu. No Grub. I seems quite impossible to figure out how to do it for a Wubi installation. There is no root=/dev/hda1 i.e. I have looked everywhere on the net but I can't find any solution which work. I've just tried everything. On an other PC I have also Ubuntu on an external HD /dev/sdc2 and here I created the boot cd using isolinux with only one line in isolinux.cfg. This line:
DEFAULT linux initrd=initrd.img ro  root=UUID=cc1d5bd5-039d-4351-9ad0-51b705cdf1b5 ro quiet splash

and it booted directly without any problems. The UUID I found in the menu.lst file in /boot/grub but the same short line except another UUID doesn't work for Wubi.

It seems for the Wubi PC that it couldn't find the root directory. Probably I must use the APPEND statement containing i,e  file= ..something eventually boot=..something

The Ubuntu is located in C drive in the default ubuntu folder. There is only one HD and one partition on the PC.

Any hints?

---

