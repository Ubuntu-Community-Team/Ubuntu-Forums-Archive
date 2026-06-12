---
title: "grub bootload problem after vista install"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by kditty on 2009-01-06
i had a dual boot, tiny vista-ubuntu 8.10 needless to say vista messed up, so i installed vista again on partition C: after that, i have no chance of booting into unbuntu because the mbr must have been written over. 

how would i go about fixing this so that i can get to my ubuntu install? i need help badly since i have no clue about grub bootloader and would hate to mess my whole system up trying to get it installed.

---

### Post by Pumalite on 2009-01-06
Boot your Live CD and post:
```
sudo fdisk -lu
```

---

### Post by kditty on 2009-01-06
> **Pumalite said:**
> Boot your Live CD and post:
```
sudo fdisk -lu
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b017dae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   254935484   127467711    7  HPFS/NTFS
/dev/sda2       254935485   488392064   116728290    5  Extended
/dev/sda5       254935548   478817324   111940888+  83  Linux
/dev/sda6       478817388   488392064     4787338+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeaa3ab4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   781417664   390708801    c  W95 FAT32 (LBA)

---

### Post by Pumalite on 2009-01-06
Mount sda5
```
sudomkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
```

Post menu.lst:
```
cat /media/sda5/boot/grub/menu.lst
```

---

