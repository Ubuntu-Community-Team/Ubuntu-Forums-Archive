---
title: "Desktop PC with weird ata errors on dmesg"
date: 2010-07-28
forum: Hardware
---

### Post by AcidRain0 on 2010-07-28
On my main desktop pc, I dual boot and use Windows more than Ubuntu. Lately i've been having weird problems on Windows like my pc will just lock up or it will blue screen and start running chkdsk when coming back up. So I booted up Ubuntu and ran badblocks on all of my hdds.. everything seems fine. Except while badblocks was running, I noticed on two of my hdds, the badblocks test was stalling and wasn't running continues. I looked at dmesg and saw this:

```
[  909.185725] sd 0:0:0:0: [sda] 72303840 512-byte hardware sectors: (37.0 GB/34.4 GiB)
[  909.186668] sd 0:0:0:0: [sda] Write Protect is off
[  909.186672] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  909.187854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  909.225065] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  909.249924] ata2.00: configured for UDMA/33
[  909.249940] ata2: EH complete
[  909.255157] sd 1:0:0:0: [sdb] 72303840 512-byte hardware sectors: (37.0 GB/34.4 GiB)
[  909.256361] sd 1:0:0:0: [sdb] Write Protect is off
[  909.256366] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  909.257393] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  909.357750] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  909.357784] ata2.00: cmd c8/00:80:80:ae:08/00:00:00:00:00/e1 tag 0 dma 65536 in
[  909.357787]          res ff/ff:ff:ff:ff:ff/00:00:00:00:00/ff Emask 0x2 (HSM violation)
[  909.357792] ata2.00: status: { Busy }
[  909.357796] ata2.00: error: { ICRC UNC IDNF ABRT }
[  909.357807] ata2: hard resetting link
[  909.677063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  909.702624] ata2.00: configured for UDMA/33
[  909.702662] ata2: EH complete
[  909.710778] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  909.710784] ata2.00: BMDMA2 stat 0x6d0009
[  909.710797] ata2.00: cmd c8/00:80:80:ae:08/00:00:00:00:00/e1 tag 0 dma 65536 in
[  909.710800]          res 51/04:00:ff:ae:08/00:00:00:00:00/e1 Emask 0x1 (device error)
[  909.710805] ata2.00: status: { DRDY ERR }
[  909.710809] ata2.00: error: { ABRT }
[  909.734827] ata2.00: configured for UDMA/33
[  909.734841] ata2: EH complete

```

sda and sdb were the ones having problems with badblocks, Both sda and sdb are on it's own Sil raid controller. So is my raid controller dieing?

---

