---
title: "Root partition size and file systems"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by ozone_00 on 2009-05-25
I'm fairly new to Linux and have been doing my homework before I install and came across two conflicting instructions regarding partitioning.  [**Here**]("https://help.ubuntu.com/9.04/switching/installing-partitioning.html") it says the root partition should be at least 4 gigs, but [**here**]("https://help.ubuntu.com/9.04/switching/dualboot-procedure.html") it says at least 10 gigs.  
I'm also wondering about ntfs-on-Linux and ext3-on-Windows tools, or if I'd be better off just formatting in fat32.  
I'll be dual booting with Vista, using Ubuntu as my primary use OS.  I plan on installing Ubuntu Studio, then installing Ubuntu Desktop software package if need be, or vice versa, so that I can have Studio's multimedia tools plus everydday use apps.

---

### Post by mcduck on 2009-05-25
The size simply depends on how much programs you are going to install, and if you are going to use a separate partition for your personal files or not.

4GB is enough for the base system, 10GB and you are not likely to ever run out of space on root partition. I'd go for 10GB as hard disk space is very cheap these days. And a lot more tan that if you aere not planning on using any separate partition for your personal files.

FAT and NTFS file systems are out of the question for any system partition, they don't support support file ownerships/permissions used in Linux.

Ubuntu Studio installs all normal desktop applications you'd get on normal Ubuntu desktop, it just adds a bunch of multimedia tools.

---

### Post by ozone_00 on 2009-05-25
> **mcduck said:**
> 

FAT and NTFS file systems are out of the question for any system partition, they don't support support file ownerships/permissions used in Linux.
Is fat ok for media files and personal documents stored on a seperate partition, that way I can access them from Windows if I have to?

---

### Post by mcduck on 2009-05-25
> **ozone_00 said:**
> Is fat ok for media files and personal documents stored on a seperate partition, that way I can access them from Windows if I have to?
Yes, both FAT and NTFS work fine for any additional storage partitions. Linux has no problems reading or writing to those file systems.

---

### Post by ozone_00 on 2009-05-25
> **ozone_00 said:**
> I'm fairly new to Linux and have been doing my homework before I install and came across two conflicting instructions regarding partitioning.  [**Here**]("https://help.ubuntu.com/9.04/switching/installing-partitioning.html") it says the root partition should be at least 4 gigs, but [**here**]("https://help.ubuntu.com/9.04/switching/dualboot-procedure.html") it says at least 10 gigs.  
I'm also wondering about ntfs-on-Linux and ext3-on-Windows tools, or if I'd be better off just formatting in fat32.  
I'll be dual booting with Vista, using Ubuntu as my primary use OS.  I plan on installing Ubuntu Studio, then installing Ubuntu Desktop software package if need be, or vice versa, so that I can have Studio's multimedia tools plus everydday use apps.

Also, just noticed, in one place the documentation says that the swap partition should be twice the size of your memory, in another it says 500mb.  It also says that when re-partitioned, all existing data on the disc will be lost, is that true?  I've partitioned drives before and never had this happen.

---

### Post by merlinus on 2009-05-25
If you already have vista installed and want to use part of your hard disk for ubuntu, then use vista's built-in tool for shrinking its partition first.  You also should defrag that partition before installing ubuntu.

The partitioner on the install cd will have a manual option.  Make sure not to format your vista partition, and your data will be safe.  But it may be a good idea to back up critical files anyway.  You can also create separate partitions for /home and /data, should you so desire.

As for a partition for data that can be shared and written to by both oses, both fat32 and ntfs can easily become fragmented.  This tool will enable you to read and write to linux partitions from windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by CWhitman on 2009-05-28
> **mcduck said:**
> Yes, both FAT and NTFS work fine for any additional storage partitions. Linux has no problems reading or writing to those file systems.

You should also be aware that you can install a driver in Windows that will allow you to read and write ext2 partitions from Windows. (Since ext3 is ext2 with a journal, it will also work with ext3 partitions with the caveat that journalling will not happen while you are in Windows, which could cause a few problems if you are writing files). The driver is available here:
[http://www.fs-driver.org](http://www.fs-driver.org)

edit: Already pointed out. That's what I get for not reading the whole thread first.

---

