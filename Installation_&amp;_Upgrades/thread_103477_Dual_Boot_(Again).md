---
title: "Dual Boot (Again)"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by dyrer on 2005-12-14
Hello, my boot disk has these partitions
/dev/sdb1 
/dev/sdb2/ 
/dev/sdb5 
and am installing Ubuntu to hda where should I install MBR (GRUB)

---

### Post by M_Cheevy on 2005-12-14
Dryer,

Couple of things.. one, it looks like you don't have an "hda" as your drives are "sd"s... sata I assume?  Secondly, it looks like you might not have them set up 100% as they're showing as slaves... "b" not "a".. but most of that is pedantic... with the partitions you've shown, since you have no other boot manager installed, put it on /dev/sdb

---

### Post by dyrer on 2005-12-14
Perhaps I should metioned that I have three hard disks
hda
sda and sdb
hda with no partition my old 200 GB hda
sda with /dev/sda1 and /sda5 (one partition FAT32)
and sdb with two partitions 
sdb1, sdb2 and sdb5

---

### Post by dyrer on 2005-12-16
Anyone please

---

### Post by alamba on 2005-12-16
sdb i think. but get a confirmation from google/another post.

Akshay

---

