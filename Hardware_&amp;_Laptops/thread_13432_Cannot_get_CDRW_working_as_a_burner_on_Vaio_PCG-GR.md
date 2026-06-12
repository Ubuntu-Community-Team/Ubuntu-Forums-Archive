---
title: "Cannot get CDRW working as a burner on Vaio PCG-GR370"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by offby1 on 2005-01-31
I've been looking over several forum posts on CD-RW troubles and have made some progress, but I am unable to take the last few steps to actually having a working burner on my system.

As the subject states, I have a Sony Vaio PCG-GR370 laptop that has a CDRW drive in it on /dev/hdc

**dmesg | grep hdc**
```
hdc: UJDA710, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x50
``` 

(note, the latter two lines do not always appear -- they seem to be new as of this last reboot, where I tried setting /dev/hdc=ide-scsi in my grub conf (which didn't appear to happen))

cdrecord has been set up to use the cdrw device by default, which is set up as:
```
cdrw=/dev/cdrom 1,5,0   4
```

**cdrecord -prcap**
```
cdrecord: Fifo size 4 too small, turning fifo off.
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'MATSHITA'
Identifikation : 'UJDA710         '
Revision       : '1.50'
Device seems to be: Generic mmc2 DVD-ROM.

Drive capabilities, per MMC-2 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does read DVD-ROM media
  Does read DVD-R media
  Does not write DVD-R media
  Does not read DVD-RAM media
  Does not write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does not support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does not read R-W subcode information
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does not support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 256
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  4234 kB/s (CD  24x, DVD  3x)
  Current read  speed:  4234 kB/s (CD  24x, DVD  3x)
  Maximum write speed:  1411 kB/s (CD   8x, DVD  1x)
  Current write speed:  1411 kB/s (CD   8x, DVD  1x)
  Buffer size in KB: 2048
  Copy management revision supported: 1
```

This seems to suggest that there is a CD-RW drive here, but not how I should go about getting either Nautilus (just has ISO output) graveman (doesn't find a burner at all), eroaster (same deal) or gtoaster (Haven't the slightest idea how its configs work) to recognize the burner.  Can someone perhaps tell me what the last few steps are to make all of this work?

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=offby1]
This seems to suggest that there is a CD-RW drive here, but not how I should go about getting either Nautilus (just has ISO output) graveman (doesn't find a burner at all), eroaster (same deal) or gtoaster (Haven't the slightest idea how its configs work) to recognize the burner.  Can someone perhaps tell me what the last few steps are to make all of this work?[/QUOTE]

Try K3b?

---

### Post by offby1 on 2005-01-31
[QUOTE=poofyhairguy]Try K3b?[/QUOTE]
 I'll have to test it once I get my hands on a blank disc, but it looks like you've got the solution.

Is there, however, any equivalent program that works more naturally in Gnome?  k3b spits out 100s of errors about missing icons and pixmaps when it loads (running from the console, of course) that I'd like not to have.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=offby1]I'll have to test it once I get my hands on a blank disc, but it looks like you've got the solution.

Is there, however, any equivalent program that works more naturally in Gnome?  k3b spits out 100s of errors about missing icons and pixmaps when it loads (running from the console, of course) that I'd like not to have.[/QUOTE]

start k3b this way:

gksudo k3b

I made a link on my top bar that has that as the command. (never use regular sudo, it will mess up your machine).

In the debate of KDE vs Gnome the one place where Gnome really can't compete is Burning apps. K3B is a Crown Jewel of Linux! Use Jdong's backported version for better results (IMHO) in Warty. 

The K3B in Hoary is pretty integrated into gnome (even has a little icon next to my clock). 

There is no Gnome app that comes close for now.

---

