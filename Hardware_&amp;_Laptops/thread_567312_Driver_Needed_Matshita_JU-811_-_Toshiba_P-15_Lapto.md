---
title: "Driver Needed Matshita JU-811 - Toshiba P-15 Laptop"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by rhardie on 2007-10-04
My DVD burner doesn't work on my Toshiba laptop - actually, it hasn't since Windows SP2.  I suspect it is a driver issue and this model of optical drive is famous for having problems.

Any suggestions on finding a driver for the Matshita UJ-811 optical drive?  I've googled with no results.

---

### Post by likemindead on 2007-10-10
Same problem here. I have a MATSHITA UJ-811 DVD-RAM in my Thinkpad and cannot burn anything!!! Here's the error I get in GnomeBaker:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-811  '
Revision       : 'H102'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1343488 = 1312 KB
FIFO size      : 12582912 = 12288 KB
locks total: 359846 Blocks current: 359846 Blocks remaining: 175217
Starting to write CD/DVD at speed   8.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.Speed set to 1411 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 32 00 10 03 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x03 Qual 0x00 (peripheral device write fault) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 11.302s timeout 60s
wodim: OPC failed.
Writing  time:   15.028s
BURN-Free was never needed.

```

Please help?! :confused:

---

### Post by rhardie on 2007-11-02
My Matshita optical drive works perfectly upon upgrading to Ubuntu V 7.10!

This is the first time my drive has been operational and RELIABLE in two years!  YAHOOOOO! It's PARTY TIME!

---

### Post by likemindead on 2007-11-02
Oh, wow, I need to try mine!

:?:

---

