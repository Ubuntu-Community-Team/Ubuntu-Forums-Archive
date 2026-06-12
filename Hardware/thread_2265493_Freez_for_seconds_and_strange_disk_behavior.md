---
title: "Freez for seconds and strange disk behavior"
date: 2015-02-15
forum: Hardware
---

### Post by mstanger on 2015-02-15
Hi all, I found this in my events logs, I found a lot of them when generic-pae change to version version 3.2.0-74-generic-pae to 3.2.0-75, enough to make my computer unusable...
So when I found this relation with the last update I select previous 3.2.0-72-generic-pae, and this gave me some peace... but this is still there and my worries is that in the future it could give me some head aches.

Details:
[B]Versión 12.04 (precise) de 32-bit
Núcleo Linux 3.2.0-76-generic-pae
GNOME 3.4.2

AMD FX(tm)-6300 Six-Core Processor × 6, 3,7 GiB RAM, the Disk is a Seagate Barracuda ST1000DM003 1TB 7200 RPM[/B]
(The disk pass all the test in linux and windows and SMART report everything in good status)

And this is what I get when it turn freez....

```
Feb 15 18:03:17 x kernel: [22780.016089] ata4.00: exception Emask 0x10 SAct 0x0 SErr 0x1850000 action 0xe frozen
Feb 15 18:03:17 x kernel: [22780.016097] ata4: SError: { PHYRdyChg CommWake LinkSeq TrStaTrns }
Feb 15 18:03:17 x kernel: [22780.016104] ata4.00: failed command: READ DMA EXT
Feb 15 18:03:17 x kernel: [22780.016114] ata4.00: cmd 25/00:08:e0:6b:5e/00:00:1c:00:00/e0 tag 0 dma 4096 in
Feb 15 18:03:17 x kernel: [22780.016116]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x14 (ATA bus error)
Feb 15 18:03:17 x kernel: [22780.016121] ata4.00: status: { DRDY }
Feb 15 18:03:17 x kernel: [22780.016131] ata4: hard resetting link
Feb 15 18:03:17 x kernel: [22780.016134] ata4: nv: skipping hardreset on occupied port
Feb 15 18:03:18 x kernel: [22780.888099] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 15 18:03:18 x kernel: [22780.912514] ata4.00: configured for UDMA/133
Feb 15 18:03:18 x kernel: [22780.912525] ata4.00: device reported invalid CHS sector 0
Feb 15 18:03:18 x kernel: [22780.912540] ata4: EH complete
```

Thanks in advances.

---

### Post by mstanger on 2015-03-19
Ok, just if this is useful for some one, there is more than 15 since I apply the some changes to try to fix this, and seems that is working pretty well.

First I change the fstab settings adding this parameters to my partitions / and /home

U********7 /               ext4    errors=remount-ro 0       1
U********7 /               ext4    errors=remount-ro,noatime,commit=100 0       1

So adding noatime and commit equal to 5~100 did the job for me... no more ata errors, no more freezing, I also found that in my smart information seek error and read error was constantly raising (read error in particular was something documented on SEGATE disk), but I always saw this number raise, and after the changes it reduce the rate of change, before that every time I click refresh button I get a higher number this rime after the changes it keep constant for a while. 

For me ti reduce the activity of jbd2 process, that was writing to disk all the time.

So I know that commit time will increase the chance to lose data for a blackout or something but is more easy for me deal with that than a broken disk or unusable PC do to the freezing, also I saw some people talking about that noatime has no effect or minimun on ext4... but for me it works so well.

Thanks and I hope this could help someone else. :p

---

