---
title: "Partitioning problem"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Richardcavell on 2009-06-04
Hello all,

I have a Macbook2,1 with a 60 gig hard disk.  I previously had:

200 MB partition for EFI
27 Gig partition for OS X
27 Gig partition for Ubuntu
5 Gig linux-swap partition

I had reFit installed, and it was able to recognize my OSX and Ubuntu installations.

Now, I wanted to add another partition on the back, so I booted to a GParted live CD.  I shrank some of my partitions and added a new one on the end.  Now reFit does not recognize my Ubuntu installation.  So I cannot boot to it at all.  I initially was not able to boot into OS X either, but after a couple of reboots it seems to have found OS X and I am currently booted into that right now.

What should I do?  Obviously when I'm repartitioning I can bugger up my system completely, so I'm asking for help early rather than too late.

Here is the report from reFit's Partition Inspector:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     55713419  Mac OS X HFS+
 3       55713420     72115784  EFI System (FAT)
 4       72115785     88502084  Linux Swap
 5       88502085    117210206  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    117210239  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 55713420:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)

Partition at LBA 72115785:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap

Partition at LBA 88502085:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 5, type MS Reserved

---

### Post by Richardcavell on 2009-06-04
For the record, I solved the problem.

It turns out that there's a bug in gparted.  An easy fix is to reinstall grub.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Richard

---

