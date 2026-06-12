---
title: "EEEK!! I have a horrible feeling this means a dying HD"
date: 2010-11-08
forum: Hardware
---

### Post by ankara on 2010-11-08
Ubuntu-10 kernel: [21963.855328] ata4.00: exception Emask 0x10 SAct 0x1 SErr 0x1c00000 action 0x6 frozen
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855333] ata4.00: irq_stat 0x08000000, interface fatal error
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855337] ata4: SError: { Handshk LinkSeq TrStaTrns }
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855341] ata4.00: failed command: READ FPDMA QUEUED
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855347] ata4.00: cmd 60/08:00:ff:7c:c5/00:00:4a:00:00/40 tag 0 ncq 4096 in
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855348]          res 40/00:04:f7:7c:c5/00:00:4a:00:00/40 Emask 0x10 (ATA bus error)
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855351] ata4.00: status: { DRDY }
Nov  8 22:53:03 Ubuntu-10 kernel: [21963.855356] ata4: hard resetting link
Nov  8 22:53:04 Ubuntu-10 kernel: [21964.381330] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  8 22:53:04 Ubuntu-10 kernel: [21964.386414] ata4.00: configured for UDMA/33
Nov  8 22:53:04 Ubuntu-10 kernel: [21964.386446] ata4: EH complete
Nov  8 22:53:12 Ubuntu-10 kernel: [21972.803710] nautilus[4967]: segfault at 16c800a ip 00007f4cf9a0522b sp 00007f4cefffea20 error 4 in libbrasero-media.so.0.2.0[7f4cf99f2000+24000]

anyone know what all this means?
edit: this drive will only mount in read only mode btw /edit
thanks in advance

---

