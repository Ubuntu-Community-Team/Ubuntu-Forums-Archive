---
title: "Mounting blank CD error"
date: 2009-12-19
forum: Hardware
---

### Post by Skinny-Mini on 2009-12-19
Sometimes, if I enter a blank CD (80 min, 700 MB) into my drive for burning, it'd either:

1) Freeze every 20 minutes or so.
2) Read it but not burn.
3) Do nothing,

It'd been a pain in the butt, and I really want to burn an ISO someone gave me. 

Help, pl0x?

---

### Post by jerrrys on 2009-12-20
is this windows your using?  what program are you burning with?  and what was the error code?

---

### Post by Skinny-Mini on 2009-12-20
> **jerrrys said:**
> is this windows your using?  what program are you burning with?  and what was the error code?

No, Ubuntu.
I've tried Brasero, K3B, and GnomeBaker.
I don't remember..?

I accidentally deleted the ISO and I have to re-download it after I get it again...

---

### Post by jerrrys on 2009-12-20
the error code is needed.  recreate the error and post the error code please

---

### Post by Skinny-Mini on 2009-12-28
> **jerrrys said:**
> the error code is needed.  recreate the error and post the error code please

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD+-RW GWA4164B'
Revision       : 'D108'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0E 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
wodim: No disk / Wrong disk!
```

Not the same file but it looks like the same error code (GnomeBaker).

---

