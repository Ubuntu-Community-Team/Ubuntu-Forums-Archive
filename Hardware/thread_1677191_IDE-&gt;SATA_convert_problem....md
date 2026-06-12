---
title: "IDE-&gt;SATA convert problem..."
date: 2011-01-28
forum: Hardware
---

### Post by neorf on 2011-01-28
I've an ide hd and i've used an ide-sata convert to plug it into mb.
Now bios sees the disk but with a strange name "ÓAÍSÕNÇ ÓP1614Î' != ".

Ubuntu 10.04 starts and the disk is not detected.

This is part of dmseg:
```
[    3.026415] ata6.00: status: { DRDY ERR }
[    3.026417] ata6.00: error: { ICRC ABRT }
[    3.026422] ata6: hard resetting link
[    3.026423] ata6: nv: skipping hardreset on occupied port
[    3.492029] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.508184] ata6.00: configured for UDMA/100
[    3.508191] ata6: EH complete
[    3.510382] ata6: limiting SATA link speed to 1.5 Gbps
[    3.510385] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    3.510387] ata6.00: BMDMA stat 0x4
[    3.510389] ata6.00: failed command: READ DMA
[    3.510394] ata6.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 i                                             n
[    3.510395]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA                                              bus error)
[    3.510397] ata6.00: status: { DRDY ERR }
[    3.510399] ata6.00: error: { ICRC ABRT }
[    3.510402] ata6: hard resetting link
[    3.510404] ata6: nv: skipping hardreset on occupied port
[    3.976026] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.992187] ata6.00: configured for UDMA/100
[    3.992191] ata6: EH complete
[    3.994370] ata6.00: limiting speed to UDMA/66:PIO4
[    3.994372] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    3.994374] ata6.00: BMDMA stat 0x4
[    3.994377] ata6.00: failed command: READ DMA
[    3.994382] ata6.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 i                                             n
[    3.994383]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA                                              bus error)
[    3.994385] ata6.00: status: { DRDY ERR }
[    3.994387] ata6.00: error: { ICRC ABRT }
[    3.994390] ata6: hard resetting link
[    3.994392] ata6: nv: skipping hardreset on occupied port
[    4.460025] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.476187] ata6.00: configured for UDMA/66
[    4.476191] ata6: EH complete
[    4.478360] ata6.00: limiting speed to UDMA/33:PIO4
[    4.478362] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    4.478364] ata6.00: BMDMA stat 0x4
[    4.478366] ata6.00: failed command: READ DMA
[    4.478371] ata6.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 i                                             n
[    4.478372]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA                                              bus error)
[    4.478375] ata6.00: status: { DRDY ERR }
[    4.478376] ata6.00: error: { ICRC ABRT }
[    4.478380] ata6: hard resetting link
[    4.478381] ata6: nv: skipping hardreset on occupied port
[    4.944030] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
SN P1614' != 'ÓAÍSÕNÇ ÓP1614Î'number mismatch 'A
[    4.960169] ata6.00: revalidation failed (errno=-19)
[    4.960172] ata6.00: limiting speed to UDMA/33:PIO3
[    9.944019] ata6: hard resetting link
[    9.944020] ata6: nv: skipping hardreset on occupied port
[   10.412028] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
SN P1614' != 'ÓAÍSÕNÇ ÓP1614Î'number mismatch 'A
[   10.420168] ata6.00: revalidation failed (errno=-19)
[   10.420170] ata6.00: disabled
[   15.412017] ata6: hard resetting link
[   16.292028] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.300174] ata6.00: ATA-7: ÓAÍSÕNÇ ÓP1614Î, ÔM100-24, max UDMA/100
[   16.300176] ata6.00: 268435455 sectors, multi 0: LBA
SN P1614'8166] ata6.00: model number mismatch 'ÓAÍSÕNÇ ÓP1614Î' != 'A
[   16.308168] ata6.00: revalidation failed (errno=-19)
[   16.308170] ata6: limiting SATA link speed to 1.5 Gbps
[   16.308173] ata6.00: limiting speed to UDMA/100:PIO3
[   21.292016] ata6: hard resetting link
[   21.292018] ata6: nv: skipping hardreset on occupied port
[   21.760028] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
SN P1614'8166] ata6.00: model number mismatch 'ÓAÍSÕNÇ ÓP1614Î' != 'A
[   21.768168] ata6.00: revalidation failed (errno=-19)
[   21.768169] ata6.00: disabled
[   21.768178] sd 5:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.768182] sd 5:0:0:0: [sdd] Sense Key : Aborted Command [current] [descript                                             or]

```

---

