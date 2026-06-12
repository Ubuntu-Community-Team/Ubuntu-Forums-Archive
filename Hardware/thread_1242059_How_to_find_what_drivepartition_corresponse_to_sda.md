---
title: "How to find what drive/partition corresponse to sda1"
date: 2009-08-16
forum: Hardware
---

### Post by B-Ry on 2009-08-16
I know which OS installation corresponds to sda1, sda2, sdb1, sdb2, etc, but how do I find out whether sda1 is hd0,0, or hd1,0, etc?

---

### Post by dabl on 2009-08-16
The useful commands are ```
sudo blkid
``` and ```
sudo fdisk -lu

```

As far as numbering, /dev/sda is always (hd0), and /dev/sdb is always (hd1).  But for partition numbering under Grub2, there's news -- you need to review that if you're contemplating Karmic Koala.

:)

---

### Post by louieb on 2009-08-16
Roughly sda ... sdx is based on where the drive is plugged in ide channel # master or slave. SATA port #.  And will change if a drive gets moved to a differet plug.

While (hd0) .. (hd#) is based on what BIOS reports to be the boot order.  And can change by changing the boot order in BIOS or by useing the boot device menu found on most computers built in the last 6-7 years. 

Because both of those can chage Ubuntu since Edgy (v6.10) uses UUID to tell one partition from another.  

You can use the geomentry command from the **GRUB>**  prompt and get a pretty good idea of whch drive is which. example.
```

grub> geometry (hd0)
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83


```

---

