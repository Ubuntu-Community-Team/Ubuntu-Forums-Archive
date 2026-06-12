---
title: "K3B can't burn Dual Layer in 10.04?"
date: 2010-05-15
forum: Hardware
---

### Post by siddartha on 2010-05-15
And here's the output which doesn't make too much sense to me.

Devices
-----------------------
Slimtype DVDRW SLW-831S WS01 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 3864434 (7914360832 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-22-generic

Used versions
-----------------------
mkisofs: 1.1.10
cdrecord: 1.1.10

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'DVDRW SLW-831S  '
Revision       : 'WS01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x002B (DVD+R/DL)
Profile: 0x002B (DVD+R/DL) (current)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1602048 = 1564 KB
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
Speed set to 3324 KB/s
Track 01: data  7547 MB        
Total size:     8668 MB (858:45.78) = 3864434 sectors
Lout start:     8668 MB (858:47/59) = 3864434 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 4173824 Blocks current: 4173824 Blocks remaining: 309390
Starting to write CD/DVD at speed   2.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
dvd_dual_layer_split: read_dvd_structure returns invalid data
Preparing middle zone location for this DVD+R dual layer disc
Waiting for reader process to fill input buffer ... /usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 3A F7 72 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.010s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:    0.044s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=3864434s -

mkisofs
-----------------------
3864434
Warning: -follow-links does not always work correctly; be careful.
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.01% done, estimate finish Sun May 16 12:39:53 2010
  0.03% done, estimate finish Sun May 16 06:13:03 2010
  0.04% done, estimate finish Sun May 16 04:02:24 2010
  0.05% done, estimate finish Sun May 16 02:59:21 2010
  0.06% done, estimate finish Sun May 16 02:21:16 2010
  0.08% done, estimate finish Sun May 16 01:55:46 2010
  0.09% done, estimate finish Sun May 16 01:37:00 2010
  0.10% done, estimate finish Sun May 16 01:23:23 2010
  0.12% done, estimate finish Sun May 16 01:12:46 2010
  0.13% done, estimate finish Sun May 16 01:04:16 2010
  0.14% done, estimate finish Sun May 16 00:57:05 2010
  0.16% done, estimate finish Sun May 16 00:51:18 2010

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Marathon Man -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sidd/k3bg13638.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-sidd/k3bW13638.tmp -dvd-video -f /tmp/kde-sidd/k3bVideoDvd0

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Marathon Man -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sidd/k3bo13638.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-sidd/k3bR13638.tmp -dvd-video -f /tmp/kde-sidd/k3bVideoDvd0

---

