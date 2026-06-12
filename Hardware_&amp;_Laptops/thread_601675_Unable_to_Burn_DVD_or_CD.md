---
title: "Unable to Burn DVD or CD"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by xcusmwah on 2007-11-03
I have tried 2 DVD ROM Drives, this is my second attempt at burning with Ubuntu (now with another drive).  I cannot burn CD-Rs or DVD-R disks.

**Here is the log from Gnomebaker...**

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 Jörg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-110D'
Revision       : '1.08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 13 03 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.001s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 9967616 bytes
Writing  time:   32.350s
Average write speed 205.1x.
Min drive buffer fill was 97%
Fixating...
Fixating time:   62.608s
cdrecord: fifo had 221 puts and 158 gets.
cdrecord: fifo was 0 times empty and 123 times full, min fill was 78%.





**Here is a log of another attempt from K3b...**
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-110D 1.08 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 2070264 (4239900672 bytes)
Pipe throughput: 48843520 bytes read, 48839168 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 4.1x1352KBps.
   11698176/4239900672 ( 0.3%) @2.2x, remaining 18:04 RBU 100.0% UBU   2.0%
:-[ WRITE@LBA=1d00h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: updating RMA
/dev/hdc: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2070264 -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2070264
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using 2006___MARVEL_LEGACY_HAN000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/2006 - Marvel Legacy Handbook - The 1970's.cbr (2006 - Marvel Legacy Handbook - The 1960's.cbr)
Using WOLVERINE_ENCYCLOPEDIA_V000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/Assorted Marvel Reference Guides/Wolverine Encyclopedia Volume 2.cbr (Wolverine Encyclopedia Volume 1.cbr)
Using G_I__JOE___ORDER_OF_BATT000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/G.I. Joe - Order of Battle 1-4 (Marvel) (1986)/G.I. Joe - Order of Battle #004.cbr (G.I. Joe - Order of Battle #003.cbr)
Using G_I__JOE___ORDER_OF_BATT001.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/G.I. Joe - Order of Battle 1-4 (Marvel) (1986)/G.I. Joe - Order of Battle #003.cbr (G.I. Joe - Order of Battle #002.cbr)
Using G_I__JOE___ORDER_OF_BATT002.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/G.I. Joe - Order of Battle 1-4 (Marvel) (1986)/G.I. Joe - Order of Battle #002.cbr (G.I. Joe - Order of Battle #001.cbr)
Using OFFICIAL_HANDBOOK_OF_THE000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - X-Men 2004.cbr (Official Handbook of the Marvel Universe - Wolverine 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE001.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Wolverine 2004.cbr (Official Handbook of the Marvel Universe - Spider-Man 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE002.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Spider-Man 2004.cbr (Official Handbook of the Marvel Universe - Hulk 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE003.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Hulk 2004.cbr (Official Handbook of the Marvel Universe - Golden Age 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE004.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Golden Age 2004.cbr (Official Handbook of the Marvel Universe - Daredevil 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE005.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Daredevil 2004.cbr (Official Handbook of the Marvel Universe - Book of the Dead 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE006.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4 (2004)/Official Handbook of the Marvel Universe - Book of the Dead 2004.cbr (Official Handbook of the Marvel Universe - Avengers 2004.cbr)
Using OFFICIAL_HANDBOOK_OF_THE000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Ultimate Marvel Universe - The Ultimates & X-Men 2005.cbr (Official Handbook of the Ultimate Marvel Universe - Spider-Man & Fantastic Four.cbr)
Using OFFICIAL_HANDBOOK_OF_THE001.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - X-Men 2005.cbr (Official Handbook of the Marvel Universe - X-Men - AOA 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE002.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - X-Men - AOA 2005.cbr (Official Handbook of the Marvel Universe - Women of Marvel 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE003.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Women of Marvel 2005.cbr (Official Handbook of the Marvel Universe - Teams 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE004.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Teams 2005.cbr (Official Handbook of the Marvel Universe - Spider-Man 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE005.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Spider-Man 2005.cbr (Official Handbook of the Marvel Universe - Marvel Knights 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE006.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Marvel Knights 2005.cbr (Official Handbook of the Marvel Universe - Horror 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE007.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Horror 2005.cbr (Official Handbook of the Marvel Universe - Fantastic Fou 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE008.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Fantastic Fou 2005.cbr (Official Handbook of the Marvel Universe - Avengers 2005.cbr)
Using OFFICIAL_HANDBOOK_OF_THE009.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v4a (2005)/Official Handbook of the Marvel Universe - Avengers 2005.cbr (Official Handbook of the Marvel Universe - Alternate Universes 2005.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO000.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 07.cbr (All-New Official Handbook of the Marvel Universe 06.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO001.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 06.cbr (All-New Official Handbook of the Marvel Universe 05.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO002.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 05.cbr (All-New Official Handbook of the Marvel Universe 04.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO003.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 04.cbr (All-New Official Handbook of the Marvel Universe 03.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO004.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 03.cbr (All-New Official Handbook of the Marvel Universe 02.cbr)
Using ALL_NEW_OFFICIAL_HANDBOO005.CBR;1 for  Official Handbook Of The Marvel Universe (All Versions) + Assorted Marvel Reference Books/OHOTMU v5 A to Z (2006) Ongoing/All-New Official Handbook of the Marvel Universe 02.cbr (All-New Official Handbook of the Marvel Universe 01.cbr)
  0.02% done, estimate finish Sat Nov  3 10:46:17 2007
  0.05% done, estimate finish Sat Nov  3 10:46:17 2007
  0.07% done, estimate finish Sat Nov  3 10:46:17 2007
  0.10% done, estimate finish Sat Nov  3 10:46:17 2007
  0.12% done, estimate finish Sat Nov  3 10:46:17 2007
  0.15% done, estimate finish Sat Nov  3 10:46:17 2007
  0.17% done, estimate finish Sat Nov  3 10:46:17 2007
  0.19% done, estimate finish Sat Nov  3 10:46:17 2007
  0.22% done, estimate finish Sat Nov  3 10:46:17 2007
  0.24% done, estimate finish Sat Nov  3 10:46:17 2007
  0.27% done, estimate finish Sat Nov  3 10:46:17 2007
  0.29% done, estimate finish Sat Nov  3 10:46:17 2007
  0.31% done, estimate finish Sat Nov  3 10:46:17 2007
  0.34% done, estimate finish Sat Nov  3 10:46:17 2007
  0.36% done, estimate finish Sat Nov  3 10:46:17 2007
  0.39% done, estimate finish Sat Nov  3 10:46:17 2007
  0.41% done, estimate finish Sat Nov  3 10:46:17 2007
  0.44% done, estimate finish Sat Nov  3 10:46:17 2007
  0.46% done, estimate finish Sat Nov  3 10:46:17 2007
  0.48% done, estimate finish Sat Nov  3 10:46:17 2007
  0.51% done, estimate finish Sat Nov  3 10:46:17 2007
  0.53% done, estimate finish Sat Nov  3 10:46:17 2007
  0.56% done, estimate finish Sat Nov  3 10:46:17 2007
  0.58% done, estimate finish Sat Nov  3 10:46:17 2007
  0.60% done, estimate finish Sat Nov  3 10:46:17 2007
  0.63% done, estimate finish Sat Nov  3 10:46:17 2007
  0.65% done, estimate finish Sat Nov  3 10:46:17 2007
  0.68% done, estimate finish Sat Nov  3 10:46:17 2007
  0.70% done, estimate finish Sat Nov  3 10:46:17 2007
  0.73% done, estimate finish Sat Nov  3 10:46:17 2007
  0.75% done, estimate finish Sat Nov  3 10:48:30 2007
  0.77% done, estimate finish Sat Nov  3 10:48:26 2007
  0.80% done, estimate finish Sat Nov  3 11:00:55 2007
  0.82% done, estimate finish Sat Nov  3 11:00:28 2007
  0.85% done, estimate finish Sat Nov  3 11:02:02 2007
  0.87% done, estimate finish Sat Nov  3 11:03:31 2007
  0.89% done, estimate finish Sat Nov  3 11:03:04 2007
  0.92% done, estimate finish Sat Nov  3 11:02:36 2007
  0.94% done, estimate finish Sat Nov  3 11:02:12 2007
  0.97% done, estimate finish Sat Nov  3 11:03:31 2007
  0.99% done, estimate finish Sat Nov  3 11:03:06 2007
  1.02% done, estimate finish Sat Nov  3 11:02:42 2007
  1.04% done, estimate finish Sat Nov  3 11:02:19 2007
  1.06% done, estimate finish Sat Nov  3 11:01:57 2007
  1.09% done, estimate finish Sat Nov  3 11:03:08 2007
  1.11% done, estimate finish Sat Nov  3 11:02:46 2007
  1.14% done, estimate finish Sat Nov  3 11:02:25 2007

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Official Handbook Of The Marvel  -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-someguy/k3bCphVIa.tmp -rational-rock -hide-list /tmp/kde-someguy/k3bXVVQUb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-someguy/k3bDvhUSb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-someguy/k3bCA1avb.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Official Handbook Of The Marvel  -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-someguy/k3b1YMgda.tmp -rational-rock -hide-list /tmp/kde-someguy/k3bxF5oub.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-someguy/k3bm6bxDa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-someguy/k3bk6XULa.tmp

---

### Post by jrev on 2007-11-03
It would be quicker to go back to windows.

Also I have been on linux for  years I would prefer to go to windows to have a reliable manufacturer CD burner. 

:lolflag:

---

