---
title: "Long boot times caused by sata_sil. Please help"
date: 2008-09-17
forum: Hardware
---

### Post by spooner on 2008-09-17
During boot my laptop pauses for 30 seconds (2*3*5 seconds) whilst waiting for ata devices to identify.
```

scsi0 : sata_sil
scsi1 : sata_sil
ata1: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc0004080 irq 22
ata2: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc00040c0 irq 22
ata1: SATA link upto 1.5 Gbps (SStatus 113 SControl 310)
ata1.00: failed to recover some devices, retrying in 5 sec

```
The last 2 lines are then repeated twice for ata1 and the 3 more for ata2.

The hardware in the laptop (Acer Aspire 3050 something or other) is AMD 3400 Semperon 64, 1.5Gb DDRII Ram, Samsung IDE 120 Gb HDD, Acer/ATI Bowfin motherboard. It is running 64bit ubuntu 7.10, kernel 2.6.24-19.41 x86_64, cli+kde-core. As the HDD is IDE I have no idea why sata drivers are being loaded.

Does anyone know how to disable the sata drivers as I don't know what they are doing? And well if this breaks something at least I will know what the problem is. Please help as wait 30 seconds at boot time for something that doesn't exist is starting to irritate.

Cheers
Spooner

---

### Post by spooner on 2008-09-18
Ok here is a copy of dmesg if anyone can see anything else or a cause that would be appricated...
I have removed the authenication of my wlan0...

---

