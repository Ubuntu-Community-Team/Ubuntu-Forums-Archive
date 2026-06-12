---
title: "how do i find out my hard drive mount points?"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by Hawk__0 on 2007-09-12
I just want to know, how, from the command line, do i accomplish the task of finding out where my drives are mounted? i understand they can be in things such as /mnt/hdd1 which is the drive i want to learn the GRUB mount point for.

i need to change the menu.lst file in grub, but i have no idea where that drive is mounted!

---

### Post by rybu on 2007-09-12
sudo fdisk -l

and

df -H

should tell you everything you're looking for.

---

### Post by MobiusNZ on 2007-09-13
Just be wary that grub handles partitions differently to Linux, as it gets its information directly from the bios (so I'm led to believe). The first partition on the first hard drive (as seen by the bios) is (hd0,0). The second partition on the first hdd is (hd0,1), the second drive is (hd1,0) and so on. 
Here are a couple of translations to get you going.

Linux: /dev/hda1 Grub: (hd0,0)
Linux: /dev/hdb2 Grub: (hd1,1)

---

