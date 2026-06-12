---
title: "Can't mount cd-rw or burn cd's"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by Cysman on 2006-02-21
Hi folks, I'm real sorry about posting such a highly posted topic, but I've read many posts about this and I can't find anything that seems to help me.  I can't burn a cd.  

When I try to mount the cdrw, this is what I get:

Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount


When I try to run Gnomebaker, this is what I get when trying to burn:

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
scsidev: '/dev/hdc'
devname: '/dev/hdc'
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

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PHILIPS '
Identifikation : 'CDD4851 CD-R/RW '
Revision       : 'C3.7'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
Drive buf size : 3244032 = 3168 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data    74 MB         padsize:   30 KB
Total size:       85 MB (08:30.98) = 38324 sectors
Lout start:       86 MB (08:32/74) = 38324 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is unrestricted
  Is erasable
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  8 2T speed high:  0 (reserved val 10)
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 4A C8 36
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 321525
Starting to write CD/DVD at speed 2 in real TAO mode for multi session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of   74 MB written.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 13 00 00 00 00 63 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x63 Qual 0x00 (end of user area encountered on this track) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 0.015s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   10.017s
Average write speed  97.3x.
Fixating...
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 13 00 00 00 00 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.015s timeout 480s
cmd finished after 0.015s timeout 480s
Fixating time:    0.045s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.


And then when I try and use sudo, this is what I get:

cysmanken@ubuntuhome:~$ sudo gnomebaker
Password:

(gnomebaker:15864): Gtk-WARNING **: gtkwidget.c:4205: widget not within a GtkWindow

** (gnomebaker:15864): WARNING **: Stat of file [/root/socket-ubuntuhome] failed
** (gnomebaker:15864): WARNING **: Stat of file [/root/tmp-ubuntuhome] failed

** (gnomebaker:15864): WARNING **: Stat of file [/root/socket-ubuntuhome] failed
** (gnomebaker:15864): WARNING **: Stat of file [/root/tmp-ubuntuhome] failed


cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
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
Response Format: 1
Vendor_info    : 'PHILIPS '
Identifikation : 'CDD4851 CD-R/RW '
Revision       : 'C3.7'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
Drive buf size : 3244032 = 3168 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data    74 MB         padsize:   30 KB
Total size:       85 MB (08:30.98) = 38324 sectors
Lout start:       86 MB (08:32/74) = 38324 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is unrestricted
  Is erasable
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  8 2T speed high:  0 (reserved val 10)
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 4A C8 36
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 321525
Starting to write CD/DVD at speed 2 in real TAO mode for multi session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of   74 MB written.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 13 00 00 00 00 63 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x63 Qual 0x00 (end of user area encountered on this track) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 0.007s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   16.120s
Average write speed  97.6x.
Fixating...
Fixating time:    0.003s
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 13 00 00 00 00 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 480s
cmd finished after 0.001s timeout 480s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

Does anyone have any idea?  Am I stuck with an operating system that won't allow me to burn cd's?[-(

---

### Post by akiro.yamamoto on 2006-02-21
Your fstab should look like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by akiro.yamamoto on 2006-02-21
When you insert a blank, it should be mounted automatically.
You don't need Write access to it. 
Tell me the error you recieve...step by step.

---

### Post by Cysman on 2006-02-21
[QUOTE=akiro.yamamoto]When you insert a blank, it should be mounted automatically.
You don't need Write access to it. 
Tell me the error you recieve...step by step.[/QUOTE]

Ok, when I put in a blank cdrw, it auto mounts.  I then used the popup screen that gives the option to burn an audio, data, or photo cd.  I selected a picture cd.  I dragged some mpeg files to the blank cdrw and it first "erased" the cdrw and then went throught the process and stated the burn was complete but when I re-inserted the cdrw back into the tray, it's empty although when you look at the surface of the disk itself, you can see data burned. ???

---

### Post by Cysman on 2006-02-21
[QUOTE=akiro.yamamoto]Your fstab should look like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/QUOTE]

Ah.....er, ahem, where do I find that?:-k

Oh wait, I found it.  Yup, that's what it looks like.

---

### Post by akiro.yamamoto on 2006-03-02
Do you get the same problems for Audio CDs?
This is the strangest thing I've ever heard of!

---

### Post by nin82 on 2006-10-24
mine wont mount at all with blank cds or dvds and not even gnomebaker will work. so basicly i cant burn any thing at all. oh and besides my normal cds dont appear on the desktop i have to got to compuer>tCdrom1> and click it then it will appear on the desktop

---

### Post by nikoli on 2007-02-25
> **nin82 said:**
> mine wont mount at all with blank cds or dvds and not even gnomebaker will work. so basicly i cant burn any thing at all. oh and besides my normal cds dont appear on the desktop i have to got to compuer>tCdrom1> and click it then it will appear on the desktop

Every burning application I've tried tells me to "insert a blank CD". The only exception is k3b which fails every time about 20 seconds after burning the starts.

---

