---
title: "[SOLVED] Can't burn CDs"
date: 2008-10-03
forum: General Help
---

### Post by PeregrinGo on 2008-10-03
Hi folks,

I already posted this message in the Hardware and Laptops forum, but I'm not sure if that's the most appropriate place for it. Basically, I can't burn CDs in Ubuntu with a burner that worked perfectly in XP. Here's the original thread. I hope some of you who are Linux / Ubuntu experts can lend me a hand. Thanks!

[http://ubuntuforums.org/showthread.php?t=936651](http://ubuntuforums.org/showthread.php?t=936651)

---

### Post by melojo on 2008-10-03
I replied

---

### Post by PeregrinGo on 2008-10-03
:::Bump:::

---

### Post by PeregrinGo on 2008-10-03
Unfortunately, K3b (which I was able to download after about 2 hours) does nothing to remedy this issue. It registered the following error: "Cdrecord has no permission to open the device."

The debugging output produced the following:
--------------------------------------------
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version: 3.3.8b
Kernel: 2.6.24-19-generic
Devices
-----------------------
CENDYNE_ 481648AX 120F (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

CREATIVE CD5233E-CF 1.04 (/dev/scd1, ) [CD-ROM] [Error] [None]
K3bIsoImager
-----------------------
mkisofs print size result: 17328 (35487744 bytes)
Pipe throughput: 124928 bytes read, 104448 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type : Removable CD-ROM
Version : 5
Response Format: 2
Capabilities :
Vendor_info : 'CENDYNE_'
Identification : '481648AX '
Revision : '120F'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW)
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size : 12582912 = 12288 KB
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB: 3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 187.512s timeout 40s
/usr/bin/wodim: Cannot load media.
/usr/bin/wodim: Cannot eject media.
Track 01: data 33 MB
Total size: 38 MB (03:51.06) = 17330 sectors
Lout start: 39 MB (03:53/05) = 17330 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -tao driveropts=burnfree -eject -multi -xa -tsize=17328s -

mkisofs
-----------------------
17328
I: -input-charset not specified, using utf-8 (detected in locale settings)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid rFw2bQ280083-02 -volset -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-harold/k3bE1nF0a.tmp -rational-rock -hide-list /tmp/kde-harold/k3bQcwS5a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-harold/k3blMOzlc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-harold/k3bkI27Xa.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid rFw2bQ280083-02 -volset -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-harold/k3bFECPXb.tmp -rational-rock -hide-list /tmp/kde-harold/k3bmS7Lgc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-harold/k3bVHu0fb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-harold/k3b34RXha.tmp
------------------------------------------------


Is there anyone with a similar problem and/or solution?

---

### Post by PeregrinGo on 2008-10-03
>>bump<< please help >>bump<<

---

