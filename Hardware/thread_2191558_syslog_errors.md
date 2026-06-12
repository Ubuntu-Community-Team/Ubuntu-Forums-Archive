---
title: "syslog errors"
date: 2013-12-03
forum: Hardware
---

### Post by paolobenve on 2013-12-03
Hi!

In my ubuntu 13.10 syslog shows many line sequences like the following:

Dec  3 13:35:26 paolo kernel: [  719.086634] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Dec  3 13:35:26 paolo kernel: [  719.086640] ata3.00: BMDMA stat 0x66
Dec  3 13:35:26 paolo kernel: [  719.086644] ata3.00: failed command: READ DMA
Dec  3 13:35:26 paolo kernel: [  719.086651] ata3.00: cmd c8/00:00:e0:4c:4c/00:00:00:00:00/e6 tag 0 dma 131072 in
Dec  3 13:35:26 paolo kernel: [  719.086651]          res 51/84:f0:f0:4c:4c/84:00:19:00:00/e6 Emask 0x30 (host bus error)
Dec  3 13:35:26 paolo kernel: [  719.086655] ata3.00: status: { DRDY ERR }
Dec  3 13:35:26 paolo kernel: [  719.086658] ata3.00: error: { ICRC ABRT }
Dec  3 13:35:26 paolo kernel: [  719.086668] ata3: soft resetting link
Dec  3 13:35:27 paolo kernel: [  719.272368] ata3.00: configured for UDMA/33
Dec  3 13:35:27 paolo kernel: [  719.280256] ata3.01: configured for UDMA/66
Dec  3 13:35:27 paolo kernel: [  719.280272] ata3: EH complete
Dec  3 13:35:27 paolo kernel: [  719.312684] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Dec  3 13:35:27 paolo kernel: [  719.312692] ata3.00: BMDMA stat 0x66
Dec  3 13:35:27 paolo kernel: [  719.312696] ata3.00: failed command: READ DMA
Dec  3 13:35:27 paolo kernel: [  719.312701] ata3.00: cmd c8/00:00:e0:56:4c/00:00:00:00:00/e6 tag 0 dma 131072 in
Dec  3 13:35:27 paolo kernel: [  719.312701]          res 51/84:c0:20:57:4c/84:00:19:00:00/e6 Emask 0x30 (host bus error)
Dec  3 13:35:27 paolo kernel: [  719.312704] ata3.00: status: { DRDY ERR }
Dec  3 13:35:27 paolo kernel: [  719.312706] ata3.00: error: { ICRC ABRT }
Dec  3 13:35:27 paolo kernel: [  719.312715] ata3: soft resetting link
Dec  3 13:35:27 paolo kernel: [  719.508348] ata3.00: configured for UDMA/33
Dec  3 13:35:27 paolo kernel: [  719.516227] ata3.01: configured for UDMA/66
Dec  3 13:35:27 paolo kernel: [  719.516241] ata3: EH complete
Dec  3 13:35:28 paolo kernel: [  720.419777] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Dec  3 13:35:28 paolo kernel: [  720.419783] ata3.00: BMDMA stat 0x66
Dec  3 13:35:28 paolo kernel: [  720.419787] ata3.00: failed command: READ DMA EXT
Dec  3 13:35:28 paolo kernel: [  720.419793] ata3.00: cmd 25/00:00:c0:06:9d/00:01:19:00:00/e0 tag 0 dma 131072 in
Dec  3 13:35:28 paolo kernel: [  720.419793]          res 51/84:b0:10:07:9d/84:00:19:00:00/e0 Emask 0x30 (host bus error)
Dec  3 13:35:28 paolo kernel: [  720.419795] ata3.00: status: { DRDY ERR }
Dec  3 13:35:28 paolo kernel: [  720.419797] ata3.00: error: { ICRC ABRT }
Dec  3 13:35:28 paolo kernel: [  720.419807] ata3: soft resetting link
Dec  3 13:35:28 paolo kernel: [  720.604361] ata3.00: configured for UDMA/33
Dec  3 13:35:28 paolo kernel: [  720.612235] ata3.01: configured for UDMA/66
Dec  3 13:35:28 paolo kernel: [  720.612250] ata3: EH complete

I thinked it were a disk failing, changed the disk, but the error seeked. I changed the cable too, the messages keep coming out.

What do those messages come from? Might it be a motherboard problem.

Thank you for your help!

---

### Post by tgalati4 on 2013-12-03
Take the machine apart and clean it thoroughly with compressed air.  Look for bad capacitors--leaky or bulging.  It could be a problem with the disk controller chipset on the motherboard.  You might try a SATA/IDE card in a vacant PCI slot as a work-around.  Don't forget to check your power supply, especially the 12VDC rails.

---

