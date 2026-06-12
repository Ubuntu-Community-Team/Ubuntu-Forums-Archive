---
title: "Formating a drive?"
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by Ben Storm on 2004-12-09
I want to format a drive to a sutable format(?) ive been messing with fdisk and i no long know what the fs type is :)
Basicaly i want to have this as a second drive mounted and formated in ubuntu to store files on
Sorry if im not very clear thanks in advance :)

---

### Post by randy on 2004-12-09
mke2fs -j device will create an ext3 filesystem on the specified partition.  You can also use mkfs to create several different filesystems but if your only going to be running Linux on this box ext3 is probably your best bet.

---

