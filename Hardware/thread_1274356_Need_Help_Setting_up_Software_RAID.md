---
title: "Need Help Setting up Software RAID"
date: 2009-09-24
forum: Hardware
---

### Post by Merkidemis on 2009-09-24
I am running Ubuntu Server 9.04 64bit.  This is an existing install.

My motherboard is a  Asus M3N78-VM with an nVidia SATA RAID controller.

I have three 1TB Seagate drives I want to add to the system in a RAID5 array, but am having problems.

I set the three drives up in the BIOS to be part of a RAID 5 array, then went into Linux where they show up as seperate disks.  This of course is expected with a FakeRAID software controller.

When I run the command:

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdc/ /dev/sdd /dev/sde 

I get a message saying /dev/md0 does not exist and is not a 'standard' name, so the array cannot be created.  I checked, and I indeed do not have a /dev/md0.

Clearly I've missed something.  What do I need to do to get this working?  Do I need driver modules? Do I need to run some other command/s before mdadm?  Any assistance would be greatly appreciated, as I've already spent hours trying to get this working.

---

### Post by u-slayer on 2010-05-25
Change md0 to /dev/mapper/md0.

That's what worked for me.

---

