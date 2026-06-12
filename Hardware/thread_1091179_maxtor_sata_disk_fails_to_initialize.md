---
title: "maxtor sata disk fails to initialize"
date: 2009-03-09
forum: Hardware
---

### Post by nilsah on 2009-03-09
Hi folks,

I am not able to get a maxtor sata disk to start up in Ubuntu. The disk works fine under windows.

Lines of interest from dmesg below. Also tried without irqpoll option.

Thank you,
Nils


[    0.000000] Linux version 2.6.27-11-server (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 20:19:41 UTC 2009 (Ubuntu 2.6.27-11.27-server)

[    0.000000] Kernel command line: root=UUID=169a55db-8481-4a1a-9ac1-feadebff04f3 ro quiet splash irqpoll

[    5.474687] ata2: SATA max UDMA/100 mmio m512@0xdffffe00 tf 0xdffffec0 irq 11
[    6.170289] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    6.190770] ata2.00: ATA-7: Maxtor 6Y200M0, YAR51HW0, max UDMA/133
[    6.190781] ata2.00: 398297088 sectors, multi 0: LBA48 
[    6.230916] ata2.00: failed to set xfermode (err_mask=0x1)
[   11.520180] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   11.580570] ata2.00: failed to set xfermode (err_mask=0x1)
[   11.580586] ata2.00: limiting speed to UDMA/100:PIO3
[   16.870183] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   16.930552] ata2.00: configured for UDMA/100
[   17.036241]  sda:<3>ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   17.036501] ata2.00: BMDMA2 stat 0x6d0009
[   17.036519] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   17.036523]          res 51/04:ff:ff:87:bd/00:00:00:00:00/a0 Emask 0x1 (device error)
[   17.036532] ata2.00: status: { DRDY ERR }
[   17.036538] ata2.00: error: { ABRT }
[   17.090680] ata2.00: failed to set xfermode (err_mask=0x1)
[   17.090707] ata2: hard resetting link
[   17.440116] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   17.500637] ata2.00: failed to set xfermode (err_mask=0x1)
[   17.500657] ata2.00: limiting speed to UDMA/100:PIO2
[   22.440157] ata2: hard resetting link
[   22.790131] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   22.850612] ata2.00: failed to set xfermode (err_mask=0x1)
[   22.850629] ata2.00: disabled
[   22.850686] ata2: EH complete

---

