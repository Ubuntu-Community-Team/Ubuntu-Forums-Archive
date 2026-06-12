---
title: "Need help fixating (or fixing) a badly burned DVD-RW"
date: 2013-05-12
forum: Hardware
---

### Post by OrangeVixen on 2013-05-12
I have a DVD-RW mini disc (the kinds used for Camcorders) that was badly recorded (by the Camcorder, I think).

When I put it into my DVD drive on my Linux box I get a blank disc dialog.

I think the disc was not fixated properly, but I am not sure, however I tried to fix it ate with:

```

$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg0'	rwrw-- : 'TSSTcorp' 'CDDVDW SH-S223B'
-------------------------------------------------------------------------

```

Then:

```

$ sudo wodim -v -fix -force "dev=/dev/sg0"
TOC Type: 1 = CD-ROM
scsidev: '/dev/sg0'
devname: '/dev/sg0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.34
Wodim version: 1.1.11
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S223B '
Revision       : 'SB02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) (current)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1376256 = 1344 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Speed set to 2770 KB/s
Starting to write CD/DVD at speed   2.0 in real force unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
wodim: Cannot open new session.

```

I'm not really sure what else I can do try to recover the disc's data, if anyone has any ideas on recovering DVD-RWs that were burned badly please let me know.

---

