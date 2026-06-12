---
title: "k3b burning 4x max"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by ap55 on 2005-05-25
Hi, anyone knows why there is this limit of 4x when the cdwriter is a 24x one?

This is the debugging output i get after burning a cd at 4x... any comments?

Thanks


====================================================
====================================================

Devices
-----------------------
HL-DT-ST RW/DVD GCC-4240N 0213 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
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
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4240N'
Revision       : '0213'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 (current)
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1705200 = 1665 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   34 MB (03:24.22) no preemp swab copy
Track 02: audio   41 MB (04:07.84) no preemp swab copy
Track 03: audio   56 MB (05:35.72) no preemp swab copy
Track 04: audio   32 MB (03:11.16) no preemp swab copy
Track 05: audio   33 MB (03:19.98) no preemp swab copy
Track 06: audio   40 MB (03:58.93) no preemp swab copy
Track 07: audio   30 MB (03:00.40) no preemp swab copy
Track 08: audio   91 MB (09:02.40) no preemp swab copy
Track 09: audio   43 MB (04:17.86) no preemp swab copy
Total size:      403 MB (39:58.53) = 179890 sectors
Lout start:      403 MB (40:00/40) = 179890 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 179959
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   34 MB written.
...
...
...
Track 09:   43 of   43 MB written (fifo 100%) [buf  98%]   4.1x.
Track 09: Total bytes read/written: 45487680/45487680 (19340 sectors).
Writing  time:  642.249s
Average write speed   3.8x.
Min drive buffer fill was 96%
Fixating...
Fixating time:   24.748s
/usr/bin/cdrecord: fifo had 6667 puts and 6667 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 6517 times full, min fill was 76%.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -dao driveropts=burnfree -eject -useinfo -pad -shorttrack -audio /tmp/kde-ap55/k3b_audio_0_01.inf /tmp/kde-ap55/k3b_audio_0_02.inf /tmp/kde-ap55/k3b_audio_0_03.inf /tmp/kde-ap55/k3b_audio_0_04.inf /tmp/kde-ap55/k3b_audio_0_05.inf /tmp/kde-ap55/k3b_audio_0_06.inf /tmp/kde-ap55/k3b_audio_0_07.inf /tmp/kde-ap55/k3b_audio_0_08.inf /tmp/kde-ap55/k3b_audio_0_09.inf 

=================================================
=================================================

---

### Post by Leif on 2005-05-25
You probably don't have dma enabled. Search the forum for dma and hdparm.

---

### Post by ap55 on 2005-05-25
already had dma enabled for device /dev/cdrom /dev/dvd and /dev/cdrw (which are the same but just in case)  and it did not fix the problem (hence my post)

---

