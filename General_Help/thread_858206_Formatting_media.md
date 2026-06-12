---
title: "Formatting media"
date: 2008-07-13
forum: General Help
---

### Post by Uchiha_madara on 2008-07-13
how can I formate My Flash Disk or NTFS,FAT32 Drive??

By using terminal, or anther  Application

---

### Post by PmDematagoda on 2008-07-13
The easiest way would be to use Gparted which can be installed with:-
```
sudo apt-get install gparted
```

---

### Post by VMC on 2008-07-13
> **Uchiha_madara said:**
> how can I formate My Flash Disk or NTFS,FAT32 Drive??

By using terminal, or anther  Application

Try gparted, if you have it installed. Also something along this line:
"sudo fdisk /dev/sdb", try man fdisk.
From Terminal type:

```
sudo fdisk -l
```
to locate your usb flash.

---

