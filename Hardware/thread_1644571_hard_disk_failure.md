---
title: "hard disk failure"
date: 2010-12-13
forum: Hardware
---

### Post by vchapman on 2010-12-13
My hard drive has become corrupted. When I run the live cd and do this

ubuntu@ubuntu:~$ dmesg | tail
[  435.056030] ata3: soft resetting link
[  440.252070] ata3: link is slow to respond, please be patient (ready=0)
[  445.068051] ata3: SRST failed (errno=-16)
[  445.068070] ata3: soft resetting link
[  453.188502] ata3.00: configured for UDMA/133
[  453.188548] ata3: EH complete
[  793.745240] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 0 failed (32105!=0)
[  793.745259] EXT4-fs (sda1): group descriptors corrupted!
[  989.906143] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 0 failed (32105!=0)
[  989.906162] EXT4-fs (sda1): group descriptors corrupted!
ubuntu@ubuntu:~$ 

I get a lot of stuff that I don't understand. 

When I go to places and select the file system I get a message that says, among other things, bad super block on /dev/sda1

Is there a way to repair this myself or do I go to my local computer store and get them to install a new hard drive. What are the chances of getting any data off the broken one?

---

### Post by dabl on 2010-12-13
You didn't say anything about the type of computer or hard drive, so the following assumes a generic desktop or laptop.

Unless there are other warranty considerations, or you are hopelessly dangerous with a phillips head screwdriver, I don't know why you would pay a shop to replace a hard disk drive.  Of course, if you want them to install and configure the OS for you, then perhaps that would justify it.  You can order a suitable replacement hard drive online, remove the computer case (2 or 4 screws), remove the old hard drive (2 cables at most, 4 screws at most), and install the new one in the same manner.

There are professional data recovery organizations, if there is important data on your dead drive, for example [http://www.ontrackdatarecovery.com/](http://www.ontrackdatarecovery.com/)

(no endorsement here ... just pointing to one such organization)

---

### Post by vchapman on 2010-12-13
> **dabl said:**
> You didn't say anything about the type of computer or hard drive, so the following assumes a generic desktop or laptop.

Unless there are other warranty considerations, or you are hopelessly dangerous with a phillips head screwdriver, I don't know why you would pay a shop to replace a hard disk drive.  Of course, if you want them to install and configure the OS for you, then perhaps that would justify it.  You can order a suitable replacement hard drive online, remove the computer case (2 or 4 screws), remove the old hard drive (2 cables at most, 4 screws at most), and install the new one in the same manner.

There are professional data recovery organizations, if there is important data on your dead drive, for example [http://www.ontrackdatarecovery.com/](http://www.ontrackdatarecovery.com/)

(no endorsement here ... just pointing to one such organization)
You are right. I am going to pull the hard drive and go and get a replacement. I will probably get some more memory while I am at it. I can install the latest Ubuntu 10.04 or 10.10. I will ask the computer shop if they can recover the data. If they can't its no big deal.

---

### Post by dabl on 2010-12-13
Just pay attention to the data interface.  If it's an old IDE, you'll have a little more challenge to find a new drive, but they all fit the same.  If it's SATA, there are two styles of power connectors -- older has the power cable and data cable separate, and newer has a combo connector.

---

### Post by vchapman on 2010-12-13
> **dabl said:**
> Just pay attention to the data interface.  If it's an old IDE, you'll have a little more challenge to find a new drive, but they all fit the same.  If it's SATA, there are two styles of power connectors -- older has the power cable and data cable separate, and newer has a combo connector.
The old one was a SATA with separate power and data connectors. The machine is back up and running with Ubuntu 10.04 installed.

As an aside, I bought another 2 gb of memory. So the total should be 3. Except the system is only recognizing 2. So I guess the BIOS only supports 2 gb.

---

