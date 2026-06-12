---
title: "Rescue Data?"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by MadMan2k on 2006-07-17
Seems like some bad sectors have eaten my ext3 superblock - at least it spits out a lot of the following errors at the start until it gives up mounting the partition:

```
[17179951.748000] end_request: I/O error, dev hdd, sector 64
[17179953.088000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179953.088000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=65, high=0, low=65, sector=65
```

but I can still see the partition as /dev/hdd1 and I could read out the first 46G with "dd bs=512 skip=16".
The partition had 40G of data and 200G in total, but I dont have the capacity to read out the whole 200G yet.
Now I wonder if the first 46G contained the 40G of data and how I can read it out...

---

### Post by John.Michael.Kane on 2006-07-20
This should be able to help you offload the files you wish to recover [**[COLOR="Red"]SystemRescueCd[/COLOR]**]("http://www.sysresccd.org/Main_Page")

---

