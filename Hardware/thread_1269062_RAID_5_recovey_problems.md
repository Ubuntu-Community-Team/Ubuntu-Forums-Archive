---
title: "RAID 5 recovey problems"
date: 2009-09-17
forum: Hardware
---

### Post by Akuma Daimao on 2009-09-17
Good morning,

I'm running Ubuntu 8.10 on a 40GB IDE hdd.  Also installed on the system is a 3-disk (3x250GB SATA) software RAID 5.  I used mdadm to construct the RAID.

I recently suffered a hard disk failure; one of the RAID drives quit on me.  I installed the new drive and booted up and am now having the following problems:

1) The drive designations have changed.  Whereas the OS HDD (the IDE drive) was formerly /dev/sda, it is now /dev/sdd.  The three raid drives have changed from /dev/sdb - /dev/sdd to /dev/sda - /dev/sdc.

2) I can't do anything with the RAID.  mdadm --assemble runs though the drives, tells me that they're busy, and then says "No arrays found in config file or automatically."  

I don't know much about this, unfortunately; I've run through some of the suggestion threads but the commands they give don't seem to be working.  

Where do I go from here?  Any help would be much appreciated.

---

