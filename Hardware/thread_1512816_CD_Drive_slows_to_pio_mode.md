---
title: "CD Drive slows to pio mode"
date: 2010-06-18
forum: Hardware
---

### Post by Thq on 2010-06-18
During startup, if I remove the quiet flag, I see this:
```
[    1.136423] ata2.00: ATAPI: ASUS CD-S400/A, V2.1N, max UDMA/33
[    1.144438] ata2.00: configured for UDMA/33
[    1.144897] scsi 1:0:0:0: CD-ROM            ASUS     CD-S400/A        2.1N PQ: 0 ANSI: 5
[   31.816037] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   31.816099] sr 1:0:0:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[   31.816605] ata2.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[   31.816607]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   31.816732] ata2.00: status: { DRDY }
[   36.856015] ata2: link is slow to respond, please be patient (ready=0)
[   41.840012] ata2: device not ready (errno=-16), forcing hardreset
[   41.840069] ata2: soft resetting link
[   42.004421] ata2.00: configured for UDMA/33
[   42.004963] ata2: EH complete
[   72.816034] ata2.00: limiting speed to UDMA/25:PIO4
[   72.816088] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   72.816143] sr 1:0:0:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[   72.816645] ata2.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[   72.816647]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   72.816771] ata2.00: status: { DRDY }
[   77.856011] ata2: link is slow to respond, please be patient (ready=0)
[   82.840014] ata2: device not ready (errno=-16), forcing hardreset
[   82.840072] ata2: soft resetting link
[   83.004420] ata2.00: configured for UDMA/25
[   83.004957] ata2: EH complete
[  113.816032] ata2.00: limiting speed to PIO4
[  113.816085] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  113.816140] sr 1:0:0:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[  113.816641] ata2.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[  113.816643]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  113.816766] ata2.00: status: { DRDY }
[  118.856015] ata2: link is slow to respond, please be patient (ready=0)
[  123.840015] ata2: device not ready (errno=-16), forcing hardreset
[  123.840073] ata2: soft resetting link
[  124.004420] ata2.00: configured for PIO4
[  124.004957] ata2: EH complete
[  124.005783] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[  124.005839] Uniform CD-ROM driver Revision: 3.20
[  124.006063] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  124.006158] sr 1:0:0:0: Attached scsi generic sg1 type 5
```

How do I either get the drive to work with UDMA 2 or how do I get it so it only uses PIO4? I've tried disabling UDMA for the cd drive in the bios, but it still says the same thing

---

### Post by Thq on 2010-06-23
If I could get an answer, I'm pretty sure I can get a 2:30 boot down to 20 seconds, so any help would be appreciated.

---

### Post by Yellow Pasque on 2010-06-23
[http://www.mjmwired.net/kernel/Documentation/ide/ide.txt](http://www.mjmwired.net/kernel/Documentation/ide/ide.txt)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt#928](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt#928)

---

