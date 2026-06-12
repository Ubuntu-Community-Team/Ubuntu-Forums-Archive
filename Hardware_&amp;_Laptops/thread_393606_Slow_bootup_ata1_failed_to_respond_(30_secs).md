---
title: "Slow bootup: ata1 failed to respond (30 secs)"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by vafada on 2007-03-25
i tired both Xubuntu and Ubuntu Ultimate edition 1.3 and booting takes around 2 minutes. I checked the logs using "dmesg" and found this:

[17179581.280000] ata1: SATA max UDMA/133 cmd 0xF8842100 ctl 0x0 bmdma 0x0 irq 169
[17179581.280000] ata2: SATA max UDMA/133 cmd 0xF8842180 ctl 0x0 bmdma 0x0 irq 169
[17179581.280000] ata3: SATA max UDMA/133 cmd 0xF8842200 ctl 0x0 bmdma 0x0 irq 169
[17179581.280000] ata4: SATA max UDMA/133 cmd 0xF8842280 ctl 0x0 bmdma 0x0 irq 169
[17179588.484000] ata1 is slow to respond, please be patient
[17179611.500000] ata1 failed to respond (30 secs)
[17179619.216000] ata1 is slow to respond, please be patient
[17179642.232000] ata1 failed to respond (30 secs)
[17179642.232000] ata1: reset failed (errno=-5)
[17179642.232000] scsi0 : ahci
[17179642.436000] ata2: SATA link down (SStatus 0)
[17179642.436000] scsi1 : ahci
[17179642.640000] ata3: SATA link down (SStatus 0)
[17179642.640000] scsi2 : ahci
[17179642.844000] ata4: SATA link down (SStatus 0)
[17179642.844000] scsi3 : ahci
[17179642.904000] Probing IDE interface ide1...

it seems that kernel is taking around a minutes (two 30 secs timeout ) just to load ata1 and ends up failing. Can i just disable ata1 loading?

---

