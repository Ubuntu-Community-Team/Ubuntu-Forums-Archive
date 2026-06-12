---
title: "HP DVD1070 SATA Burner Won't Burn DVDs"
date: 2010-02-20
forum: Hardware
---

### Post by -kg- on 2010-02-20
I'm at my wits end.  I've searched using Uboontu and all and can't find this problem.  I'm running Karmic, but this has extended back through Jaunty and, I think, Hardy.

I have an HP DVD1070 SATA DVD drive installed on an ASUS A8V Deluxe MB with an AMD 64 3200+ processor, 1 GB DDR memory.  I cannot burn an ISO by any means; either with Brasero or with k3b.  Either of these programs works fine on my laptop, but I can't burn on my tower.

First I did it with k3b, and of course it failed with the first results:

> Devices
-----------------------
SONY CD-RW  CRX175A1 5YS2 (/dev/sr0, CD-R, CD-RW, CD-ROM) [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R] [%7]
HP DVD Writer 1070r RH22 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-19-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 1070r'
Revision       : 'RH22'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1343488 = 1312 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 22160 KB/s
Track 01: data  3674 MB        
Total size:     4220 MB (418:06.49) = 1881487 sectors
Lout start:     4220 MB (418:08/37) = 1881487 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 413617
Starting to write CD/DVD at speed  17.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 3674 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 1F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 210.840s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 63488 bytes
Writing  time:  243.350s
Average write speed  12.9x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 1000s
Fixating time:    1.801s
/usr/bin/wodim: fifo had 192 puts and 2 gets.
/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 99%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr1 speed=16 -sao driveropts=burnfree -data -tsize=1881487s -

I then tried it by running k3b as root with the next results:

> Devices
-----------------------
SONY CD-RW  CRX175A1 5YS2 (/dev/sr0, CD-R, CD-RW, CD-ROM) [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R] [%7]
HP DVD Writer 1070r RH22 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-19-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 1070r'
Revision       : 'RH22'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1343488 = 1312 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 5540 KB/s
Track 01: data  3674 MB        
Total size:     4220 MB (418:06.49) = 1881487 sectors
Lout start:     4220 MB (418:08/37) = 1881487 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 413617
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 3674 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 3E 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 210.659s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 126976 bytes
Writing  time:  240.162s
Average write speed  12.9x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 1000s
Fixating time:    4.527s
/usr/bin/wodim: fifo had 193 puts and 3 gets.
/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 98%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr1 speed=4 -sao driveropts=burnfree -data -tsize=1881487s -

I also tried with Brasero.  It looked like it was going to work, but failed at the last:

The first two Thumbnails are for the first two tries and the last two are for the Brasero try.  Anyone have any ideas?

---

### Post by -kg- on 2010-02-21
Bump, and an addendum:

I found a thread (not exactly applicable to my situation, but...) that suggested the following command:

```
sudo chmod 777 /dev/sr1 (<-the drive in question)
```

It didn't work, so I wonder if it is right, or if I'm doing it correctly.  It would make sense considering that k3b was complaining about permissions the first time.  Also, the second try (as root) didn't complain about it, but instead cdrecord returned the error.  I assume that, though I ran k3b as root, cdrecord itself didn't.

I tried editing k3bsetup to give cdrecord permission as suggested, but was unable to figure out how to do so.  I would think that, if the above command was right, that cdrecord would have the requisite permission to access the drive anyway, but apparently not.  Would cdrecord's permissions override the permissions I (assume I) chmod'ed the drive with?  I guess a little more research is going to be necessary on that.

What really gets me, though, is that Brasero went through the whole write procedure, threw an error, and at the same time said that the burn was successful.  It wasn't...the disk was unreadable and unmountable.  My DVD drive is visible in Nautilus with no disk, and with a good disk in it, but disappears when I put the disk I burned in it.  I assume it's another coaster.

I want to get this situation resolved.  I think that the drive in my laptop is going out, and the one in the tower is nearly brand new.  If nothing else, I may install an alternative OS which allows me to run as root and just drop into root when I need to burn; that is, if I can't get it to work under a normal user account.  I want to figure this out, though, since among other things, it is a learning process.

---

### Post by redcap on 2010-03-24
I am not using an HP drive, but I am having the exact same problems as -kg-. My drive is a Samsung SH-S223F.

I am running Linux Mint 8 Main Edition, and I just posted a similar issue over on the Mint forums.  If you want to check it out, you can find it here: [http://forums.linuxmint.com/viewtopic.php?f=49&t=44677](http://forums.linuxmint.com/viewtopic.php?f=49&t=44677)

So far, I have tried Brasero, growisofs, GnomeBaker, k3b and xfburn, but none of them worked. The drive works flawlessly while booted into a Windows partition.

The only reply I've received over there is about a bug where the file system is reporting the incorrect amount of space on the drive and that's what is causing the burning issue.  I have no idea if that's what's actually happening or not, but it's the only lead I've got so far.  Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200)

I see this post is a month old so I'm curious to see if there's a solution out there.  If there is, I'd love to hear about it.

---

### Post by DarkRookie on 2011-03-26
I had a similar issue.
In k3b, I lowered the burn speed from 4 to 3 and that worked for me, maybe try something similar

---

