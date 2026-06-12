---
title: "gparted won't allow assignment of linux-raid drive"
date: 2017-07-16
forum: Hardware
---

### Post by dan400man2 on 2017-07-16
I'm a Linux noob.  I have a tower that has Windows 10 installed, and I running Ubuntu 16.04.2 LTS via Live USB boot.

I am attempting to use a single drive pulled from a WD My Book Live Duo NAS storage device, and attached internally in a the aforementioned tower, the reasons for which I explain below (so as to avoid TL;DR).  WD (non-)support said that Windows would probably not recognize the drive and  suggested I try a Linux system to read the drive, since My Book Live Duo  uses a Linux OS under the covers.  Gparted shows the drive and the partitions, but I am unable to access the drive's contents via the Files app.  Gparted shows the particular partition as:

   [FONT=courier new]Partition  Name        File System   Size           Used  Unused  Flags
[/FONT]
[FONT=courier new]/dev/sdb4  primary     linux-raid  2.72 TiB      ---     ---  raid[/FONT]


When I right-click on this, the only options available are Delete, Format to, Name Partition, Manage Flags, and Information.  FWIW, Windows' Disk Management gives me the same type of limitations, and I am unable to assign a drive letter to the partition.  I tried unchecking "raid" in the Manage Flags dialog, but that had no effect.  Can anyone advise on how to get Ubuntu to recognize this drive and let me read files from it?

_**The TL;DR details behind my request:**_
I have a WD My Book Live Duo NAS storage, and the two 3TB drives are configured in a RAID 1 mirror.  The unit's diagnostics report everything is rosy, but the unit "fails" after a certain period of time and requires the unit to be rebooted.  The failure is that the drive share becomes unavailable, and Windows will report that the drive is not communicating.  However, when I navigate to the unit's user interface through the browser, I have all of the tools available, and it is here where diagnostics will report that nothing is wrong.  This is also where I issue the reboot request.  The problem is becoming more frequent, and I have been trying to offload all of the data from the unit to another drive, but it has been an exercise in frustration.  I don't know whether the enclosure or the disk drives are failing.

---

