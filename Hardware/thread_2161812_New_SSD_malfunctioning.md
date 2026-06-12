---
title: "New SSD malfunctioning?"
date: 2013-07-12
forum: Hardware
---

### Post by rko618 on 2013-07-12
I just purchased a new motherboard, CPU, RAM, and SSD hard drive for my desktop. After replacing all of the parts and installing ubuntu 13.04 amd64, I am experiencing weird behavior with the new hard drive. On boot, fsck finds errors about 50% of the time but seems to auto repair them well enough. In addition, I have experienced Ubuntu locking up and programs crashing at a higher rate than I think is normal.

I would like to determine if the SSD is faulty so I can RMA it before my 30 days is up. Since I purchased the drive refurbished I am already suspicious. I ran through the SMART tests on the drive and it said everything was good. I tried plugging the drive into a different SATA port, no change. I tried a different SATA III cable, no change there either.

Here is the hardware I am using:
[LIST]
[*]Motherboard is a brand new ASUS Z87-C with a Haswell processor
[*]Refurbished OCZ Vertex 3 VTX3-25SAT3-120G 120GB SATA III MLC SSD
[/LIST]

Probably the biggest hint is this error that appears over and over again in /var/log/kern.log. I tried Googling for it found no results.

[FONT=Courier New]Jul  9 22:04:54 kernel: [  183.351248] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul  9 22:04:54 kernel: [  183.431426] ata2.00: configured for UDMA/33
Jul  9 22:04:54 kernel: [  183.431439] ata2: EH complete
Jul  9 22:04:55 kernel: [  184.191638] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Jul  9 22:04:55 kernel: [  184.191648] ata2: irq_stat 0x00400040, connection status changed
Jul  9 22:04:55 kernel: [  184.191654] ata2: SError: { PHYRdyChg 10B8B DevExch }
Jul  9 22:04:55 kernel: [  184.191664] ata2: hard resetting link[/FONT]

I really appreciate any help with this.

---

### Post by CatKiller on 2013-07-12
Sounds faulty to me.

---

### Post by rko618 on 2013-08-09
Following up... I RMA'd the drive and received a replacement that is the same model. The new drive is working very well without any errors. Now I can say for sure that the previous drive was faulty.

---

