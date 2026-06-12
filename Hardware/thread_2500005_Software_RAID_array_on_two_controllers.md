---
title: "Software RAID array on two controllers"
date: 2024-08-18
forum: Hardware
---

### Post by jobrcogb on 2024-08-18
Hello,

I have a motherboard with two sets of four(4) SATA ports. One set of four(4) is part of the Intel Z270 Chipset. The other set is on an ASMedia chip.
I need a RAID5 array with at least five(5) HDD's out of the eight(8) SATA ports. Is it possible as a software RAID using mdadm to combine the two(2) different controllers into one RAID5 array, possibly using all eight(8) drives?

In case you need the information:
Motherboard: ASUS ROG Maximus IX Extreme
Processor: Core i7-6700K

Any questions, just ask!

TIA

Joe

---

### Post by TheFu on 2024-08-18
Yes. It is possible using mdadm.  mdadm doesn't care about drive controllers.  There are lots of possible configurations that will work, but that doesn't make some of them a good idea.  For example, I would never try to use any disks connected via USB in any RAID configuration.

However, it is likely the ASMedia controller will be slower. Mine runs at only SATA-I speeds, not SATA-II or SATA-III speeds.

Also, you'll be challenged to have the boot or OS using RAID that isn't HW-based.  What most people do is setup the OS without any RAID, then place only data onto RAID storage.  This would be my recommendations, since the OS will likely be installed on an NVMe SSD anyway with very low failure rates.

Regardless, RAID never replaces the need for backups, so you'll need backups for the data and enough of the OS to meet your recovery requirements.  Be aware that sometimes the only fix for a RAID issue is to wipe it completely and start over.  You'll need the backups for that.  

RAID solves 2 specific issues.  High-availability and, perhaps, with HW-RAID, improved performance.  That's it.  If you want anything else from RAID, best to rethink why you want it.

If you really want RAID1 for the OS, you can use LVM. Install the OS onto a single device with LVM, then post-install add a 2nd device to the VG and use lvconvert to create a RAID1 mirror.  You cannot have RAID5 or RAID10 with the OS in LVM.  You can do RAID5 or RAID10 for data controlled by LVM post-install.  As much as I love LVM, I have not been impressed by the RAID support it provides. For 20 yrs, most people would setup mdadm, then use the /dev/mdxx device(s) for LVM management.

---

