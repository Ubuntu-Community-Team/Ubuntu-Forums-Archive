---
title: "[SOLVED] how can i find which (hdN,M) represents my drive?"
date: 2008-11-16
forum: General Help
---

### Post by chriskin on 2008-11-16
i want to add an (hd0,something) to my boot menu but i do not know how to recognise the name of the drives in (hd-,-).

---

### Post by Kevbert on 2008-11-16
In terminal:
```
sudo fdisk -l
```
The last part of the hard disk under the device column will give you the name
eg /dev/sda2
gives sda2 (numbered from 1, 2nd partition of first drive)
The hard disks are numbered from 0 in the grub menu so hda (0,1) is the first hard disk(0) and the second partition(1). So in the example above for sda2, its hard drive 0 partition 1.

---

### Post by chriskin on 2008-11-16
yep :) i found it 
thanks anyway :)

---

