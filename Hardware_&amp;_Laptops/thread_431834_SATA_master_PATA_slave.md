---
title: "SATA master PATA slave"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by TheGerminator on 2007-05-03
I had an old P3 and a Seagate IDE (20GB) on which I had Debian 3.1 - perfectly running well.  I had bought a new P4 with Intel motherboard D915GLVG with a Seagate SATA.  It is running Ubuntu 6.10 and is working well.  Now, I want to connect the old Seagate IDE to copy some old data I have on that disk.  I changed the jumper setting on the IDE to "Enable Cable Select" mode and connected it.  In the BIOS I changed the setting from "enhanced" to "Legacy - SATA P0/P2 PATA", however, on reboot bios is detecting the 20GB drive but as "PATA master" instead of "PATA Slave", and ubuntu is loading normally.  I see /dev/sdb1, /dev/sdb2..etc. corresponding to the old IDE disk.  However, when I am trying to mount them using "mount -t ext2 /dev/sdb1 /mnt/newdisk1" , I get a message "/mnt/newdisk1 does not exist".
When I go to Device Manager, I find that the disk is listed under SCSI Host Interface -> SCSI Device and also displays the hard disk model number (ST320414A).  The new SATA disk is also listed here (ST380817AS).
My only objective is "copy some data from old hard disk to the new one"
I am fairly new to hardware related issues, and esp. ubuntu, though I have been using it on my desktop for the past 1 year.
Will appreciate if I get some help.

Thanks.
TheGerminator

---

