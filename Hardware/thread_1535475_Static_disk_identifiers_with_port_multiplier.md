---
title: "Static disk identifiers with port multiplier"
date: 2010-07-20
forum: Hardware
---

### Post by Seq on 2010-07-20
Hi all,

I've got a SATA port multiplier, and if I plug a drive into a specific slot, I can see it registers in that slot properly, so I can identify drives by port. As an example, throwing a drive in slot 3 shows up as ata7.02 (see below).

All is fine so far. But the device nodes that udev creates are purely sequential, so this drive would be sdf. If I throw a drive into slot 2, it would be sdg. What I would like to do is have udev start at an offset (say, sdm) and assign from ata7 based port. So for example, slot 3 would always be 'sdo'.

Is this possible? Does anybody know the necessary udev voodoo to accomplish this?

Thanks,

```
[19844.107476] **ata7.02**: ATA-8: WDC WD5000AAKS-22YGA0, 12.01C02, max UDMA/133
[19844.107483] **ata7.02**: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[19844.108483] **ata7.02**: configured for UDMA/100
[19844.108584] ata7: EH complete
[19844.108754] scsi 1:2:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 12.0 PQ: 0 ANSI: 5
[19844.109127] sd 1:2:0:0: Attached scsi generic sg5 type 0
[19844.113156] sd 1:2:0:0: [**sdf**] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[19844.113257] sd 1:2:0:0: [**sdf**] Write Protect is off
[19844.113264] sd 1:2:0:0: [**sdf**] Mode Sense: 00 3a 00 00
[19844.113314] sd 1:2:0:0: [**sdf**] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[19844.113661]  **sdf**: sdf1 sdf2
[19844.122043] sd 1:2:0:0: [**sdf**] Attached SCSI disk

```

---

