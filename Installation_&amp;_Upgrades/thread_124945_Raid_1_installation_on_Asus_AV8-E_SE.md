---
title: "Raid 1 installation on Asus AV8-E SE"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by dlafary on 2006-02-02
I am new to ubuntu and linux as a whole. I have successfully set up the raid 1 array via the bios by doing a tab at boot and getting into the sata rom bios. However, when I start the ubuntu install and I get to the partitioning area. I see both hard drives. I am trying to install the isp setup using raid 1 mirroring. I am setting up a complete ubuntu server for file serving, email, sql, ftp, Domain server, and web server etc. I am using the "ISP server setup
-Ubuntu 5.10 "breezy Badger" from the "howtoforge.com/linux_software_raid" webpage. My question is this:
Does ubuntu 5.10 utilize the onboard raid controller or is the raid discussed on these web pages a software raid that does not use the onboard Via 8237 but uses a software applet to raid two independent sata HDD controller channels?  Right now I am requesting some assistance on making the right decision. I am at the manual partitioning screen and this is what I am seeing.

Configure Software Raid
Configure Logical Volume Manager
Guided Partitioning
Help on Partitioning

SCSI (0,0,0) (sda) - 251.0 GB ATA Maxtor 6L250S0
SCSI (0,0,0) (sdb) - 251.0 GB ATA Maxtor 6L250S0

Undo Changes to Partition
Finish Partitioning and Write Changes to Disk.


Where should I go from here?  At this point I need to make the correct decisions to install ubuntu and user directories on this raid 1 computer.

:-k

---

