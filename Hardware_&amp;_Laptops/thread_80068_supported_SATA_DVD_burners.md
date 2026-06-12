---
title: "supported SATA DVD burners?"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by jamieson on 2005-10-21
I'm considering buying a new DVD burner and thinking about getting one of the SATA models (Plextor FX-716SA).  My Soyo motherboard has a VIA 8237 SATA controller on it and that's been working fine with my Seagate SATA hard drive.

Does anyone know of compatibility issues with breezy, VT8237 and SATA DVD drives?   I'm seeing lots of conflicting info on which chipsets work with which DVDs...

---

### Post by Kyral on 2005-10-21
I dunno about the Drive itself, but if the VIA controller works (They do very nicely, I have one on my ASUS A7V600-X) then it SHOULD work.

I've never tried a SATA burner myself...

---

### Post by jamieson on 2005-11-04
Seems like SATA DVD/CDROM drives just aren't supported well, or at all... yet.

My Plextor SATA DVD drive isn't detected.  Looking at /var/log/dmesg I see that it's trying to find the SATA devices, and it does find my SATA hard drive but the DVD drive (ata2?) seems to timeout:


ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 20
[4294673.753000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 20
[4294674.108000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01  87:4023 88:407f
[4294674.108000] ata1: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
[4294674.108000] ata1: dev 0 configured for UDMA/133
[4294674.108000] scsi0 : sata_via
[4294674.614000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000  87:0000 88:101f
[4294674.614000] ata2: dev 0 ATAPI, max UDMA/66
[4294674.614000] ata2(0): applying bridge limits
[4294674.614000] ata2: dev 0 configured for UDMA/66
[4294674.614000] scsi1 : sata_via
[4294674.614000]   Vendor: ATA       Model: ST3250823AS       Rev: 3.03
[4294674.614000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294680.114000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x1

---

### Post by ookadoo on 2007-10-18
> **jamieson said:**
> Seems like SATA DVD/CDROM drives just aren't supported well, or at all... yet.

My Plextor SATA DVD drive isn't detected.  Looking at /var/log/dmesg I see that it's trying to find the SATA devices, and it does find my SATA hard drive but the DVD drive (ata2?) seems to timeout:


ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 20
[4294673.753000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 20
[4294674.108000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01  87:4023 88:407f
[4294674.108000] ata1: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
[4294674.108000] ata1: dev 0 configured for UDMA/133
[4294674.108000] scsi0 : sata_via
[4294674.614000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000  87:0000 88:101f
[4294674.614000] ata2: dev 0 ATAPI, max UDMA/66
[4294674.614000] ata2(0): applying bridge limits
[4294674.614000] ata2: dev 0 configured for UDMA/66
[4294674.614000] scsi1 : sata_via
[4294674.614000]   Vendor: ATA       Model: ST3250823AS       Rev: 3.03
[4294674.614000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294680.114000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x1

Is this still a problem?  I'm considering getting a SATA burner but not if it's not supported

---

