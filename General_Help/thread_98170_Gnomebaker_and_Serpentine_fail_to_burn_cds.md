---
title: "Gnomebaker and Serpentine fail to burn cds"
date: 2005-12-02
forum: General Help
---

### Post by cowlip on 2005-12-02
Hi, I have trouble burning cds in Ubuntu. In Gnomebaker it stopped right away, but Serpentine managed to burn 6 songs out of 18 I wanted to burn. Also, I followed this thread before ( [http://ubuntuforums.org/showthread.php?t=30596&highlight=cdrecord+suid+root](http://ubuntuforums.org/showthread.php?t=30596&highlight=cdrecord+suid+root) )and stopped dbus, but now even that doesn't work.  Serpentine then tells me to insert a blank cd even if I have a blank cd in.

Here is the error log from gnomebaker:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX140E  '
Revision       : '1.0p'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 1843 kB/s 10x CD 1x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: WARNING: Data may not fit on current disk.
cdrecord: Notice: Use -overburn option to write more than the official disk capacity.
cdrecord: Notice: Most CD-writers do overburning only on SAO or RAW mode.
pregap1: -1
Track 01: audio   24 MB (02:26.82) no preemp     
Track 02: audio   47 MB (04:42.13) no preemp     
Track 03: audio   44 MB (04:22.25) no preemp     
Track 04: audio    8 MB (00:49.12) no preemp     
Track 05: audio   43 MB (04:19.18) no preemp     
Track 06: audio   77 MB (07:43.60) no preemp     
Track 07: audio   10 MB (01:04.38) no preemp     
Track 08: audio   52 MB (05:12.37) no preemp     
Track 09: audio    8 MB (00:48.85) no preemp     
Track 10: audio   61 MB (06:08.50) no preemp     
Track 11: audio   39 MB (03:53.12) no preemp     
Track 12: audio   32 MB (03:11.36) no preemp     
Track 13: audio   68 MB (06:46.85) no preemp     
Track 14: audio   40 MB (03:58.90) no preemp     
Track 15: audio   68 MB (06:49.37) no preemp     
Track 16: audio   40 MB (04:03.24) no preemp     
Track 17: audio   21 MB (02:08.13) no preemp     
Track 18: audio   22 MB (02:16.53) no preemp     
Track 19: audio   36 MB (03:34.22) no preemp     
Track 20: audio   55 MB (05:28.98) no preemp     
Total size:      811 MB (80:25.97) = 361948 sectors
Lout start:      812 MB (80:27/73) = 361948 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -11740 (97:25/35)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: -2099

---

### Post by cowlip on 2005-12-03
no one? :(

---

### Post by shadowhunter on 2005-12-12
might work with

sudo dpkg-reconfigure cdrecord

and select the suid root...

Geert...

Or use in sudo.

---

### Post by az on 2005-12-12
"Total size: 811 MB (80:25.97) = 361948 sectors
Lout start: 812 MB (80:27/73) = 361948 sectors"

There is only 700MB of room on a cd.

Other than that, the other messages are normal cdrecord output messages.

---

### Post by cowlip on 2005-12-17
Hmmm I see thank you azz & shadowhunter.  Sorry for not responding earlier.  The only thing I is that I thought the data size doesn't matter for audio cds, because it counts in minutes.  This is supposed an 80 minute cd on the label

---

### Post by Ocxic on 2005-12-17
make sure your putting you music files in the AUDIO tab and not the DATA tab in GnomeBaker

---

### Post by cowlip on 2005-12-23
Yes I think I did that.  However because it happens in both serpentine an dngomebaker I think it's something common to them.


The only thing is that it's hard to replicate this because I don't particularily want to end up wit more coasters ;)  Is there anyway to test it, since I'm on Dapper and bugs could ahve been fixed, without that outcome.

---

### Post by mikeymouse on 2005-12-23
Hi: I had the same problem with gnomebaker, it would copy a cd but not create a new one.. I found the best was was to install K3B. I even had  trouble with that but I copied the cd and then as a separate process burned a cd.. it was a 2 step affair but it works
Hope this helps
 MIkeymouse.

---

### Post by cowlip on 2006-01-14
I just tried Dapper and it appears serpentine is working normally if I untick "add 2 second gap" in preferences.  I don't know if it works otherwise because I don't want more coasters :P but I'm happy with this

---

