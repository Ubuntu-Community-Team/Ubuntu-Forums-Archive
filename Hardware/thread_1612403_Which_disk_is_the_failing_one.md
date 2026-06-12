---
title: "Which disk is the failing one?"
date: 2010-11-03
forum: Hardware
---

### Post by mamruoc on 2010-11-03
Hello,

I got a failing disk, and dmesg give me this result (dmesg | grep ata4):
[    1.868835] ata4: SATA max UDMA/100 host m128@0xfc7ffc00 port 0xfc7fa000 irq 17
[    6.270042] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    6.271060] ata4.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    6.271064] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.272511] ata4.00: configured for UDMA/100
[353251.040043] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[353251.040049] ata4.00: failed command: SMART
[353251.040056] ata4.00: cmd b0/da:00:00:4f:c2/00:00:00:00:00/00 tag 0
[353251.040062] ata4.00: status: { DRDY }

How do i find which disk this is? I got 5 disk from same batch, så I need to know the serial number to be able to identify the correct disk.

Mam

---

