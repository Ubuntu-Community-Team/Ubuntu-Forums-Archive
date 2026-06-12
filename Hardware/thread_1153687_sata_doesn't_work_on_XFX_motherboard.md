---
title: "sata doesn't work on XFX motherboard"
date: 2009-05-09
forum: Hardware
---

### Post by linuxraptor on 2009-05-09
I have an XFX 750a motherboard that sata does not function on with the new kernel series.  I honestly have no idea what the problem is, worked for all kernels up to 2.6.28.  Doesn't show any hard drives as attatched to sata.
Kernel output:
```
ata8: SATA max UDMA/133 abar m8192@0xf5f76000 port 0xf5f76380 irq 763
ata3.00: qc timeout (cmd 0xec)
ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3.00: qc timeout (cmd 0xec)
ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3.00: qc timeout (cmd 0xec)
ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4.00: qc timeout (cmd 0xec)
ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4.00: qc timeout (cmd 0xec)
ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4.00: qc timeout (cmd 0xec)
ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
ata7: SATA link down (SStatus 0 SControl 300)
ata8: SATA link down (SStatus 0 SControl 300)
```

---

