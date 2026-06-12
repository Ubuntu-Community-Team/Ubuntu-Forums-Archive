---
title: "Hardware RAID 5 Setup"
date: 2009-02-13
forum: Hardware
---

### Post by bigrig454 on 2009-02-13
I am very new to Ubuntu and am having some troubles seeing my RAID 5 array.
I have 3 320gb Seagate drives on an Adaptec 2610sa RAID controller. I setup the array in the Adaptec BIOS. The problem I am having is that I have no idea how to see the array in Ubuntu. I do know I can see a SCSI drive in the Computer "window" that was not there before, but this drive can not be mounted. Any help would greatly appreciated.

---

### Post by martalli on 2009-02-14
I am not certain of your next step, but have you tried looking at the drive in gparted or qtparted?  Maybe the drive still needs to have a partition table made and formatted.

I have a related question, though.  Using hardware raid, how can you monitor the health of the array?  How do you know when a drive has failed?

---

### Post by cocoa117 on 2009-02-14
> **martalli said:**
> I am not certain of your next step, but have you tried looking at the drive in gparted or qtparted?  Maybe the drive still needs to have a partition table made and formatted.

I have a related question, though.  Using hardware raid, how can you monitor the health of the array?  How do you know when a drive has failed?

You will need monitoring software from the card menufacture which works under Linux or from third party monitoring tool that support this card, otherwise, you can't.

---

### Post by bigrig454 on 2009-02-14
> **martalli said:**
> I am not certain of your next step, but have you tried looking at the drive in gparted or qtparted?  Maybe the drive still needs to have a partition table made and formatted.

I have a related question, though.  Using hardware raid, how can you monitor the health of the array?  How do you know when a drive has failed?

You were right I downloaded gparted, created a disk label and partitioned the drive and now all is working well. As for monitoring the array, there are two ways, in the BIOS setup or Adaptec has software to monitor and manage the array in Ubuntu and other operating systems.

Thanks for the advice, it was much needed for this Ubuntu newbie.

---

