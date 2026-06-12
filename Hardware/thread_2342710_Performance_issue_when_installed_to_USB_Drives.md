---
title: "Performance issue when installed to USB Drives"
date: 2016-11-09
forum: Hardware
---

### Post by guy.joseph on 2016-11-09
Hi

I have just set up a HP ProLiant DL160 G6 with Ubuntu Server 16.04 LTS.

When I set up the partitions, I set up a software RAID 1 across two identical USB sticks that are installed in the machine.  I set up a 6GB swap, and 11GB ext4 for the root directory.  I really like the idea of having a redundant boot up drive.

The install took a very long time (>2 hours), and it seemed to be to do with the raid array re-syncing.  The performance that I am experiencing isn't great at all, and these drives are the only thing I can think is causing the problem.  Sadly I don't have enough hard drive bays to install an extra drive for the system.

Is there a way to improve performance on this system, ideally whilst preserving the cheap costs of the USB sticks and the redundancy of the RAID 1?

Thanks!

---

### Post by mörgæs on 2016-11-10
Hi, welcome to the fora.

A hard disk is both faster and has a longer life time than a USB stick for data storage. Your setup is an interesting proof of concept but I would prefer hard disks in the long run.

RAID 1 is made for security, not performance, which only makes the problems worse. 

Is there really no way to attach two hard disks?

---

### Post by MartyBuntu on 2016-11-11
> **mörgæs said:**
> Your setup is an interesting proof of concept but I would prefer hard disks in the long run.



Agreed.

---

### Post by sudodus on 2016-11-11
It is possible and much better to connect a hard disk drive via USB than a USB pendrive.

---

### Post by C.S.Cameron on 2016-11-11
+1, USB HDD vs USB Flashdrive

---

### Post by guy.joseph on 2016-11-15
Hi Guys

Thanks for your replies, I really appreciate it!

I have since tried booting from an old laptop hard drive which I attached using a cheap USB to SATA external connection.  Speeds increased drastically and the system was much more useable.  The twin USB stick concept was born out of trying FreeNAS, which prefers to be installed to USB sticks over a hard drive, and allows you to set it up at install in RAID 1 for redundancy.

Just another thought I had earlier.... I'm installing this onto a server which will be fitted with 4x500gb hard drives for data storage.  I want to set these up as a ZFS pool for storage, but what about creating a ~20gb partition on each drive, then creating a software RAID 1 across all 4 drives to install Ubuntu on?  Saves having an extra hard drive dangling out the back of the machine, and should mean that in the event of a single drive failure, the OS can still boot using the other three in the RAID 1.

Just wondering if anyone has any ideas about how this would affect performance.

Cheers for your help!

---

