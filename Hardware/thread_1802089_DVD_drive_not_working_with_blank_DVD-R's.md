---
title: "DVD drive not working with blank DVD-R's"
date: 2011-07-11
forum: Hardware
---

### Post by painejake on 2011-07-11
Hi there!

Seem to be having an issue with blank DVD and CD-R's. Ubuntu doesn't pick them up nor do they show in K3b or Brasero. I have tried force mounting and the drive just seems to spin up then do nothing.

wodim returns:

```
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDRWDVD TS-H493B'
Revision       : 'D200'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
```

wodim: No write mode specified. - Maybe a failing drive? It burns fine under Windows 7.

Thanks!

---

