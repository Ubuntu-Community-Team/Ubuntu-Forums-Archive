---
title: "USB Problem with the DVD Writer LG GSA-5163D"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by catworld on 2005-06-12
Ubuntu detect it without problems, but if I want with K3b other program copy then I can not copy and there is an error:
[B]
input/output error.Not necessarily serious[/B]

I don't know to solve this problem.



Dmesg:
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: HL-DT-ST  Model: DVDRAM GSA-5163D  Rev: A102
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0
usb-storage: device scan complete
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5





cdrecord -scanbus

Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.31
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'HL-DT-ST' 'DVDRAM GSA-5163D' 'A102' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
 

log of KDE

Devices
-----------------------
HL-DT-ST DVDRAM GSA-5163D A102 (/dev/scd0, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
MATSHITA UJDA740 DVD/CDRW 1.04 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-686

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-686
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.31
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
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-5163D'
Revision       : 'A102'
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
/usr/bin/cdrecord: Input/output error. read buffer: scsi sendcmd: cmd timeout after 6.008 (40) s
CDB:  3C 00 00 00 00 00 00 FC 00 00
resid: 2
cmd finished after 6.008s timeout 40s
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
FIFO size      : 4194304 = 4096 KB

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=0,0,0 speed=40 -tao driveropts=burnfree -eject -data /tmp/kde-miquel/Reino cielos.iso 

mkisofs
-----------------------
Warning: creating filesystem with (nonstandard) Joliet extensions
         but without (standard) Rock Ridge extensions.
         It is highly recommended to add Rock Ridge
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
 10.84% done, estimate finish Sun Jun 12 16:03:59 2005
 21.38% done, estimate finish Sun Jun 12 16:03:59 2005
 32.03% done, estimate finish Sun Jun 12 16:04:02 2005
 42.77% done, estimate finish Sun Jun 12 16:04:01 2005
 53.41% done, estimate finish Sun Jun 12 16:04:00 2005
 64.13% done, estimate finish Sun Jun 12 16:04:02 2005
 74.99% done, estimate finish Sun Jun 12 16:04:01 2005
 85.38% done, estimate finish Sun Jun 12 16:04:01 2005
 96.31% done, estimate finish Sun Jun 12 16:04:02 2005
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 28
Max brk space used 21000
4686 extents written (9 MB)

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid Reino cielos -volset  -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-miquel/k3bvTT0oa.tmp -joliet -hide-joliet-list /tmp/kde-miquel/k3bza2ACb.tmp -udf -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-miquel/k3b5pYnLa.tmp /home/miquel/.kde/share/apps/k3b/temp/dummydir0/ 


Anybody can help me?
TIA
 :-?

---

### Post by davey.moore on 2006-06-01
i am having the same problem now on dapper.
it's been one year, so hopefully you managed to fix it and read this soon!

thanks!

---

