---
title: "partition appearing twice"
date: 2008-08-03
forum: General Help
---

### Post by mordecai83 on 2008-08-03
Hello,

I'm  new to Ubuntu and i love it. I've had to search a lot to get all things working the way i like it, but all worked out well and now i hardly use vista any more.  Now I came across this problem, well not really a problem, more of a nuisance. But i cant seem to fix it or find any information about it.

I've got one drive with 4 partitions yet Ubuntu sees 5, one of the partitions is an exact duplicate of another one. How can i get rid of this? 

BTW I'm using Hardy
Any help would be appreciated

---

### Post by Elfy on 2008-08-03
Can you open a terminal, run these commands and post the outputs here please.

```
sudo fdisk -l
cat /etc/fstab
```

Which partition does it see twice - and where is it showing them?

---

### Post by Keith Hedger on 2008-08-03
I sometimes have this problem with a large external daisy chained firewire disk a reboot usually solves the problem

---

### Post by mordecai83 on 2008-08-03
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              17        1322    10485760    7  HPFS/NTFS
/dev/sda3   *        1322       35711   276230469    7  HPFS/NTFS
/dev/sda4           35712       38914    25721218    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           35712       38462    22097376   83  Linux
/dev/sda7           38463       38586      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dba7bee0-5f7b-4aae-9156-6a9eb6b2dea7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=78a265ea-50b3-47a1-9845-923638f1fa3c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

the one that says system "unknown" is  a duplicate of the first and as to the question where it is showing: under places, the partition appears twice, when i open "computer" it does so too.  Weird thing is that it wasnt like this from the beginning, it just appeared one day. I dualboot with vista and vista sees only one of them. thanks for the fast reply!

---

### Post by cdtech on 2008-08-03
I wonder what "gparted" shows, from the live CD. That's interesting........

---

### Post by Elfy on 2008-08-03
They both seem to be inside the extended, I'd quite like a look at a gparted screenshot as well. You could install it in your system and run it

```
sudo apt-get install gparted
gksudo gparted
```

---

### Post by mordecai83 on 2008-08-03
hello again,

when i run gparted it says: "cant't have overlapping partitions" and it shows the whole disk as unallocated space. Disk information in vista shows all the partitions that i posted earlier exept the duplicate. Only ubuntu sees that. It occurred to me that maybe i made a mistake partitioning but everything works fine tho. And the duplicate wasnt there before, it just appeared yesterday. Everything works so it isnt really a problem, its just annoying as hell.
I appreciate the help tho

---

### Post by Elfy on 2008-08-03
Well that's a bit on the peculiar side - how did it get made in the first place I wonder.

It's also a bit on the odd side that you have 2 boot flags, logically it would seem to me that the 2 partitions got created at the same time as buntu made the extended to install in

   Device Boot      Start         End      Blocks   Id  System

/dev/sda2              17        1322    10485760    7  HPFS/NTFS
/dev/sda3   *        1322       35711   276230469    7  HPFS/NTFS
/dev/sda4           35712       38914    25721218    f  W95 Ext'd (LBA)
/dev/sda6           35712       38462    22097376   83  Linux
/dev/sda7           38463       38586      995998+  82  Linux swap /Solaris
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)


Bit beyond me at the moment - I would certainly make sure I had good backups just in case you get problems, what do you have on the sda1 partition - or is it the vista restore partition?

---

