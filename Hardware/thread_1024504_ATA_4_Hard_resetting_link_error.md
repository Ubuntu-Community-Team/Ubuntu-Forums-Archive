---
title: "ATA 4 Hard resetting link error"
date: 2008-12-29
forum: Hardware
---

### Post by Georgie.Mathews on 2008-12-29
Hello all

Can someone diagnose the exact problem of my computer - I get the follow message in dmesg - my hard drive keeps resetting often now and it is irritating..I know it isnt my hard drive since I plugged it into my other machine and I dont get the error...

Here is the output from dmesg regarding the resetting :

```

[  276.973654] ata4: exception Emask 0x10 SAct 0x0 SErr 0x1810000 action 0xe frozen
[  276.973663] ata4: SError: { PHYRdyChg LinkSeq TrStaTrns }
[  276.973671] ata4: hard resetting link
[  283.284769] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  283.395677] ata4.00: configured for UDMA/133
[  283.395687] ata4: EH complete
[  283.395805] sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[  283.395826] sd 3:0:0:0: [sda] Write Protect is off
[  283.395830] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  283.395858] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Thanks a lot :)

---

### Post by Georgie.Mathews on 2008-12-30
LOL i fixed it - was a faulty power supply :)

---

