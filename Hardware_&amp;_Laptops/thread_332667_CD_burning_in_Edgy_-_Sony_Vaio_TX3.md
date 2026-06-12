---
title: "CD burning in Edgy - Sony Vaio TX3"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by tomranson on 2007-01-06
Hi all,

I am having CD burning issues on my Sony VAIO TX3XP running Ubuntu Edgy 6.10 (2.6.17-10-generic).

I have successfully used the internal CD/DVD burner under Ubuntu 6.06 for many months, and have burned created many CD's and DVD's. The drive in question is a Matshita UJ-842D,

Having upgraded to 6.10 (both via dist-upgrade, and now a totally new install) I am unable to burn CD's via the same internal burner.

Simply trying to write an ISO file to CD via the built in Ubuntu CD/DVD writer software (which I believe uses cdrecord) returns a generic error as soon as writing starts:

**"There was an error writing to the disc. Error while writing to disc. Try a lower speed".**

So, I try cdrecord from the command line, so I get get more verbose output.

**cdrecord -v -pad speed=1 dev=/dev/hdb ubuntu-6.06.1-server-i386.iso**

And I get....

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-842D         '
Revision       : '1.20'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   432 MB         padsize:   30 KB
Total size:      496 MB (49:10.30) = 221273 sectors
Lout start:      496 MB (49:12/23) = 221273 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 138576
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Starting to write CD/DVD at speed 4 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 81 01 09 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x01 (tracking servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.886s timeout 60s
cdrecord: OPC failed.
Writing  time:    1.910s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

The same happens when I run the above command via sudo (wanted to prove it wasn't something that silly).

I've researched the various error messages returned for days with no avail. 

Please can someone help?

Many thanks,

Tom

---

### Post by DagMan on 2007-01-06
I don't know if this is of the same nature, but I've had problems burning and I had to chmod the write permission to the device.  I would imagine that this would mean any symlink that the process is using as well as whatever the device is that's being pointed to.  It was straitforward on mine as to what needed to be done.  It's something to look at if nothing else.

I also had a problem with some functions of the drive and had to modprobe ide-cd although it's not something that is relating in the same way to your issue.

---

### Post by tomranson on 2007-01-08
That sounds like its worth a go... what exactly did you change on your setup?

---

### Post by DagMan on 2007-01-08
I used gnomebaker and it specified the device in the output in the part that can expand and show a little output when the progrss bar is showing.  Then at a terminal I did 
sudo chmod 666 /dev/device-goes/here
So for example on my machine it was sudo chmod 666 /dev/sg0

I would have thought that to find the device I would just type ls -l /dev/cdrom or ls -l /dev/dvd and it would have a pointer to where it's going, but in my case this isn't the problem as they both point at scd0 which is /dev/scd0 and this wasn't what was needed.
If you use gnomebaker and expand the view to see what is happening, it will likely specify a device IF this is actually the problem.  It will look like /dev/something and if that's the case then do
sudo chmod 666 /dev/something
replacing 'something' for whatever you see in the output.

If you work it out and get it going... if this is indeed the problem and you get an accurate report of what needs to have the file permissions changed and you do so and it works, then post here again if you don't know how to add it to a startup script.  The sudoers file has to be edited to allow it to run without typing in a password.  I'll try to remember to come back in case someone else doesn't help... it was a real coincidence that I remembered I'de posted here and that we came online at almost the same time.

---

### Post by tomranson on 2007-01-13
Guess what.... I think its the bl***y media thats been the problem all along. 

It would kind of explain the "servo tracking error"... watch this space for a conclusive answer.

---

