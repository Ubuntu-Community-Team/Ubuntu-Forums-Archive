---
title: "HL-DL-ST DVDRAM making my head ache!"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by kittcankitt on 2005-12-06
Been using breezy for quite some time and it's only been until recently, I'd say maybe two weeks, that this external burner is giving me so many problems that it isn't funny!

I seem to be able to burn DVD iso's fine using almost any way I can get at it be it command line, gnomebaker (usually), graveman, nerolinux.  OK, so this isn't the problem.

The problem is now whenever I try to burn files of any sort to a CD I get all sorts of errors about cdrecord being installed suid, I/O errors, etc.

Example of the Gnomebaker output:
cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '4,0,0'
scsibus: 4 target: 0 lun: 0
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
cdrecord: Input/output error. read buffer: scsi sendcmd: cmd timeout after 6.013 (40) s
CDB:  3C 00 00 00 00 00 00 FC 00 00
resid: 2
cmd finished after 6.013s timeout 40s
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
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
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
FIFO size      : 4194304 = 4096 KB

I've tried dao tao sao and every other *ao  known to man and I can not write to a CD.

Like I mentioned before, it USED to work and I haven't modified any settings pertaining to the drive or anything else that might have caused this.

Any thoughts (or more info needed) to help out?  I've searched the forums and googled but other than a faulty LG and other permission issues, my problem doesn't really fit in there.

Thanks in advance! KCK

---

### Post by az on 2005-12-06
[QUOTE=kittcankitt]
The problem is now whenever I try to burn files of any sort to a CD I get all sorts of errors about cdrecord being installed suid, I/O errors, etc.

Example of the Gnomebaker output:
cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '4,0,0'
scsibus: 4 target: 0 lun: 0
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.[/QUOTE]


These are normal messages that I used to get in Hoary, I beleive.

[QUOTE=kittcankitt]
cdrecord: Input/output error. read buffer: scsi sendcmd: cmd timeout after 6.013 (40) s
CDB:  3C 00 00 00 00 00 00 FC 00 00
resid: 2
cmd finished after 6.013s timeout 40s
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
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
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
FIFO size      : 4194304 = 4096 KB


[/QUOTE]

I dunno about that.  Have changed any hardware on your system?  Can you burn from a live cd (maybe Hoary?)

---

### Post by kittcankitt on 2005-12-06
No I haven't changed any hardware and I've only recently purchased the burner (I was using breezy at the time and it all used to work)  I seem to remember errors and the whole process working anyways but now it won't even go that far.  I just burnt the same thing I was trying to a DVD with gnomebaker and this is the output:

Executing 'mkisofs -V GnomeBaker data cd -p kittcankitt -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points dish=/media/usbdisk/**** f12dti.EXE=/media/usbdisk/windows/f12dti.EXE nero7=/media/USB/Windows_Software/nero7 | builtin_dd of=/dev/sr0 obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
Using R0044779361_301_010_13EB000.BIN;1 for  ****/R0044779361-301.010-13EB-EAEA-10U-P243-U23.bin (R0044779361-301.010-13EB-EAEA-10U-P243-U22.bin)
/dev/sr0: engaging DVD-RW DAO upon user request...
/dev/sr0: reserving 478416 blocks
/dev/sr0: "Current Write Speed" is 2.0x1385KBps.
  0.11% done, estimate finish Tue Dec  6 22:22:51 2005
  0.21% done, estimate finish Tue Dec  6 20:04:44 2005
  0.32% done, estimate finish Tue Dec  6 19:17:20 2005
  0.42% done, estimate finish Tue Dec  6 18:50:03 2005
  0.53% done, estimate finish Tue Dec  6 18:33:00 2005
  0.63% done, estimate finish Tue Dec  6 18:24:40 2005
 
  1.25% done, estimate finish Tue Dec  6 17:58:16 2005
  1.36% done, estimate finish Tue Dec  6 17:55:46 2005
  1.46% done, estimate finish Tue Dec  6 17:54:49 2005
  99.50% done, estimate finish Tue Dec  6 17:32:36 2005
 99.60% done, estimate finish Tue Dec  6 17:32:36 2005
 99.71% done, estimate finish Tue Dec  6 17:32:37 2005
 99.81% done, estimate finish Tue Dec  6 17:32:36 2005
 99.92% done, estimate finish Tue Dec  6 17:32:36 2005
Total translation table size: 0
Total rockridge attributes bytes: 18990
Total directory bytes: 55296
Path table size(bytes): 380
Max brk space used 42000
478405 extents written (934 MB)
/dev/sr0: flushing cache


Hmmm?  I'm assuming it's something to do with cdrecord as that seems to be giving me the real problems.  Balls back in your court :)

---

