---
title: "CD burning through firewire not possible?"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by QuiQ on 2005-09-24
Hi all,

I have problem with creating _CD_ (DVD not tested yet) on my notebook. 
I use a LG GSA-4120B and connect it through PCMCIA firewire card (AFW-1430) to my notebook (HP Pavilion).
Reading of CDs is OK but I can burn any CD, I'm just occasional linux user so I don't if it's not possible in this stage of linux or I have some problem with my environment...
The problem I have on Hoary as well as on Breezy
Thanks for any advices 

the following error log is produced by K3B:

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.2
QT Version:  3.3.4
Kernel:      2.6.12-9-686
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4120B A110 (/dev/scd0, /dev/sg0) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

MATSHITA DVD-ROM SR-8175 G025 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.33
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 2
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4120B'
Revision       : 'A110'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Input/output error. read buffer: scsi sendcmd: retryable error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x0 (GOOD STATUS)
cmd finished after 289.957s timeout 200s
/usr/bin/X11/cdrecord: No such device or address. Cannot send SCSI cmd via ioctl
......................."""""""""___many____ times""""""""""'....................
/usr/bin/X11/cdrecord: No such device or address. Cannot send SCSI cmd via ioctl

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=0,0,0 speed=40 -dao driveropts=burnfree -eject -data /home/anonymous/k3b_0.iso

---

