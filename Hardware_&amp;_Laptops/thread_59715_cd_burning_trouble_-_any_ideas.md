---
title: "cd burning trouble - any ideas?"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by bionnaki on 2005-08-25
I am trying to burn a copy of the ubuntu live cd and have had no luck. I have used both gnomebaker and k3b (thought I'd give it a try). Each time I have attempted to burn has ended in failure.

here is the log for k3b. perhaps someone can make sense of it:

> Devices
-----------------------
PIONEER DVD-RW  DVR-105 1.21 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
SONY DVD-ROM DDU1612 DYS1 (/dev/hdb, ) at /media/cdrom1 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.24
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-105 '
Revision       : '1.21'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   624 MB        
Total size:      717 MB (71:06.04) = 319953 sectors
Lout start:      718 MB (71:08/03) = 319953 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 39893
Starting to write CD/DVD at speed 16 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  624 MB written.
Track 01:    1 of  624 MB written (fifo  96%) [buf  76%]  11.4x.
Track 01:    2 of  624 MB written (fifo  95%) [buf  83%]  13.1x.
Track 01:    3 of  624 MB written (fifo  98%) [buf  80%]  16.4x.
[*edited*]
Track 01:  624 of  624 MB written (fifo 100%) [buf  77%]  16.3x.
Track 01: Total bytes read/written: 655259648/655259648 (319951 sectors).
Writing  time:  271.706s
Average write speed  15.8x.
Min drive buffer fill was 75%
Fixating...
/usr/bin/cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.477s timeout 480s
cmd finished after 1.477s timeout 480s
Fixating time:    1.575s
/usr/bin/cdrecord: Cannot fixate disk.
/usr/bin/cdrecord: fifo had 10321 puts and 10321 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 2424 times full, min fill was 53%.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -tao driveropts=burnfree -eject -data /home/bill/ubuntu-5.04-live-i386.iso 



Any ideas on how I can correct this?
Thanks!

---

### Post by bionnaki on 2005-08-26
bump

---

### Post by FLeiXiuS on 2005-08-26
Have you tried:
-bumping down how fast your burning?
-enabling dma? (sudo hdparm -d1 /dev/cdrom)
-changing burning medium (memorex/sony/etc..)

Other then this..give me feedback on everything you've tried..

---

### Post by trash on 2005-08-31
[QUOTE=FLeiXiuS]Have you tried:
-bumping down how fast your burning?
-enabling dma? (sudo hdparm -d1 /dev/cdrom)
-changing burning medium (memorex/sony/etc..)

Other then this..give me feedback on everything you've tried..[/QUOTE]

I have the same drive, tried everything suggested with no luck.

fstab has dev/sr0 entry but graveman scans it as dev/scd0 where as gnomebaker scans it as dev/sr0... neither burns but i have no problem watching dvd's.

EDIT:
I have no problem burning from the livecd with cdcreater... but no go with the installed system:(

---

