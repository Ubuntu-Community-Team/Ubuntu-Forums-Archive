---
title: "I have no idea Oo"
date: 2009-08-29
forum: Hardware
---

### Post by briantoumbs on 2009-08-29
Dmesg | less > [    1.739215] ata1: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff900 irq 22
[    1.739222] ata2: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff980 irq 22
[    1.739230] ata3: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa00 irq 22
[    1.739237] ata4: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa80 irq 22
[    2.220019] ata1: softreset failed (device not ready)
[    2.220029] ata1: failed due to HW bug, retry pmp=0
[    2.384035] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.385377] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    2.385386] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.385406] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.387137] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.387143] ata1.00: configured for UDMA/133
[    2.704033] ata2: SATA link down (SStatus 0 SControl 300)
[    3.188020] ata3: softreset failed (device not ready)
[    3.188029] ata3: failed due to HW bug, retry pmp=0
[    3.352029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.365067] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL05, max UDMA/100, ATAPI AN
[    3.365087] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.378450] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.378454] ata3.00: configured for UDMA/100
[    3.860019] ata4: softreset failed (device not ready)
[    3.860024] ata4: failed due to HW bug, retry pmp=0
[    4.024027] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.025294] ata4.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    4.025299] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.025317] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.026985] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.026989] ata4.00: configured for UDMA/133
[    4.027087] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    4.027177] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.027196] sd 0:0:0:0: [sda] Write Protect is off
[    4.027200] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.027222] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.027291] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.027307] sd 0:0:0:0: [sda] Write Protect is off
[    4.027312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.027331] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.027339]  sda: sda1 sda2 sda3
[    4.048609] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.048660] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.049767] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL05 PQ: 0 ANSI: 5
[    4.054110] sr0: scsi3-mmc drive: 8x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.054117] Uniform CD-ROM driver Revision: 3.20
[    4.054198] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.054229] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.054284] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    4.054361] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.054378] sd 3:0:0:0: [sdb] Write Protect is off
[    4.054382] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.054402] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.054448] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.054464] sd 3:0:0:0: [sdb] Write Protect is off
[    4.054468] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.054488] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.054496]  sdb: sdb1
[    4.071384] sd 3:0:0:0: [sdb] Attached SCSI disk
[    4.071417] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    4.071660] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.071695] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    4.071773] scsi4 : pata_atiixp
[    4.071854] scsi5 : pata_atiixp
[    4.073096] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.073101] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    4.236494] ata5.00: ATAPI: ASUS    DRW-22B1S, 1.01, max UDMA/66
[    4.252441] ata5.00: configured for UDMA/66
[   10.804042] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   10.804056] ata5.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   10.804057]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   10.804058]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   10.804070] ata5.00: status: { DRDY }
[   15.844015] ata5: link is slow to respond, please be patient (ready=0)
[   20.828015] ata5: device not ready (errno=-16), forcing hardreset
[   20.828025] ata5: soft resetting link
[   21.008443] ata5.00: configured for UDMA/66
[   21.009196] ata5: EH complete
[   26.804039] ata5.00: limiting speed to UDMA/44:PIO4
[   26.804044] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   26.804052] ata5.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   26.804053]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   26.804054]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   26.804065] ata5.00: status: { DRDY }
[   31.844014] ata5: link is slow to respond, please be patient (ready=0)
[   36.828015] ata5: device not ready (errno=-16), forcing hardreset
[   36.828025] ata5: soft resetting link
[   37.008446] ata5.00: configured for UDMA/44
[   37.009222] ata5: EH complete
[   42.804039] ata5.00: limiting speed to UDMA/33:PIO4
[   42.804044] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   42.804052] ata5.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   42.804053]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   42.804054]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   42.804065] ata5.00: status: { DRDY }
[   47.844014] ata5: link is slow to respond, please be patient (ready=0)
[   52.828014] ata5: device not ready (errno=-16), forcing hardreset
[   52.828024] ata5: soft resetting link
[   53.008446] ata5.00: configured for UDMA/33
[   53.009194] ata5: EH complete
[   58.804039] ata5.00: limiting speed to PIO4
[   58.804043] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   58.804051] ata5.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   58.804052]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   58.804053]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   58.804064] ata5.00: status: { DRDY }
[   63.844015] ata5: link is slow to respond, please be patient (ready=0)
[   68.828014] ata5: device not ready (errno=-16), forcing hardreset
[   68.828024] ata5: soft resetting link
[   69.008447] ata5.00: configured for PIO4
[   69.010799] ata5: EH complete
[   69.010805] scsi scan: 96 byte inquiry failed.  Consider BLIST_INQUIRY_36 for this device
[   69.011425] scsi 4:0:0:0: CD-ROM            ASUS     DRW-22B1S        1.01 PQ: 0 ANSI: 5
[   69.017526] sr1: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   69.017593] sr 4:0:0:0: Attached scsi CD-ROM sr1



I haven't been able to find a fix for this error, it turns a normally very fast boot time into a few minutes boot time. Can anyone help me please!

---

### Post by briantoumbs on 2009-09-14
Is there anything about this?

Motherboard: Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: M3A
	Version: Rev 1.xx
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+


Kernel: 2.6.28-15-generic

---

### Post by luks911 on 2009-09-14
I don't know if it's your case, but I had the same error in a PC and the problem was the wire (the one that connect the motherboard with the HD). I replaced it and the problem disappeared. Also, sometimes I have that error in my notebook, and I don't know which is the cause.

---

### Post by briantoumbs on 2009-09-15
I had this error when I first installed 9.04, wasn't there in 8.04 or 8.10.
I re-installed 8.10 and the problem went away. But now with 9.04 back the problem is back.

---

### Post by luks911 on 2009-09-15
It doesn't seem like a hardware problem, hum... Maybe it's something related to the kernel, but I don't know what... I'm run out of ideas for now. Sorry.

---

### Post by Whiffle on 2009-09-15
Have you tried reseating your SATA cable?

[http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837)

---

### Post by briantoumbs on 2009-09-15
Doesn't seem to be the same problem as mine, but I checked the cables an there all seated. 2 SATA HDDs and 1 SATA DVD burner.

---

