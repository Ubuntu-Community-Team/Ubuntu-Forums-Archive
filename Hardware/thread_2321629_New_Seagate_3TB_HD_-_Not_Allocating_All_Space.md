---
title: "New Seagate 3TB HD - Not Allocating All Space"
date: 2016-04-23
forum: Hardware
---

### Post by scott129 on 2016-04-23
Good afternoon.  I've recently received a new Seagate 3TB drive that I wanted to use on my windows box.  I tried the device manager but it was not allocating all the drive space, only 2TB of it.  The other 700mb+ is labeled as non-partition.  So I decided to use my Ubuntu box to format the drive.  Using fdisk I was able to format the drive but when I opened up Gparted, again it shows 2TB and 700mb+ non-partition.  When I try  to extend the partition I get an error.  Is there any way to format the drive to use all the space in one partition ??  Tks

---

### Post by ajgreeny on 2016-04-23
Are you using an old BIOS machine and msdos partition-table which will only see disks up to 2TB?

To see all of a 3TB disk you will have to format using GPT partition-table and partitions.

---

### Post by TheFu on 2016-04-23
Welcome to the forums.

Don't use fdisk (or any variant of it (sfdisk/cfdisk). While it can handle the job, it is a hassle to get things aligned correctly. There are tools which handle the alignment issue automatically, so your new disk isn't 20% slower than it should be just due to a bad alignment choice.

Use either **parted** or **gparted**.

The disk needs to be using the "GPT" partition table type, not MSDOS (also called MBR).  There are many great things about GPT and Linux has been fully compatible with it for years.  Windows has an issue with GPT on boot disks (requires UEFI boot and x64). For data disks, Windows since Vista doesn't mind GPT.

So you'll need to delete all the partitions, then write a fresh partition table entry ...  There is a menu option in gparted for this.  After that, you can create partitions as needed.  No more Extended/Logical required.  There are many upgrades for GPT disks - one is 100+ primary partition support. There are many others.

I'd also add a warning about using gdisk.  In the past, those utilities could screw up disks that weren't GPT partitioned making the data unavailable.  Don't know if that is still true or not, but I wouldn't risk it.  gparted is so much easier anyway.  It was bad enough that people wrote other utilities to fix the issues caused by gdisk.

Learn more about GPT - [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by oldfred on 2016-04-23
gdisk is the fdisk for gpt partitioned drives.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

And there is a new version of fdisk in 16.04 that does now recognize gpt drives. I have only used gparted to partition drives, but use gdisk to review and repair them (rarely needed).

Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning before doing anything else.

You may be able to convert from MBR to gpt, but not sure with large drive if it works correctly.
Best to start over.
      
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Even if not currently planning on booting from drive, I suggest both an ESP for UEFI boot and a bios_grub for BIOS boot. Nether take much space on new drives and then later allow you to install an operating system on drive. ESP is supposed to be near beginning of drive and can be then difficult to add if drive has lots of data.

       
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

