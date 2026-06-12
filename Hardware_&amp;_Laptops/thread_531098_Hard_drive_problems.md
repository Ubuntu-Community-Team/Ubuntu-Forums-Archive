---
title: "Hard drive problems"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by super.rad on 2007-08-21
I cant boot into ubuntu for some reason, it comes up saying "Error 17: Cannot mount selected partition". At the moment i am running a knoppix live dvd. I have two hard drives in my computer, one of them has a few small files on, i can access this drive from in knoppix but when i try to open the other (i want to backup some of my files) i get the message 
"Could not mount device.
The reported error was:
mount: I could not determine the filesystem type, and none was specified"
Is there anyway i can access this drive to backup my files. Thanks

---

### Post by super.rad on 2007-08-21
From knoppix i ran
```
sudo fdisk /dev/hdd1
```
and the output was
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 153175.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
Command (m for help): p

Disk /dev/hdd1: 79.0 GB, 79053133824 bytes
16 heads, 63 sectors/track, 153175 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

     Device Boot      Start         End      Blocks   Id  System
```
Not sure if this helps but thought i should add it

---

### Post by kissg1988 on 2007-08-21
Is the partition table writable? Some BIOSes have integrated protection against modifing the MBR (Master Boot Record). Check the BIOS setup, look for an option like "Boot sector access" or "Boot sector virus protection". Make sure, MBR protection is turned off, then try again to install Ubuntu.

---

### Post by super.rad on 2007-08-21
The MBR is fine as im dual-booting suse and ubuntu, suse loads fine and the MBR is on that hard drive but ubuntu worked fine last night, i turned it on this morning and it wont load. The reason im using knoppix and not suse is that i still havn't worked out how to do anything in suse as i only installed it yesterday. I'm not fussed about re-installing ubuntu yet all i want to do is be able to access the hard-drive to backup my documents

---

### Post by heimo on 2007-08-21
> **super.rad said:**
> From knoppix i ran
```
sudo fdisk /dev/hdd1
```

Why hdd1 and not hdd?

---

### Post by super.rad on 2007-08-21
because knoppix mounted my 2 hard drives as hdc1 and hdd1

---

### Post by super.rad on 2007-08-21
Ran fsck on the disk from knoppix and after correcting hundreds of errors i can now mount the drive in knoppix so im going to back up all important files then do a fresh install of ubuntu.

---

### Post by heimo on 2007-08-21
> **super.rad said:**
> because knoppix mounted my 2 hard drives as hdc1 and hdd1

Did you try it with hdc or hdd, without number one?

---

### Post by super.rad on 2007-08-21
No, just assumed that if knoppix mounted them as hdc1 and hdd1 then i should type it the same

---

