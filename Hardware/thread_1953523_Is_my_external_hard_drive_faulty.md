---
title: "Is my external hard drive faulty?"
date: 2012-04-06
forum: Hardware
---

### Post by arroy_0209 on 2012-04-06
I have two ext. hard drives (disks) and one of them works fine. When I add to the computer, a new window opens automatically showing the folders. However when the second is connected, sometimes it is opened showing the folders and sometimes it is not opened. There is no icon on the desktop. The command sudo fdisk -l shows (when it is not shown on desktop):
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x000306a7

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       30032   241223680   83  Linux

/dev/sda2           30032       30402     2972673    5  Extended

/dev/sda5           30032       30402     2972672   82  Linux swap / Solaris


Disk /dev/sdb: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x2e892aa8


   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

```
also the messages file shows:
```

usb 1-5: USB disconnect, address 5

usb 1-5: new high speed USB device using ehci_hcd and address 6

usb 1-5: configuration #1 chosen from 1 choice

scsi5 : SCSI emulation for USB Mass Storage devices

scsi 5:0:0:0: Direct-Access     Hitachi  HTS541680J9AT00       PQ: 0 ANSI: 0

sd 5:0:0:0: Attached scsi generic sg2 type 0

sd 5:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)

sd 5:0:0:0: [sdb] Write Protect is off

sdb: sdb1

sd 5:0:0:0: [sdb] Attached SCSI disk

```
and nothing after that. Normally when I encounter such behavior, I am able to open the ext. disk on windows but I am asked to format. The inside folders are not opened by windows also. Strangely if I format, then for few days the disk behaves normally, if used frequently both on ubuntu (10.04) or on windowsXP. But if I do not use for a few months, the problem is faced again. What should I do?

---

### Post by coffeecat on 2012-04-07
*Thread moved to **Hardware & Laptops**, at request of OP.*

---

### Post by cody1233 on 2012-04-07
Make sure all of the USB cables and docks are securely tightened and maybe plug it into a different port (preferably on a different card).  If that doesn't work I would probably try getting a new USB cable.  If that doesn't work it might be a problem with the drive.

---

### Post by recluce on 2012-04-08
Three possibilities:

1.) Faulty USB hub/connector/cable. Try to connect to a different computer with a different cable. If the problem stays, try the next solution. If the problem goes away, you need to do some troubleshooting on the USB subsystem of the first computer.

2.) Faulty USB bridge or power supply on your external USB drive. Try this ONLY if you don't void any warranty this way: remove the drive from its enclosure and connect to an eSATA dock or directly to an internal SATA cable. If the drive now works reliably, you need a new external HDD enclosure (cheap). If not, try the third solution.

3.) With your drive still connected directly to eSATA or SATA (99% of USB bridges are unable to pass SMART command correctly), run smartmontools (this needs to be installed, but can even be installed in a live session).

First command to use from a shell is:

```

sudo smartctl -a /dev/sdX

```

Where X is the device letter of your drive (a,b,c etc). If in doubt, a "blkid -o list" shows the devices in your machine.

Look for any "failed" entries in the SMART parameters and if overall SMART status passes. Feel free to post the output here, if you like. Next thing to do, if everything looks fine:

```

sudo smartctl --test=long /dev/sdX

```

This test can take a long time (60 to 200 minutes), smartctl will let you know the estimated test time. Do not restart or power off your computer during that period. After the time for the test has elapsed, use the first smartctl command above to see the self-test result. You should see a new entry on top of the list of test (if not, you need to wait a bit longer). The test should have passed, any error here means a failing drive.

4.) If all of the above does not yield results, try some vodooo... ;)

---

### Post by DWade on 2012-04-14
I think it is the Hitachi USB drive.

I just may take mine apart and try it in the my second drive bay. and look at the smart settings.

Mine is a 750 gig usb powered pocked drive.  under dmesg Hitachi  HTS547575A9E384

When I first got the drive I went to use it to back up My nephews laptop. Acronis would not Recognize the drive, So I used a different drive.

Checked the drive out in several modes.  Its visible in Windows, but not in Ubuntu 10.04 or 11.10 or CD version of Acronis which is linux or Clonezilla.  I reformated the drive.  Made a 100 gig primary partition and 540 gig secondary partition. I can see the 100 gig now in Linux but not the 540 secondary. 

and Ubuntu 10.04 loses all drives in nautilus except for filesystem, when drive is plug in to a usb slot. but in Open Office when searching for a file all is listed execpt for secondary 540 gig partition.  A Warning comes up can not mount Hitachi drive when nautilus is opened. Gparted sees it fine

and Ubuntu 11.10 shows only that the USb drive is mounted the 100 gig. Can not see the secondary, but Gparted sees it fine.

---

### Post by DWade on 2012-04-20
A bigger question?  Is your hard drive bigger than 400 gigs?
Next is the partition your having problems with a secondary partition?
Check this post of mine [http://ubuntuforums.org/showthread.php?t=1750320]("http://ubuntuforums.org/showthread.php?t=1750320")

---

