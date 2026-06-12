---
title: "Can't burn CDs"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by computerdude33 on 2005-05-13
I can't burn CDs anymore.

My CD-R Drive is a Plextor PlexWriter.
I'm running Ubuntu on a Pentium 4.

I was able to write to CDs before.

Any help?

(I was trying to burn an ISO- I tried another ISO, didn't work)

---

### Post by Sam on 2005-05-13
Did you try to burn an ISO you already burned successfully ? Maybe your ISO file is broken.

---

### Post by computerdude33 on 2005-05-13
I've tried burning 5.04 Install CD and Mandriva LE2005 Mini.

---

### Post by Maestro23 on 2005-05-13
[QUOTE=computerdude33]I can't burn CDs anymore.

My CD-R Drive is a Plextor PlexWriter.
I'm running Ubuntu on a Pentium 4.

I was able to write to CDs before.

Any help?

(I was trying to burn an ISO- I tried another ISO, didn't work)[/QUOTE]

What OS/program are you using to burn Iso's? Did the Iso pass the checksum? You were able to burn CDs before? Before what?  Just trying to help ya, need more info.. ;)

---

### Post by nad on 2005-05-13
What software/upgrades have you installed since you were 'able to write to CDs before'?

Have you read your logs for error messages?

Perhaps if you configure some options, Gconf->apps->nautilus-cdburner, you will regain the ability to write.

---

### Post by computerdude33 on 2005-05-13
I'm running Ubuntu 5.04. I'm using the default ISO burner. When I try to burn a CD, it says I don't have enough space on the disc, even though I know it has 0 bytes of info on it. (I looked at them on other computers)

---

### Post by Segovia on 2005-05-13
[QUOTE=computerdude33]I'm running Ubuntu 5.04. I'm using the default ISO burner.[/QUOTE]
I didn't even know Ubuntu has a default CD burner than can do ISOs.  I always use Gnomebaker for those.

---

### Post by Sam on 2005-05-13
Try to mount your iso file:
```
$ sudo mount -o loop -t iso9660 <filename>.iso /mnt/iso
```([nautilus script](http://www.ubuntuforums.org/showthread.php?t=33881) for doing this simplier)

If it don't work you iso file is corrupted.

---

### Post by luvdemheels on 2005-05-13
I have a similar problem. Tried burning an iso with gnomebaker and it failed. Turned around and burned the same iso with windows xp and sonic with no problem. Makes me so mad when I can do something in xp and not linux.  I want this stuff to work in linux.

---

### Post by lett on 2005-05-14
hello,

like luvdemheels I use GnomeBaker and I can't burn any cd's. I turned on dma for cd-rw - no result. 

# cdrecord -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by lett on 2005-05-14
Print out from GnomeBaker:

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using
setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1
'@(#)scsitransp.c        1.91 04/06/17 Copyright 1988,1995,2000-2004 J.
Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg
Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of
cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to
<cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this
version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'CD-RW GCE-8524B '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009
Profile: 0x0008
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1658880 = 1620 KB
Drive DMA Speed: 4695 kB/s 26x CD 3x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using
setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data    47 MB
Total size:       54 MB (05:25.72) = 24429 sectors
Lout start:       55 MB (05:27/54) = 24429 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11625 (97:27/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 0
Manufacturer: Illegal Manufacturer code
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 335420
Starting to write CD/DVD at speed 10 in real SAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.   1
seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x4 (CONDITION MET/GOOD)
cmd finished after 232.286s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1839 K BSize: 1860 K
Starting new track at sector: 0

Track 01:    0 of   47 MB written.cdrecord: Success. write_g1: scsi
sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x00 (logical block address out of range) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.002s timeout 200s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
cdrecord: Please report.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set
up.

write track data: error after 0 bytes
Writing  time:  237.317s
Average write speed   1.4x.
Fixating...
cdrecord: faio_wait_on_buffer for writer timed out.
cdrecord: Success. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 09 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x09 (write error - loss of streaming) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 151.344s timeout 200s
Trouble flushing the cache
Fixating time:  151.520s
Track 01: data    47 MB
Total size:       54 MB (05:25.72) = 24429 sectors
Lout start:       55 MB (05:27/54) = 24429 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11625 (97:27/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 0
Manufacturer: Illegal Manufacturer code
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 335420
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

---

### Post by ducko on 2005-05-14
Hello fellow human beings!

There has been many posts concerning GnomeBaker and CD burning difficulties. The usual problem seems to produce the same error message just as 'lett' earlier posted. Could someone help us and specify what is possible cause of this or should I turn to GnomeBaker developers. This particular problem seems to be increasing AFAIK?

Most of the queries I've made to these forums about this problem deals with this specific error message.

-ducko

---

### Post by Dogmeat on 2005-05-14
i have the same problem with GnomeBaker, it says the cd not mounted and gives those errors if I proceed. What i did was get xcdroast, it's the only cd-rom burning app that worked for me so far on Ubuntu. To get it, just

```
sudo apt-get install xcdroast
```

---

### Post by lett on 2005-05-14
It's definitely not the question of app, i'm quite sure that the problem is somewhere else. For everybody who have problem: in terminal:

cdrecord -scanbus

if you will get something like this:

Cdrecord-Clone 2.01a19 (i686-pc-linux-gnu) Copyright (C) 1995-2003 Jörg Schilling
Linux sg driver version: 3.5.29
Using libscg version 'schily-0.7'
scsibus0:
        0,0,0     0) 'HL-DT-ST' 'RW/DVD GCC-4241N' '0C29' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

you're ok, if not - well...

---

### Post by atezun on 2005-05-15
[QUOTE=computerdude33]I'm running Ubuntu 5.04. I'm using the default ISO burner. When I try to burn a CD, it says I don't have enough space on the disc, even though I know it has 0 bytes of info on it. (I looked at them on other computers)[/QUOTE]

I had the same problem what i did was go to

```
Applications -> System Tools -> Configuration Editor

apps -> nautilus-cd-burner -> overburn -> (checked)

and

apps -> nautilus-cd-burner -> default_speed -> (any supported burn speed example: 4)
```

Hope this helps

---

### Post by uncasamus on 2005-07-29
[QUOTE=atezun]I had the same problem what i did was go to

```
Applications -> System Tools -> Configuration Editor

apps -> nautilus-cd-burner -> overburn -> (checked)

and

apps -> nautilus-cd-burner -> default_speed -> (any supported burn speed example: 4)
```

Hope this helps[/QUOTE]
 **This did the trick!**
Thanks very much!

The problem I had was essentially the same - a requester kept coming up asking me to insert a disk with enough free space (511 MB) for what I was trying to write to CD, even though I inserted several TDK-brand blank CD-R's.

Sam

---

### Post by uncasamus on 2005-07-29
**It is the overburn setting that mattered.** 
I reset the default_speed to "0" and the burn proceeded fine, though I think slower than when I specified "4".

Sam


[QUOTE=atezun]I had the same problem what i did was go to

```
Applications -> System Tools -> Configuration Editor

apps -> nautilus-cd-burner -> overburn -> (checked)

and

apps -> nautilus-cd-burner -> default_speed -> (any supported burn speed example: 4)
```

Hope this helps[/QUOTE]

---

### Post by PhilOSparta on 2005-08-25
Great fix.  This ought to be in the FAQ lists.
After going down many dead ends, this worked for me.
Who would have thought to go to the configuration screen?

Some said it was a kernel problem.
Others said you had to activate SCSI emulation, etc.

Thanks for your efforts.

---

### Post by sumadartson on 2005-09-05
Hi,

There definitely seems to be something wrong here. I'm using good old cdrecord and getting the following output

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PLEXTOR '
Identifikation : 'CD-R   PX-W8432T'
Revision       : '1.09'
Device seems to be: Generic CD-ROM.
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   :
Supported modes:
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.

```

I do get the message from cdrecord about the kernel mismatch, but for the rest it seems that, for some reason, my ancient plextor isn't recognized as a recorder. Weird...  :-| 

Does anybody recognize this problem? Or am I overlooking something trivial?

Edit : Oddly enough reinstalling cdrecord from restricted has fixed the problem. Strange. I don't see a version difference.

---

### Post by charon79m on 2005-10-09
Great fix.... worked for me too.

I had to define the temp directory for the disk ISO.  


Thanks!

MrKnisely

---

