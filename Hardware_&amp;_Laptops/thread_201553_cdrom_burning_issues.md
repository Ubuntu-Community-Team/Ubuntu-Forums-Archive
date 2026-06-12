---
title: "cdrom burning issues"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by JTD on 2006-06-22
I'm getting the following error messages from cdrecord (I am in the cdrom group).

cdrecord: Warning: Running on Linux-2.6.15-1-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type : Removable CD-ROM
Version : 0
Response Format: 2
Capabilities :
Vendor_info : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4167B'
Revision : 'DL12'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012
Profile: 0x0011
Profile: 0x0015
Profile: 0x0016
Profile: 0x0014
Profile: 0x0013
Profile: 0x001A
Profile: 0x001B
Profile: 0x002B
Profile: 0x0010
Profile: 0x0009
Profile: 0x000A (current)
Profile: 0x0008
Profile: 0x0002
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13638 kB/s 77x CD 9x DVD
cdrecord: Operation not permitted. Cannot send SCSI cmd via ioctl

I've googled and checked the forums but to no avail yet.
Any help would be appreciated.

JTD
_______________

---

