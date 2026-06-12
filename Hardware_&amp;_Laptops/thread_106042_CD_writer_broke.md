---
title: "CD writer broke?"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by Olav on 2005-12-19
Hi, since a few days my CD writer won't write, well, CDs. If I try to burn an ISO image through Nautilus, it will start cdrecord but after a minute or so it returns with the message:

[INDENT]**Reload a rewritable or blank disc**
Please replace the disc in the drive with a CD-R/CD-RW, with at least 696 MiB free.[/INDENT]

When I try 

```
root@dinges:~# cdrecord -v -dev=/dev/hdc -driveropts=burnfree /home/olav/av.iso
```

I get this:

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

cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'MITSUMI '
Identifikation : 'CR-48XFTE       '
Revision       : '4.0B'
Device seems to be: Philips CDD-522.
Current: 0x0009
Profile: 0x0008
Profile: 0x0009 (current)
Profile: 0x000A
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1441792 = 1408 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   695 MB
Total size:      799 MB (79:10.88) = 356316 sectors
Lout start:      799 MB (79:12/66) = 356316 sectors
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
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 3533
Starting to write CD/DVD at speed 54 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  695 MB written.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.001s timeout 40s

write track data: error after 0 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
Writing  time:    5.024s
Average write speed 948.3x.
Fixating...
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 480s
cmd finished after 0.000s timeout 480s
cdrecord: Cannot fixate disk.
Fixating time:    0.002s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
```

The interesting bit seems to be:

[INDENT][B]Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)[/B][/INDENT]

.. but I don't know what it means.

How do I check if my CD writer went to heaven, or wether something is wrong with software?

---

### Post by Olav on 2005-12-21
OK, got it. Lacking diagnostic tools, I tried the drive in someone else's (Windows) computer. It didn't burn anything there, and now it doesn't read anything anymore, too. So I witnessed the gradual breakdown of a CD burner...

Just too bad that the cdrecord messages could not be clearer about it, but I won't nag :p.

So I'm about to buy another one. Would you say [[COLOR="Blue"]this LG[/COLOR]]("http://www.lge.nl/prodmodeldetail.do?actType=search&page=1&modelCategoryId=0502&categoryId=0502&parentId=05&modelCodeDisplay=GSA-4167B&model=3") (cheapest that also burns DVDs) would be OK?

---

