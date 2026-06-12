---
title: "Dual System"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by dragooon478 on 2009-08-28
When i am installing the ubuntu 9.04 i get this message
> 

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #6 of SCSI1 (0,0,0) (sda) as swapthe computer is a vista computer, i am wondering if continue will it delete / corrupt vista or will it let me chose from the two OS on start up.

---

### Post by Partyboi2 on 2009-08-29
Hi, that message is telling you that its going to create 2 partitions sda5 and sda6 which for Ubuntu, continuing should setup a dual boot setup, unless you have vista on one of those partitions. (its more likely to be on sda1 or sda2) you can check by opening a terminal (Applications>Accessories>Terminal)from the Desktop of the live cd and typing
```
sudo fdisk -l
``` this will list your current partitions and show the vista partition as ntfs.

---

