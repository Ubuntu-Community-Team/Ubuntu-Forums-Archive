---
title: "Making Sure my hard drive dosen't die..."
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by transkinetic on 2007-12-04
I attempted to wipe my hard drive to do a fresh install of gutsy and got a message saying that either my hard drive was dead or my install cd was bad. I rebooted and selected the check cd option. It reported that the cd had no defects whatsoever. I tried the istall a couple more times, getting the same error message on each attempt. After stewing on it for a few minutes, I tried taking out the hard drive and staring at it, sacrificing a chicken and putting it back in the computer. I then rebooted and selected oem install for no paricular reason. The system installed without complaint. I realize that I should invest in a new hard drive soon but I'm too broke at the moment. Is there a way that I can scan my new installation for corruptions every time I reboot the system?

---

### Post by tgalati4 on 2007-12-04
Do this only once:

>sudo fsck -cc /dev/hda1  (or sda1 whatever your boot drive is called)

This will check for bad blocks.  It may take a while.  If it passes then you should be OK for a while.  Then install SMART monitoring tools:

>sudo apt-get install smartmontools

>man smartd

>man smartctrl

---

### Post by transkinetic on 2007-12-04
I'm going to reboot and install the softwar you recommended
thanks,
-travis
oem@spacerig:~$ sudo fsck -cc /dev/sda1
[sudo] password for oem:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
Clearing orphaned inode 5193909 (uid=0, gid=0, mode=0100644, size=1309)
/dev/sda1 is mounted; it's not safe to run badblocks!
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(10297412--10297413) +10297420 +10297434 +10316751
Fix<y>? yes

Free blocks count wrong for group #314 (16511, counted=16506).
Fix<y>? yes

Free blocks count wrong (13538041, counted=13538036).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: ***** REBOOT LINUX *****
/dev/sda1: 101537/7143424 files (0.2% non-contiguous), 747757/14285793 blocks
oem@spacerig:~$

---

### Post by transkinetic on 2007-12-04
I installed smartmontools aswell as smart-notifier...

I unsure how to effectively use smartmontools. Having smartd check sda1 every 30 minutes sounds like a good plan. The best I've been able to do looks like the following...

```
spacepopeye@spacerig:~$ sudo smartd -d -i 30
[sudo] password for spacepopeye:
smartd version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Opened configuration file /etc/smartd.conf
Drive: DEVICESCAN, implied '-a' Directive on line 22 of file /etc/smartd.conf
Configuration file /etc/smartd.conf was parsed, found DEVICESCAN, scanning devices
glob(3) found no matches for pattern /dev/hd[a-t]
glob(3) aborted matching pattern /dev/discs/disc*
Problem creating device name scan list
Device: /dev/sda, opened
Device /dev/sda: ATA disk detected behind SAT layer
  Try adding '-d sat' to the device line in the smartd.conf file.
  For example: '/dev/sda -a -d sat'
Unable to register SCSI device /dev/sda at line 22 of file /etc/smartd.conf
Device: /dev/sdb, opened
Device: /dev/sdb, Bad IEC (SMART) mode page, err=5, skip device
Unable to register SCSI device /dev/sdb at line 22 of file /etc/smartd.conf
Unable to monitor any SMART enabled devices. Try debug (-d) option. Exiting...
spacepopeye@spacerig:~$ 


```

Any suggestions? I'm sure if I keep playing with it, I'll get it going eventually.
Thanks for your help so far!

---

### Post by manuelb on 2008-01-11
> **transkinetic said:**
> 
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes


You shouldn't do that on a MOUNTED volume man, boot from a livecd, make sure its unmounted and then perform the check!

---

