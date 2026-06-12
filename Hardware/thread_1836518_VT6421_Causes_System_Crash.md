---
title: "VT6421 Causes System Crash"
date: 2011-08-31
forum: Hardware
---

### Post by lynwode on 2011-08-31
Howdy Folks,
I have run into an issue with a recently purchased esata controller card running with VT6421A chip. The card is picked up at boot time and I have the sata_via modules loaded. Sometimes at boot the attached 2TB WD HDD is picked up and mounted othertimes not. In addition to this when, on the rare occasions, it is picked up any data transfer causes the system to hang or crash. Below is a sample of the errors from SYSLOG.

Does anyone have any idea on what may be causing this or what can be done to fix it?
I have trawled google etc... and haven't found a solution - although I have educated myself in the world of lspci and lsmod :)

BTW I'm runing Natty on AMD 64Bit and Asus Mobo (exact details escape me at the moment)

Cheers,
Tim.


Aug 30 23:21:18  kernel: [   90.582844] 4:2:1: cannot get freq at ep 0x84
Aug 30 23:23:58  kernel: [  249.935929] ata6.00: exception Emask 0x12 SAct 0x0 SErr 0x1400500 action 0x6
Aug 30 23:23:58  kernel: [  249.935940] ata6.00: BMDMA stat 0x5
Aug 30 23:23:58  kernel: [  249.935949] ata6: SError: { UnrecovData Proto Handshk TrStaTrns }
Aug 30 23:23:58  kernel: [  249.935957] ata6.00: failed command: WRITE DMA EXT
Aug 30 23:23:58  kernel: [  249.935973] ata6.00: cmd 35/00:00:3f:a4:50/00:04:00:00:00/e0 tag 0 dma 524288 out
Aug 30 23:23:58  kernel: [  249.935976]          res 51/84:90:3f:a4:50/84:00:00:00:00/e0 Emask 0x12 (ATA bus error)
Aug 30 23:23:58  kernel: [  249.935984] ata6.00: status: { DRDY ERR }
Aug 30 23:23:58  kernel: [  249.935989] ata6.00: error: { ICRC ABRT }
Aug 30 23:23:58  kernel: [  249.936006] ata6: hard resetting link
Aug 30 23:23:58  kernel: [  250.680205] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 30 23:23:59  kernel: [  250.721221] ata6.00: configured for UDMA/133
Aug 30 23:23:59  kernel: [  250.721261] ata6: EH complete

---

### Post by arnuschky on 2011-09-07
Hey,

I have the same problem. I started a new bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639](https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639)

Cheers,
Arnuschky

---

### Post by lynwode on 2011-09-08
Nice one, I'll subscribe to it and hopefuly it'll get fixed soon :)

---

