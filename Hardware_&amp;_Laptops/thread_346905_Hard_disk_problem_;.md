---
title: "Hard disk problem ;/"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by uNiverSus on 2007-01-26
Hi . I've got ubuntu since a few days. The first problem i had was to configure wifi on my pc . But finally i made it . Now i got the next problem ;/ Maybe someone can help me plz !

I've got 2 hard drives . sudo fdisk -l 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7289    58548861   83  Linux
/dev/hdb2            7290        7476     1502077+   5  Extended
/dev/hdb5            7290        7476     1502046   82  Linux swap / Solaris

As you see i got maxtor 60 and 80 GB . 
The problem is i cant mount the maxtor 80GB( /dev/sda1) , I need to copy the files from the 60 GB hard disk to the 80 . When i use this command :  sudo mount /dev/sda1 /media/maxtor80/ -t ext3 -o nls=utf8,umask=0222

i get such information from the console :
 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

can someone help me ?? i dont know how to do it and whats wrong ;/ I need to get write and read rights to the 80 GB second drive . Then i want to install ubuntu new on the first drive (60 G)

Sorry , for my very bad english . Waiting for some support ;( pls help!

---

