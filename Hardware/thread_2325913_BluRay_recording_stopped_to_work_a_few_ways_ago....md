---
title: "BluRay recording stopped to work a few ways ago... Any clues?"
date: 2016-05-26
forum: Hardware
---

### Post by zzarko on 2016-05-26
Following advices on a few web pages, a few months ago I have installed cdrtools form [https://launchpad.net/~brandonsnider/+archive/ubuntu/cdrtools](https://launchpad.net/~brandonsnider/+archive/ubuntu/cdrtools), and compiled latest version (2.0.3a) of K3b from [http://www.k3b.org/](http://www.k3b.org/) for my 14.04 64bit installation (and made a deb file to make installation easier). After that, I have finally stopped using windows, as I could write BluRay discs on Linux with ease :)

At least until a few ways ago... My burning setup just stopped to work, and I cannot find the cause. Every attempt to burn BluRay disc finishes with error, right at the beginning. Here is the log from K3b:
```
Devices
-----------------------
HL-DT-ST DVDRAM GH22NS70 EX00 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
HL-DT-ST BD-RE  BH16NS40 1.03 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, BD-ROM, BD-R, BD-RE, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW, BD-ROM, BD-R Sequential (SRM), BD-R Random (RRM), BD-RE] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump, Random Recording, Sequential Recording, Sequential Recording + POW] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 12163291 (24910419968 bytes)

System
-----------------------
K3b Version: 2.0.3
KDE Version: 4.13.3
QT Version:  4.8.6
Kernel:      3.13.0-87-generic

Used versions
-----------------------
mkisofs: 3.2a06
cdrecord: 3.2a06

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
cdrecord: Warning: Cannot read drive buffer.
cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.02a06 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2016 Joerg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'BD-RE  BH16NS40 '
Revision       : '1.03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: BD-R sequential recording
Profile: BD-RE 
Profile: BD-R random recording 
Profile: BD-R sequential recording (current)
Profile: BD-ROM 
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-RAM 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R 
Profile: CD-ROM 
Profile: Removable Disk 
Using generic SCSI-3/mmc-3 BD-R driver (mmc_bdr).
Driver flags   : NO-CD BD MMC-3 BURNFREE 
Supported modes: PACKET SAO LAYER_JUMP
Drive buf size : 2359296 = 2304 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data  23756 MB        
Total size:     23756 MB = 12163291 sectors
Current Secsize: 2048
WARNING: Phys disk size 4452354 differs from rzone size 12219392! Prerecorded disk?
WARNING: Phys start: 25088 Phys end 4477441
Blocks total: 12219392 Blocks current: 12219392 Blocks remaining: 56101
Reducing transfer size from 64512 to 32768 bytes.
Starting to write CD/DVD/BD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:    0 of 23756 MB written.
[COLOR=#ff0000][B]cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
[/B][/COLOR]cmd finished after 6.838s timeout 200s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   11.843s (00:00:11.843)
Average write speed 468.0x.
Fixating...
operation 99% done
=== last message repeated 8 times. ===
Fixating time:   16.014s (00:00:16.014)
cdrecord: fifo had 128 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was not used.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -xa -tsize=12163291s -

mkisofs
-----------------------
mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
12163291
mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
Setting input-charset to 'UTF-8' from locale.
  0.00% done, estimate finish Fri May 27 13:46:14 2016
  0.01% done, estimate finish Fri May 27 04:26:29 2016
  0.01% done, estimate finish Fri May 27 01:00:53 2016
  0.02% done, estimate finish Thu May 26 23:19:15 2016

mkisofs calculate size command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -print-size -quiet -volid Games -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zzarko/k3bt11810.tmp -rational-rock -hide-list /tmp/kde-zzarko/k3bQ11810.tmp -no-cache-inodes -udf -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-zzarko/k3bb11810.tmp

mkisofs command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid Games -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zzarko/k3bS11810.tmp -rational-rock -hide-list /tmp/kde-zzarko/k3bm11810.tmp -no-cache-inodes -udf -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-zzarko/k3bn11810.tmp
```

I have serached for information about cdrecord error, but I haven't found anything useful. I have also tried to use old Nero Linux, just to see if there is anything wrong with BR drive or discs. It records on the same disc that K3b refused to write just fine. I tried this several times, it is always the same: K3b gives error, Nero writes the same physical disc without a problem. Now, I prefer K3b (OSS, still developed) over Nero (proprietary, no longer supported), so this isn't a permanent solution for me. 

Did anyone had similar problem, and if you did, did you solved it? I really don't want to again restart to win just to burn BR discs...

---

