---
title: "[SOLVED] not a good start"
date: 2008-08-10
forum: General Help
---

### Post by Thora3967 on 2008-08-10
I started to install ubuntu 64bit, and it hung almost immediately, while loading the partitioner.  It displays the following message:

> "Warning!  Device /dev/sda has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

So I'm currently d/l'ing the 32-bit I86 version and will try to run that without problems.

---

### Post by TenPlus1 on 2008-08-10
Typically if you have 3gb memory or less, I'd install the 32-bit Ubuntu on your system to save hassle later...  64-bit is good, and fast for processor intentive apps, but for day-to-day usage it's better with 32-bit and everything works fine (flash,java,codecs etc)...

---

### Post by Thora3967 on 2008-08-10
That was my first thought and that was my next attempt, without success.  Got the same error and hang. :(

---

### Post by Mgiacchetti on 2008-08-10
u got a usb drive present?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/147548](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/147548)

---

### Post by Vivaldi Gloria on 2008-08-10
Remove that filesytem and create a new filesystem gparted has no problems with. I mean format it completely. Then install.

---

### Post by Thora3967 on 2008-08-10
[QUOTE=Mgiacchetti]u got a usb drive present?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/147548](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/147548)[/QUOTE]

No, my drives are all SATA.

[quote="Vivaldi Gloria"]
Remove that filesytem and create a new filesystem gparted has no problems with. I mean format it completely. Then install.[/quote]

The drive in question was formatted NTFS, used, then the files were erased.  Should I re-format in windows, as NTFS? or format it 
via FAT16 and let linux re-format to NTFS?

---

### Post by koenn on 2008-08-10
why would you want to use NTFS ? 
and are you trying to install linux on that NTFS partition ?

---

### Post by Thora3967 on 2008-08-10
I was originally using that drive on windows xp, and had assumed linux would see it and re-format it.  How else can I format it now manually so that linux can use it?

EDIT:  I've since dug up an older copy of partition magic.  Used it to format the drive to /ext3 (with suggested partitioning from another thread).  Same error & hang with both 32- and 64-bit versions of Ubuntu.

I downloaded and burned a disk of OpenSUSE and it is currently installing without difficulty.

I guess that's bubye for Ubuntu

---

