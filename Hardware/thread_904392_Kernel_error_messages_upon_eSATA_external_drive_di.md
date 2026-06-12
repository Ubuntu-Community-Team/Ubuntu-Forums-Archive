---
title: "Kernel error messages upon eSATA external drive disconnect"
date: 2008-08-29
forum: Hardware
---

### Post by kevinp on 2008-08-29
Hi all,

I am running Kubuntu with kernel 2.6.22-15-generic on AMD64.

I've connected an eSATA external hard drive enclosure (Antec MX-1) to the eSATA port of an M2N32-SLI Deluxe motherboard.  The enclosure and drive work very well and I am pleased to report sustained data write rates of 55 MB/sec :)

Anyway, when I shutdown the drive, I umount the partitions and then flip the power switch on the enclosure.  At which point, the following error messages appear in /var/log/messages:

```
Aug 29 07:31:36 kpas1 kernel: [38219.576991] ata7: soft resetting port
Aug 29 07:31:36 kpas1 kernel: [38219.577005] ata7: SATA link down (SStatus 0 SControl 300)
Aug 29 07:31:36 kpas1 kernel: [38219.577014] ata7: failed to recover some devices, retrying in 5 secs
Aug 29 07:31:41 kpas1 kernel: [38224.581416] ata7: hard resetting port
Aug 29 07:31:43 kpas1 kernel: [38226.659919] ata7: SATA link down (SStatus 0 SControl 300)
Aug 29 07:31:43 kpas1 kernel: [38226.659934] ata7.00: limiting speed to UDMA/100:PIO3
Aug 29 07:31:43 kpas1 kernel: [38226.659937] ata7: failed to recover some devices, retrying in 5 secs
Aug 29 07:31:48 kpas1 kernel: [38231.660341] ata7: hard resetting port
Aug 29 07:31:51 kpas1 kernel: [38233.738862] ata7: SATA link down (SStatus 0 SControl 300)
Aug 29 07:31:51 kpas1 kernel: [38233.738874] ata7.00: disabled
Aug 29 07:31:51 kpas1 kernel: [38234.242514] ata7: EH complete
Aug 29 07:31:51 kpas1 kernel: [38234.246989] ata7.00: detaching (SCSI 6:0:0:0)
Aug 29 07:31:51 kpas1 kernel: [38234.247148] sd 6:0:0:0: [sdd] Synchronizing SCSI cache
Aug 29 07:31:51 kpas1 kernel: [38234.247367] sd 6:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Aug 29 07:31:51 kpas1 kernel: [38234.247371] sd 6:0:0:0: [sdd] Stopping disk
Aug 29 07:31:51 kpas1 kernel: [38234.247520] sd 6:0:0:0: [sdd] START_STOP FAILED
Aug 29 07:31:51 kpas1 kernel: [38234.247522] sd 6:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
```

So they seem scary, but in reality, I can switch on the drive again and it is detected and mounts just fine.

So should I just ignore these messages?  Or is there something in there that I should pay attention to?

---

