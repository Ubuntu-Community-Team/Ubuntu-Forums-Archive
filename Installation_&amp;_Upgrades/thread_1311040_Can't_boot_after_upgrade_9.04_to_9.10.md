---
title: "Can't boot after upgrade 9.04 to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by frank4360 on 2009-11-02
After upgrade from 9.04 to 9.10 my PackardBell EasyNote laptop (AMD Turion 64x2) will not boot except in Recovery mode.

Normal powering up simply loops round the Bios display and Grub.

Booting from Recovery mode leaves me at a Linux login - I have to login and execute "startx" to get the Desktop.

When closing I have to execute "shutdown".

---

### Post by frank4360 on 2009-11-02
I have found a workround for the boot hangup - I have edited the /boot/grub/menu.lst file and removed "splash" from the default boot line.

The entry was:-

title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=d268c13e-75b3-4ab0-81cc-11feb01f2beb ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

it is now:-

title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=d268c13e-75b3-4ab0-81cc-11feb01f2beb ro quiet
initrd /boot/initrd.img-2.6.31-14-generic
quiet

The boot now works - but I don't know what effect, if any, the "splash" parameter had!!!

---

