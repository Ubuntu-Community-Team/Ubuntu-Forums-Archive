---
title: "Live CD not booting, odd device error"
date: 2008-04-26
forum: Hardware
---

### Post by matthias.sitte on 2008-04-26
Hi,

I have an odd problem installing Ubuntu on a machine. After downloading the AMD64 version (also tried the i386 version), verifying and burning I'm not able to boot Ubuntu Live CD on a specific computer. Btw, it works on a second one without flaw, so I guess the CD is ok. Anyway, after booting (w/o splash and quiet option) I see repeatedly the following output:

```
[x] end_request: I/O error, dev sr0, sector 128
[x] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[x] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current]
[x] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[x] end_request: I/O error, dev sr0, sector 132
[x] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[x] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current]
[x] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
```

Finally the CD leaves me with Busybox where I can reboot...

I have already tried irqpoll, noacpi and noapic boot options, none of them worked. I've been searching this forum but didn't find a solution yet.

1) Is it a hardware incompatibility?
2) Other boot options not tried?

I appreciate any suggestions, help and comments.

Thanks!

**Update:**
I finally solved the problem. Adding "all_generic_ide" to the boot options managed to make the Live CD boot. Maybe it's a problem related to the fact that my CD is the only PATA drive, and it's made a Master, not a Slave device. We'll see about that...

---

### Post by matthias.sitte on 2010-11-20
Error was fixed by re-partitioning the drive(s).

---

