---
title: "ATA bus error"
date: 2011-01-17
forum: Hardware
---

### Post by davidhoenig on 2011-01-17
Every once in a while it feels like accesses to my boot hard disk (~1yr old 32GB SSD) get reallllly slow. I'm doing some debug and trying to figure out if I might have a hardware problem/bad disk. Here's what I see:

During boot, dmesg shows these messages, at three separate times:


[    4.164797] ata7.00: exception Emask 0x10 SAct 0x1 SErr 0x780100 action 0x6
[    4.164800] ata7.00: irq_stat 0x08000000
[    4.164802] ata7: SError: { UnrecovData 10B8B Dispar BadCRC Handshk }
[    4.164804] ata7.00: failed command: READ FPDMA QUEUED
[    4.164807] ata7.00: cmd 60/08:00:10:09:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[    4.164808]          res 40/00:04:10:09:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[    4.164809] ata7.00: status: { DRDY }
[    4.164812] ata7: hard resetting link


Neither 'fsck' nor smartmontools report any problems. Can anyone tell me if the above messages definitely indicate a hardware problem?

---

### Post by davidhoenig on 2011-01-17
Just for a second data point, here is another time that the error occurs:


[  190.005725] ata7: limiting SATA link speed to 1.5 Gbps
[  190.005731] ata7.00: exception Emask 0x10 SAct 0x3 SErr 0x780100 action 0x6
[  190.005735] ata7.00: irq_stat 0x08000000
[  190.005739] ata7: SError: { UnrecovData 10B8B Dispar BadCRC Handshk }
[  190.005743] ata7.00: failed command: READ FPDMA QUEUED
[  190.005750] ata7.00: cmd 60/00:00:d8:0f:d7/01:00:43:00:00/40 tag 0 ncq 131072 in
[  190.005751]          res 40/00:04:d8:0f:d7/00:00:43:00:00/40 Emask 0x10 (ATA bus error)
[  190.005755] ata7.00: status: { DRDY }
[  190.005758] ata7.00: failed command: READ FPDMA QUEUED
[  190.005764] ata7.00: cmd 60/00:08:d8:10:d7/01:00:43:00:00/40 tag 1 ncq 131072 in
[  190.005766]          res 40/00:04:d8:0f:d7/00:00:43:00:00/40 Emask 0x10 (ATA bus error)
[  190.005769] ata7.00: status: { DRDY }
[  190.005775] ata7: hard resetting link
[  190.493160] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  190.500930] ata7.00: configured for UDMA/133
[  190.500941] ata7: EH complete

---

