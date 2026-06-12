---
title: "External  eSata disk not recognised"
date: 2008-07-08
forum: Hardware
---

### Post by Titanet on 2008-07-08
Here is the result of a dmesg | tail -15 after pluging my external 2.5 disk on the eSata port of a ASUS V1S-AK012E laptop :

~$ dmesg | tail -15
[  129.953872]    groups: 03
[  142.360733] ata6: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xa frozen
[  142.360747] ata6: irq_stat 0x00400040, connection status changed
[  142.360754] ata6: SError: { PHYRdyChg CommWake DevExch }
[  142.360773] ata6: hard resetting link
[  143.214470] ata6: port is slow to respond, please be patient (Status 0xd0)
[  144.229644] ata6: softreset failed (device not ready)
[  144.229658] ata6: hard resetting link
[  144.915797] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  144.916375] ata6.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[  144.916384] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[  144.917045] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  144.917053] ata6.00: revalidation failed (errno=-5)
[  144.917060] ata6: failed to recover some devices, retrying in 5 secs
[  146.622763] ata6: hard resetting link
titanet@Ubu710-laptop:~$ dmesg | tail -15
[  163.766833] ata6: hard resetting link
[  163.886909] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  163.888098] ata6.00: configured for UDMA/133
[  163.888129] ata6: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  163.888136] ata6: irq_stat 0x00400040, connection status changed
[  163.889246] ata6.00: configured for UDMA/133
[  163.889256] ata6: EH complete
[  163.889332] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  163.889357] sd 5:0:0:0: [sdb] Write Protect is off
[  163.889362] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  163.889398] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  163.889435] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  163.889456] sd 5:0:0:0: [sdb] Write Protect is off
[  163.889461] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  163.889494] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


I updated from Ubuntu Gutsy to Hardy some weeks ago.

---

