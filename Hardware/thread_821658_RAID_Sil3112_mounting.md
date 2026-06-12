---
title: "RAID Sil3112 mounting"
date: 2008-06-07
forum: Hardware
---

### Post by bossfn on 2008-06-07
I'm sure I've done this before using linux, but haven't used it in a couple of years now and can't figure it out this round. I have 2 SATA drives connected to my sil3112 raid controller on my motherboard (it's rubbish, i know). I can't get the striped set to recognize in ubuntu 8.04.

I've followed numerous guides and each one ends with something not working quite right.

sudo fdisk -l shows this:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb517d515

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e7249f6

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7476    60050938+  83  Linux

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6e8eff9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1             327        9964    77417235   83  Linux
/dev/sdd2               1         326     2618563+  82  Linux swap / Solaris


In total there are 4 drives, but I'm only concerned with the top 2 SATA ones that are  a RAID stripe set (easily seen within Windows using drivers from my mobo driver disc -- I configured the RAID from the motherboard, it's not a windows set.)

The drives are found, but I can't mount them in anyway. I've installed dmraid and devicemapper already; however, there is not a folder called /dev/mapper/ for me to look at. Also, there is no /dev/sda or /dev/sdb or /dev/sda1 directories.


gianni@server:~$ sudo dmraid -r
/dev/sdb: sil, "sil_ahaedeabajfc", stripe, ok, 625139360 sectors, data@ 0
/dev/sda: sil, "sil_ahaedeabajfc", stripe, ok, 625139360 sectors, data@ 0
gianni@server:~$ 

Everything appears to be recognized, following guides either has me unable to browse my /dev/mapper dir or unable to properly patch the kernel (ncurses-devel missing).

Could anyone give me a hand with this please?!

*Edit* 
More output from dmraid if it helps! It doesn't seem to activate the RAID set. No clue why.

gianni@server:~$ sudo dmraid -an
RAID set "sil_ahaedeabajfc" is not active
gianni@server:~$ sudo dmraid -ay
gianni@server:~$ sudo dmraid -ay
gianni@server:~$ sudo dmraid -r
/dev/sdb: sil, "sil_ahaedeabajfc", stripe, ok, 625139360 sectors, data@ 0
/dev/sda: sil, "sil_ahaedeabajfc", stripe, ok, 625139360 sectors, data@ 0
gianni@server:~$ sudo dmraid -s
*** Set
name   : sil_ahaedeabajfc
size   : 1250278720
stride : 32
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
gianni@server:~$

---

