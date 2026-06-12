---
title: "CD-Drive error"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by kimusabi on 2007-10-22
[i] Heyo, having abit of trouble with my COMBO-52X16C on Feisty (7.04). It seems to read DVDs, Installation and Game CDs perfectly. But when I put in a blank it fails to mount and doesn't recognize the CD.

Quite annoying because I was planning on making copies of a music video I put together :(

Any help would be lovely.

/Kim [/i]

---

### Post by kimusabi on 2007-10-22
Bump.

---

### Post by kimusabi on 2007-10-23
Bumpity?

---

### Post by Linicks on 2007-10-23
You don't mount a blank CD for burning... once you burn the files to it, the burning software 'fixates' it so that it has a recognisable FS the system can read.

Just plonk the disk in and burn straight to the device.

Nick

---

### Post by kimusabi on 2007-10-23
[i] Probably should have been more clear when first writing this. But the thing is, Ubuntu doesn't see the blank CD, so it can't write to the blank CD.

/Sen [/i]

---

### Post by Linicks on 2007-10-23
Nothing will see a CD that is not yet created.

Can you show the error message the burning software (what do you use?) produces?

Nick

---

### Post by kimusabi on 2007-10-23
[i]Sorry for the long reply, been abit busy.
GNOMEBaker Output
```
 wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : '        '
Identification : 'COMBO-52X16C    '
Revision       : '1.83'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0008 (CD-ROM)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) (current)
Profile: 0x0002 (Removable disk) 
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1951488 = 1905 KB
FIFO size      : 12582912 = 12288 KB
Errno: 0 (Success), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.004s timeout 40s
wodim: No disk / Wrong disk!

```

K3B doesn't seem to want to produce an error report. Neither does CDControl 

/Sen[/i]

---

