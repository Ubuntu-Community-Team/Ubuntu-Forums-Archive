---
title: "Disk vanished??!!!"
date: 2010-06-18
forum: Hardware
---

### Post by Colin@oxford on 2010-06-18
I had left my computer running whilke I had to do something else.  I returned to it to find a blank screen with a small white arrow on it.  Nothing I could do would get the machine to do anything, so I pressed the power button to reboot.  Now the BIOS does not detect the hard disk.  I can only boot from a CD (or an external disk - it does detect that).

So my question is - has my hard disk suddenly died?  Is there any hope of getting anything off it?  What can I do to retrieve any information?

---

### Post by Colin@oxford on 2010-06-18
Further info.  On booting with a CD and running 'dmesg', all I see is a large number of thses messages:

```

[  280.791809] ata2: irq_stat 0x00000040, connection status changed
[  280.791816] ata2: SError: { RecovComm PHYRdyChg CommWake 10B8B DevExch }
[  280.791828] ata2: limiting SATA link speed to 1.5 Gbps
[  280.791834] ata2: hard resetting link
[  281.516545] ata2: SATA link down (SStatus 0 SControl 310)
[  281.516557] ata2: EH complete
[  281.526879] ata2: exception Emask 0x10 SAct 0x0 SErr 0x40d0002 action 0xe frozen


```

---

