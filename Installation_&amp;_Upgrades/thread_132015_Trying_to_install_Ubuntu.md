---
title: "Trying to install Ubuntu"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2006-02-17
In the following install procedure I use partition magic from winXP to make
all the partitions. I know this is not advisable and I should just use the
partitioning program from the Ubuntu install CD, but a friend of mine have
made it work flawless this way so I would like to make it work too.

On a clean 80GB (76GB) disk I install winXP. When I am finished I use
partition magic to resize the partition to 66GB

Then I make the following 3 partitions in the following order:

1) Ext3 Primary with size 9 GB
2) Ext3 Logical with size 2 GB
3) swap with size 500 MB

I then set 1) to "active" which results in my windows partition having
status "hidden".

I then boot from the Ubuntu install CD where I choose to configure the
partitioning table myself:

I set 1) to "boot", 2) to "root" save the changes and continue the
installation and when asked if I would like to add winXP to GRUB I choose
yes.


When done I open a shell and type:

sudo fdisk -l and get:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hda1   *           1        8804    66558208+  17 Hidden HPFS/NTFS
/dev/hda2            9050       10337     9737249    f W95 Ext'd (LBA)
/dev/hda3            8805        9049     1852168+  83 Linux
/dev/hda5            9050       10269     9223168+  83 Linux
/dev/hda6           10270       10337      514048+  82 Linux swap / Solaris
Partition table entries are not in disk order 

Guess the last line is not good. My friend gets this when he types fdisk -l:

Disk /dev/hda: 56.7 GB, 56746501120 bytes
240 heads, 63 sectors/track, 7330 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5901    44611528+   7  HPFS/NTFS
/dev/hda2   *        5902        5919      136080   83  Linux
/dev/hda3            5920        7330    10667129    f  W95 Ext'd (LBA)
/dev/hda5            5920        7191     9616288+  83  Linux
/dev/hda6            7192        7330     1050808+  82  Linux swap / Solaris

Why the difference when or config is the same besides that my disk is 20 GB
larger...

When I try to boot winXP I just get a blue screen and an error which is gone
before I can read it, then the system reboots.


I am almost sure I do the same thing he does but still I cannot use winXP
and my fdisk looks different.

any ideas?

JOhs

---

### Post by TimeGoneBomb on 2006-02-17
Wow that sucks. Dude I feel for ya, it sounds like the partition probably got corrupted somehow.  I know its like a 1 in a billion chance that partion magic could do that, but I use pmagic too and I remember it corrupted my drive once. 

To find out, try booting linux and use it to take a look at the ntfs partition. Are all of your files there like they should be? Another thing you could use is chkdisk. Or try booting into safe mode. If you can boot into safe mode, I guess that your partion is fine. Have you tried that?

---

### Post by bigblop on 2006-02-17
There is nothing of importance on either disk so I am already in the process of formating the whole drive....but what was I doing wrong the described procedure?

---

