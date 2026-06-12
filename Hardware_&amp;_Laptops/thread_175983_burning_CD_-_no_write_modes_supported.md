---
title: "burning CD - no write modes supported"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by jamespfeiffer on 2006-05-14
Hello,

I wanted to burn some music to a CD.  Serpentine did not work, and when I tried to use:
cdrecord dev=ATAPI:/dev/hdd driveropts=burnfree -v -audio *
it gave me an error message "TAO not supported", and in fact lists no write modes under Supported Modes.
```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 0 = CD-DA
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: 'ATAPI:/dev/hdd'
devname: 'ATAPI:/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'SONY    '
Identifikation : 'DVD RW DRU-510A '
Revision       : '1.1a'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x001B
Profile: 0x001A
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes:
Drive buf size : 8112896 = 7922 KB
Drive DMA Speed: 2358 kB/s 13x CD 1x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.
```
It says I should switch to linux 2.4 but I don't want to do that unless I have to.  I haven't been able to find this problem discussed anywhere, and I've looked for a while, so it must not be very widespread.  

My drive is a Sony DVDRW DRU510A.  I can read from the drive fine.

Any suggestions?

Thanks

---

