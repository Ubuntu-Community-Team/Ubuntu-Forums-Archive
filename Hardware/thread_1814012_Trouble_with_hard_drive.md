---
title: "Trouble with hard drive"
date: 2011-07-28
forum: Hardware
---

### Post by goshock on 2011-07-28
All of the sudden I cannot access my hard drive, one of them.  I rebooted and it still would not come online.  Here is something I found in the messages file:
> 
Jul 28 14:21:55 file kernel: [   22.470026] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Jul 28 14:21:55 file kernel: [   22.473505] ata10.00: failed to read native max address (err_mask=0x1)
Jul 28 14:21:55 file kernel: [   22.473508] ata10.00: HPA support seems broken, skipping HPA handling
Jul 28 14:21:55 file kernel: [   22.473513] ata10.00: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
Jul 28 14:21:55 file kernel: [   22.473516] ata10.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 28 14:21:55 file kernel: [   29.790026] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Jul 28 14:21:55 file kernel: [   29.796830] ata10: limiting SATA link speed to 1.5 Gbps
Jul 28 14:21:55 file kernel: [   29.796833] ata10.00: limiting speed to UDMA/100:PIO3
Jul 28 14:21:55 file kernel: [   37.110026] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
Jul 28 14:21:55 file kernel: [   37.132923] ata10.00: disabled

Is this thing toast?  Is there something I can do to get it to come back online.

---

### Post by jerrrys on 2011-07-28
you can try using your live cd.  this may allow you access to the hdd and you can at least retrieve your files.

---

