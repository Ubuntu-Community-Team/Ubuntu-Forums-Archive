---
title: "cdrecord - burning problem"
date: 2008-08-17
forum: General Help
---

### Post by satimis on 2008-08-17
Hi folks,


Ubuntu 8.04 desktop amd64
SATA Sony DVD burner

cdrecord -version```

Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.6

```

On running;

$ cdrecord -scanbus```

scsibus5:
	5,0,0	500) 'SONY    ' 'DVD RW AW-G170S ' '1.72' Removable CD-ROM
	5,1,0	501) *
	5,2,0	502) *
	5,3,0	503) *
	5,4,0	504) *
	5,5,0	505) *

```


$ cdrecord -v -eject -tao dev=5,0,0 /path/to/ubuntu-8.04.1-desktop-i386.iso```

TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '5,0,0'
scsibus: 5 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.

```

$ wodim -v -checkdrive dev=/dev/scd0```

TOC Type: 1 = CD-ROM
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW AW-G170S '
Revision       : '1.72'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) (current)
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.

```

Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by dfmalh on 2008-08-27
Hi 'satimis',

Did you resolve your problem? I am also having the same problems that you are experencing...

My *cdrecord -version* output:

```
Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.6
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling

```

My *cdrecord --scanbus* output:

```
scsibus1:
	1,0,0	100) 'Slimtype' 'DVDRW SOSW-852S ' 'PRS9' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
```

I get exactly the same outputs when I run *wodim -version* and *wodim --scanbus*.

I have no idea how to fix this problem. I tried diffent burners and they all give the same result, burned the CD, but afterwards although it looks like something is on the CD, it says empty.

Now when I insert a DVD into my drive it locks up, keeps spinning, and the only way to remove it, is to "hard" power on/off. 

This all started happening after a fresh install of Hardy, everything was working perfectly in Feisty. :lolflag:

---

