---
title: "General question about linux boot"
date: 2008-07-20
forum: General Help
---

### Post by oconnor663 on 2008-07-20
The '/etc/fstab' file is stored my root partition. It contains instructions for mounting my root partition. How does the Linux kernel know where to find this file before the filesystem is mounted?

I'm specifically asking this so I can better understand what's going on when Linux uses loop-aes to encrypt the root partition. Thanks for your help.

---

### Post by mcduck on 2008-07-20
The information is in Grub's configuration file, /boot/grub/menu.lst. And the location of that file is stored in the first stage of Grub, located on your disks MBR.

---

