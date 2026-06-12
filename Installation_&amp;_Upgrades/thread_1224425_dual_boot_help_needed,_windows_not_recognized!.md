---
title: "dual boot help needed, windows not recognized!"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by sneza on 2009-07-27
Hi!
I tried finding some similar topic but I couldnt. 
so here it goes:
I installed windows on my old desktop, and then i installed ubuntu 7.10 from a cd.
i had installed windows on the D partition of my HD.
After I installed ubuntu I couldnt find my windows in the grub menu.
I changed menu.lst  to include windows as follows:

title Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1

I did this since my windows is on /dev/sda5

now when I tried going to windows it gives me error 12 invalid request or sth.
So I can only log on to ubuntu, and since I am using ADSL internet I can not set it up properly there :(
I am trying to set the computer working for my parents, but I guess formating everything was a bad idea :)

I am a beginner on ubuntu myself, so any help would be great!

---

### Post by merlinus on 2009-07-27
Open a terminal windows, and post results of:

```
sudo fdisk -l
```

It seems that xp is in a logical partition, however, and it is very difficult to run it from there.

---

### Post by sneza on 2009-07-28
sorry for my late reply. the output of the command sudo fdisk -l is the following:

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/tracks, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab5eab5e

Device Boot   Start    End    Blocks    Id  System
/dev/sda2  *     1    4998   40146403+   f  W95 Ext'd (LBA)
/dev/sda5     3649    4998   10843843+   7  HPFS/NTFS
/dev/sda6        1      36     289075+  82  Linux swap / Solaris
/dev/sda7       37    1252    9767488+  83  Linux
/dev/sda8     1253    3648   19245838+   b  W95 FAT32

Partition table entries are not in disk order

```

---

### Post by merlinus on 2009-07-28
As I suspected, windows is installed in a logical partition.  You can google for workarounds, but all are tricky.  It wants to be in a primary partition.

You can try to use gparted to move and/or resize partitions to make this so, beginning with reducing the size of sda1 (the extended partition) to make room for a primary, but it may be best to start afresh, if you can back up important data..

---

