---
title: "Highpoint Raid walk through"
date: 2010-10-06
forum: Hardware
---

### Post by kernelmustard on 2010-10-06
With much help from lukeiamyourfather and highpoints documentation I was  able to get my Highpoint RAID card drivers compiled (231x) and can load  the module.  Once I reboot the machine the system hangs.  I am trying  to migrate from Windows 2008 R2 with a 5TB ESATA array (NTFS) to  Ubuntu.   Once the driver is loaded I can see all of the disk running  fdisk -l but still fail to get the raid utility to run.

Attached are the dmesg, lsmod and related log files.  Currently I am running 10.04 x64 off a Live CD (RAID 1 SATA drives are ext4 formatted w/o any live data).

I tried following the steps at [http://debianclusters.org/index.php/HighPoint_RocketRAID:_Installation](http://debianclusters.org/index.php/HighPoint_RocketRAID:_Installation)  but still couldn't get RAID sorted.   If anyone has used the 231x  adapter and had luck would love to know the steps taken and would write  up the documentation so someone new to linux and migrating from Windows  to Ubuntu with an existing array could follow.

---

### Post by SBFree on 2010-11-13
I just got my 2310 delivered and intend to build a file server with it. Have you had success in installing this with Ubuntu?
Scott

---

