---
title: "Can I update from Ubuntu 5.04 to Kubuntu 5.10 ??"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2005-12-29
I have been running 5.04 for quite some time now and have lost patience with trying to solve some problems regarding writing CD's. I would like to be able to update to  Kubuntu 5.10 directly through APT,  if this is possible. Can someone please explain how this might be achieved. Cheers

---

### Post by varunus on 2005-12-29
Well, one way to do this would be to open up /etc/apt/sources.list using "sudo gedit" from a terminal, change every instance of "hoary" to "breezy", and then open synaptic.

Once you do, you'll get an error about package lists; reload your packages to fix it.

Then, mark all upgrades, and install the package "kubuntu-desktop" along with it.  This will install KDE.  Hit apply, and let the process work; then follow aysiu's howto on howto remove GNOME once KDE has been installed.

---

### Post by Julian David Pitt on 2006-01-01
I did as suggested and sure enough it worked fine, but the problems I had previouslya re still there, namely that I cannot burn CD's. I have tried Gnomebaker and K3b with the same results. I have included the debug output below
> System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.10-6-386
Devices
-----------------------
PIONEER DVD-ROM DVD-115 1.27 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

ATAPI CD-R/RW 12X8X32 9.CC (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; RAW/R16; RAW/R96R]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.10-6-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
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
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-R/RW 12X8X32 '
Revision       : '9.CC'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R16 RAW/R96R
Drive buf size : 1630208 = 1592 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   617 MB        
Total size:      708 MB (70:13.08) = 315981 sectors
Lout start:      709 MB (70:15/06) = 315981 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11078 (97:34/22)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43868
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
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 79.698s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1592 K BSize: 1592 K
Starting new track at sector: 0
Track 01:    0 of  617 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 82.225s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:  166.975s
Average write speed  25.2x.
Fixating...
Fixating time:    0.003s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=4 -dao driveropts=burnfree -eject -data /home/julian/Download/ubuntu-5.10-install-i386.iso 

Hopefully someone can make head or tail of this, many thanks in advance.

---

