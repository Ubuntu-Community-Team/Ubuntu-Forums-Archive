---
title: "Error message: kernel: ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100) wth?"
date: 2018-05-02
forum: Hardware
---

### Post by armadanasar on 2018-05-02
Hi guys,

so I just resetted my pc while I'm playing a game on Windows disk because of a freeze and then I decided to move on to to work on my Linux partition. However, during boot I got this surprising boot messages:

```

[B]May 02 19:31:06 nasar-pc kernel: ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 02 19:31:06 nasar-pc kernel: ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 02 19:31:06 nasar-pc kernel: ata4: SATA link down (SStatus 4 SControl 300)
May 02 19:31:06 nasar-pc kernel: ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 02 19:31:06 nasar-pc kernel: ata1.00: ATA-8: ST1000DM010-2EP102, CC43, max UDMA/133
May 02 19:31:06 nasar-pc kernel: ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 02 19:31:06 nasar-pc kernel: ata2.00: ATA-9: ST2000DM001-1ER164, CC26, max UDMA/133
May 02 19:31:06 nasar-pc kernel: ata2.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 02 19:31:06 nasar-pc kernel: ata1.00: configured for UDMA/133
May 02 19:31:06 nasar-pc kernel: ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)[/B]
May 02 19:31:06 nasar-pc kernel: scsi 0:0:0:0: Direct-Access     ATA      ST1000DM010-2EP1 CC43 PQ: 0 ANSI: 5
May 02 19:31:06 nasar-pc kernel: random: fast init done
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: Attached scsi generic sg0 type 0
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] 4096-byte physical blocks
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] Write Protect is off
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 02 19:31:06 nasar-pc kernel:  sda: sda1 sda2 sda3
May 02 19:31:06 nasar-pc kernel: sd 0:0:0:0: [sda] Attached SCSI disk

... some other long usb detection message...


May 02 19:31:06 nasar-pc kernel: [drm] RC6 on
May 02 19:31:06 nasar-pc kernel: ata2.00: configured for UDMA/133
[B]May 02 19:31:06 nasar-pc kernel: scsi 1:0:0:0: Direct-Access     ATA      ST2000DM001-1ER1 CC26 PQ: 0 ANSI: 5
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: Attached scsi generic sg1 type 0
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] 4096-byte physical blocks
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] Write Protect is off
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 02 19:31:06 nasar-pc kernel:  sdb: sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
May 02 19:31:06 nasar-pc kernel: sd 1:0:0:0: [sdb] Attached SCSI disk
May 02 19:31:06 nasar-pc kernel: ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 02 19:31:06 nasar-pc kernel: ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
May 02 19:31:06 nasar-pc kernel: ata3: limiting SATA link speed to 1.5 Gbps
May 02 19:31:06 nasar-pc kernel: ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May 02 19:31:06 nasar-pc kernel: ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
May 02 19:31:06 nasar-pc kernel: ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/B]

```

and my pc spec is:

Motherboard: Asus H110M-E/M.2 DDR4
Processor: Intel Core i5-7400 Kaby Lake
RAM: 8GB DDR4


After I've seen those messages I decided to promptly backup all my important documents to the other drive for safety.. Now, my question is: What are those ata3: failed to identify messages actually mean? And what should I do? Are they a telltale sign of failing drives? To me, both drives failing are an impossibility, because the ST2000DM drive were 2.5 years old meanwhile the ST1000DM drive are just 2 months old? It's so damn ridiculous..

I would to hear from you guys.. Thanks in Advance.

---

