---
title: "usb external drive doesn't get detected"
date: 2011-04-21
forum: Hardware
---

### Post by ravengirl1960 on 2011-04-21
I'm running Ubuntu Studio on an HP Pavillion dv6000 laptop. I had Windows 7 on it and I had no problem with the usb detection.

When I boot, the device I'm looking for shows up but it isn't detected in the file system. I have two drives, a 500g and a 1Tb in a dual usb case.

Checking a few things:

erin@penguinperch:~$ lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 046d:c31c Logitech, Inc. 
Bus 001 Device 006: ID 046d:c05a Logitech, Inc. 
**Bus 001 Device 005: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive**
Bus 001 Device 004: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 03f0:2504 Hewlett-Packard DeskJet F4200 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and (note: the 200g is my laptop drive, the other two are the usb-case drives):

erin@penguinperch:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046636

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187395072   83  Linux
/dev/sda2           23330       24322     7963649    5  Extended
/dev/sda5           23330       24322     7963648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c6e34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a4f3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      120455   967546880   83  Linux
/dev/sdc2          120455      121602     9212929    5  Extended
/dev/sdc5          120455      121602     9212928   82  Linux swap / Solaris

The 500g drive shows up as "New Volume" in the system and works fine.

---

### Post by ravengirl1960 on 2011-04-21
Okay, I tried installing Ubuntu 10.04 on this laptop. It does the same thing. (since I have all my data on the 500G drive, wipes/installs are no big deal).

The ironic thing is that when I went to install Ubuntu, the disk recognized all three drives; the 200g laptop, the 500g external and the 1Tb external. 

Now that Ubuntu is installed, however, it still won't recognize the drive.

*looks confused*

---

