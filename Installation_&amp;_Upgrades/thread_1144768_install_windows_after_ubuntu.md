---
title: "install windows after ubuntu"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by kevinalle on 2009-05-01
Hi
I have Ubuntu 9.04 on an ext4 partition (hd0,0).
i want to install windows xp in some free space I have after the ext4 partition.
i boot from windows cd, but when I choose the partition I want it to install into, it says something like: windows needs to write some system files to (hd0,0) but is of an unrecognized filesystem type,
and refuses to install
i saw many totorials saying this would break grub, thats ok, ill fix it. but I think it is because of ext4 filesys type that windows cannot write there.
i dont want to remove my ubuntu, and i dont want to change the places of the partitions, its just a temporary install.
can one install windows and tell it not to write any of the MBR files?
how can i install windows?
i was hoping one could install the windows in that partition right from ubuntu, like copy a windows system to that partition, but i dont know how.
if you know how i can instal windows,
thank you!

oh, and my fdisk -l is

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8511    68364576   83  Linux
/dev/sda2            8512       30401   175831393+   f  W95 Ext'd (LBA)
/dev/sda5            8512       10199    13558797   83  Linux
/dev/sda6           10200       26523   131122498+   7  HPFS/NTFS
/dev/sda7           30280       30401      979933+  82  Linux swap / Solaris
/dev/sda8           26524       30279    30170038+   b  W95 FAT32

(i want to install to sda8, was "unallocated" when i tryed, then i changed to fat)

---

### Post by diiphantom on 2009-05-01
why dont you install windows in virtualbox?

---

### Post by PC_load_letter on 2009-05-01
> **diiphantom said:**
> why dont you install windows in virtualbox?

+1. I did it on my 2GB Ram Dell laptop running Ubuntu 8.04 64bit and XP feels snappier than the XP installed originally on the same machine. The only drag is the XP desktop has 3:4 aspect ratio but my laptop has a wide screen, so there are two black stripes on both sides. But everything works!

---

### Post by kevinalle on 2009-05-01
yes, i already have a virtualbox with a windows,
but i need to make a real installation so i can use all my computers power in windows..
btw, is it possible to copy a virtualbox harddrive to a partition?
thanks

---

### Post by diiphantom on 2009-05-01
to me, if you have another hard drive do it there, if not, then just reinstall everything

a fresh start :):guitar:

---

### Post by kevinalle on 2009-05-01
noooooooo
no, no.
not possible to reinstall my ubuntu :)
i like it too much as it is..
isnt it possible to install windows without the #&% MBR??
i have a winXP liveCD, can i copy it to the partition? how?

---

