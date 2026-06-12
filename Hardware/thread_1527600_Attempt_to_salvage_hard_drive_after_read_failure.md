---
title: "Attempt to salvage hard drive after read failure"
date: 2010-07-09
forum: Hardware
---

### Post by rmeas on 2010-07-09
In my role as neighborhood tech guy, I got shipped a "crashed" hard drive.  It spins up and BIOS identifies it, but it gets a read failure on startup:

```

[    1.836943] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.001025] ata1.00: failed to read native max address (err_mask=0x1)
[    2.001030] ata1.00: HPA support seems broken, skipping HPA handling
[    2.001037] ata1.00: ATA-7: Maxtor	ARES C64K, VAM51JJ0, max UDMA/133
[    2.001042] ata1.00: 80295529 sectors, multi 0: LBA48 
[    2.008220] ata1.00: failed to set xfermode (err_mask=0x1)
[    7.164225] ata1.00: failed to set xfermode (err_mask=0x1)
[    7.164230] ata1.00: limiting speed to UDMA/100:PIO3
[   12.320232] ata1.00: failed to set xfermode (err_mask=0x1)
[   12.320236] ata1.00: disabled
```

Is there any chance of a bit by bit copy?  Any other suggestions?  Thanks.

---

### Post by wookieshaver on 2010-07-09
There's always a chance you can get data from a drive. If your using linux to grab the data there a few free forensic tools which might help available here:
 
[http://www.opensourceforensics.org/tools/unix.html](http://www.opensourceforensics.org/tools/unix.html)
 
Alternately, I have had good luck with getting data from a drive using windows and the "getback ntfs" program. I might also suggest if the bios cannt read it to place the drive in an external enclosure (usb esata - whatever type) and see if it will mount.

---

