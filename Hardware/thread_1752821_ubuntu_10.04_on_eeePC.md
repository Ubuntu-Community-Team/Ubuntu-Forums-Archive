---
title: "ubuntu 10.04 on eeePC"
date: 2011-05-08
forum: Hardware
---

### Post by jrev on 2011-05-08
Hi, when you install ubuntu 10.04 on the second HD (sdb) of the Asus eeepc 900
the grub is installed in the mbr of the first HD (sda1) by default
How can we correct this fault after the install is done ?
Thanks

---

### Post by jrev on 2011-05-09
very simple, as usual :
1  you can start your system with the "super grub_disk2" which will detect and start your linux-system.

2  type into a console :
    sudo fdisk -l in order to see which is the root partition 

3  type < sudo grub-install /dev/sdx > where x is the root partition

4  type <sudo update-grub>  in order to eventually include the other installed systems

---

