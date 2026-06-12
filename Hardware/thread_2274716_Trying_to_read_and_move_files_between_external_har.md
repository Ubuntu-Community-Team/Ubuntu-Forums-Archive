---
title: "Trying to read and move files between external hard drives."
date: 2015-04-21
forum: Hardware
---

### Post by plan-b2 on 2015-04-21
Hi all,

First off I should share that this is my first hours of playing with Ubuntu so please bare with my learning curve.

A few weeks ago our pvr started making the death sounds of a dying fan  and I knew it was time for a replacement. I started to copy all our  saved and unwatched shows over to an external HD, but unfortunately the  pvr packed it in after only about 10% was transferred. The new pvr is up  and running now and I was able to copy the 10% that I had saved over to  it. The problem I have is, I would like to somehow save the other 90%  that is still left on the old pvr's internal HD. I've pulled the old HD  out of the pvr and connected it to my windows pc via a hard drive dock, but the  pc will not recognize the drive, either in explorer or disk management.  I've also tried connecting the old drive directly to the new pvr, but  the pvr wants to format it and won't read the data off it. 

After a little research I've found that the drives are formatted with an EXT3 filesystem – primarily used by Linux. I've since created and booted from an Ubuntu live cd, but I'm still not finding the drives for editing in ubuntu "files/devices".  

With one the old pvr internal drive connected via usb, if I enter "sudo fdisk -l" in terminal, I get the following. I'm thinking the "/dev/sda2" is the drive in question.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc86f2ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   12  Compaq diagnostics
/dev/sda2        27265024    27469823      102400   1a  Unknown
/dev/sda3   *    27469824   976771071   474650624    7  HPFS/NTFS/exFAT


If i type "lsusb" in terminal, I get the following. Again I'm thinking "Bus 001 Device 001" is the drive and "Bus 002 Device 004" is the usb reader I'm using to access it.

Bus 002 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I'm pretty much at a loss as to where to go from here. Any and all help is very appreciated.

---

### Post by papibe on 2015-04-21
Hi plan-b2. Welcome to the forum ):P

I'm inclined towards /dev/sda3...

Is that the only disk on the system?
Are using a live CD or a live USB stick?

If there are another disk involved, then it is not that simple. The disk is /dev/sda and the partitions are sda1, sda2, and sda3. If it were another disk it should be, say, /dev/sdb and its partitions should start with sdb1

You should be able to mount the sda3 partition by clicking on one of the disk icons available on the launcher. Try that and see what happens.

If that doesn't work, you can try this on a terminal:
```
mkdir pvr

sudo mount /dev/sda3 pvr/
```
Then try to open Nautilus (File Manager), and browse the pvr directory.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by plan-b2 on 2015-04-21
Hi Papibe,

Thanks so much for the welcome and quick response to my issues. After reading your post I think maybe were both off base. The top line says /dev/sda is 500.1 GB. The internal hard drive on my laptop is 500 gb and also has 3 partitions. I'm thinking the /dev/sda1, 2, and 3 are the partitions on the laptops internal drive and it's not showing the external drive at all. 

I'm using a live cd to boot from and the loptop has an internal drive, so along with the external drive there should be multiple disks showing up on the system. The Ubuntu disk app does show the 320 gb external drive, but the edit mount options button is grayed out and not accessible. 

Thanks again so much for all your help.

[COLOR=#000000]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/COLOR]
[COLOR=#000000]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/COLOR]
[COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#000000]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#000000]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#000000]Disk identifier: 0xcc86f2ea[/COLOR]

[COLOR=#000000]Device Boot Start End Blocks Id System[/COLOR]
[COLOR=#000000]/dev/sda1 2048 27265023 13631488 12 Compaq diagnostics[/COLOR]
[COLOR=#000000]/dev/sda2 27265024 27469823 102400 1a Unknown[/COLOR]
[COLOR=#000000]/dev/sda3 * 27469824 976771071 474650624 7 HPFS/NTFS/exFAT


[/COLOR]

---

### Post by papibe on 2015-04-21
> **plan-b2 said:**
> The Ubuntu disk app does show the 320 gb external drive, but the edit mount options button is grayed out and not accessible.
Interesting.

There's a possibility that the disk is formated using exfat. By default the driver is not install on a regular Ubuntu install.

Let's see if that's the case. When using the live CD, install the utilities to support exfat:
```
sudo apt-get install exfat-utils exfat-fuse
```
Then try if you can mount the external drive.

Let us know how that goes.
Regards.

---

### Post by weatherman2 on 2015-04-21
Hard drives fail completely all the time.  This one may be dead, and in that case, you won't be able to recover anything with Ubuntu.

You can try installing GSmartControl from a Ubuntu live session to check the drive's S.M.A.R.T. health - enable the "universe" repository first:

[http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository](http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository)

Then install gsmartcontrol from a terminal window (Ctrl alt t to open a terminal window):

```

sudo apt-get install gsmartcontrol

```

Then start GSmartControl and see which drives are detected.  If only your laptop drive shows up, maybe the drive has truly failed and isn't even detected - though sometimes it is difficult to get S.M.A.R.T. data from a USB-connected drive.

---

### Post by plan-b2 on 2015-04-21
Thanks guys, 

I will try both of the above suggestions and report back later tonight, but I think we might be barking up the wrong trees. From what I've read in post like the one below and others, the Bell PVR drives are formatted with the EXT3 file system. I can't personally confirm one way or the other so I will definitely try the exfat utilities. [https://answers.launchpad.net/ubuntu/+question/81662](https://answers.launchpad.net/ubuntu/+question/81662)

I'm pretty sure the drive is in working order. The old PVR has overheating issues I think, not hard drive. With the hard drive installed in the PVR, it can read and access the drive fine. The problem is that the PVR overheats and freezes after about 10-30 seconds of use making it impossible to use the PVR to copy the files to my external hard drive. Also, with the old PVR hard drive removed and then connected to the new PVR as an external hard drive, the new PVR can see and access the drive. The problem here is that the new PVR wants to format the drive for some reason and this would wipe the data I'm assuming. Again, I can't confirm for sure this is the case so will try the above Gsmartcontrol suggestion above as well. I'll report back and let you know how it goes.

Thanks again for all the help.

---

### Post by plan-b2 on 2015-04-22
Ok. Tried the GSmartControl suggestion first. Before booting with the live cd, I connected the old PVR internal hard drive and my external hard drive which was formatted by the PVR and has a couple PVR recordings on it. The external hard drive shows up in the launcher bar as expected and I can access the files on it, but still no sign of the old PVR internal drive. Once GSmartControl loaded, it showed 4 different drives, my laptops internal drive, laptops DVD-Ram and the two above mentioned drives. The laptop internal drive and my external drive both show the "basic health check" as passed. The DVD-Ram drive and the old PVR internal drive (the one I'm having issues reading) came up as unknown for the "basic health check". Clicking "view details" on the old PVR internal drive bring up the following. I'm not sure if this is of any help.

----------------------------------------------------------------------------------------------------------------------------

smartctl 6.2 2013-07-26 r3841 [i686-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

Warning! Drive Identity Structure error: invalid SMART checksum.
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Pipeline HD 5900.1
Device Model:     ST3320310CS
Serial Number:    5TX01EFT
LU WWN Device Id: 5 000c50 0148b63ab
Firmware Version: ES11
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5900 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Apr 22 05:43:30 2015 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

SMART Disabled. Use option -s with argument 'on' to enable it.
(override with '-T permissive' option)

-----------------------------------------------------------------------------------------------------------------------------

Trying to enable "SMART" on the drive fails, stating "Mandatory SMART command failed"

I also checked out the Ubuntu disks app again with both drives attached to usb. 

The external drive currently comes up as
Device: /dev/sdb
Partitioning: Master Boot Record
Serial Number: 9QM3QMDD
Partition Type: Linux
Contents: Ext3 (Version 1.0)

The old PVR internal drive shows
Device: /dev/sdc
(No Partitioning info)
Serial Number: 000000000000
(No Partition Type info)
Contents: Unknown


After installing the exfat utilities I notice no difference with the problem drive. The edit mount options button is still grayed out and not accessible.


I'm pretty clueless about most of this stuff, but the above has me thinking that maybe the drive is damaged as weatherman suggested? I know it did at least appear to be working before I pulled it out of the PVR. Would my next step be some sort of recovery program and if so do you have any recommendations? 

Once again, thank you so much for all the help with this.

---

