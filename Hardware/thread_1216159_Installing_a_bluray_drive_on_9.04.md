---
title: "Installing a bluray drive on 9.04"
date: 2009-07-18
forum: Hardware
---

### Post by cpufreak2589 on 2009-07-18
I'm still very new to linux, and I'm finding the lack of a "device manager" irritating. I've just bought and plugged in a new sata bluray drive, which shows up in bios just fine, and when I'm booting I see something scroll by with the words SATA and the drive's mfr, so I know it is detected, but I can't access it at all. I'm not sure how to properly word what I've done, but I know that /dev/sr0 is my primary cd drive, which works, and there is no /dev/sr1 or any other /dev/whatever you can think of. Can anybody point me towards a good guide on installing hardware that isn't autodetected? I don't know where to even begin.

---

### Post by cariboo on 2009-07-18
Have a look at this [wiki]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") page.

---

### Post by cpufreak2589 on 2009-07-18
> **cariboo907 said:**
> Have a look at this [wiki]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") page.

I've run through that a few times, and it starts assuming my drive is detected. Maybe I fail at linux, and the drive won't show up under "computer" until a disc is inserted, but I've put in a plain ol' data CD and nothing happens. That article focuses on playing movies which, while great, won't happen until ubuntu decided to recognize my drive.

Is there some sort of command to list what sata devices are recognized and go from there?

EDIT: I checked dmesg and I found what I saw at boot, can anyone decipher this?


```
[    5.888444] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb000 irq 23
[    5.888534] ata4: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xb008 irq 23
[    6.768054] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.776294] ata3.00: ATAPI: ATAPI   iHOS104, WL06, max UDMA/100
[    6.792302] ata3.00: configured for UDMA/100
[   11.792025] ata3.00: qc timeout (cmd 0xa0)
[   11.792111] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
[   12.672053] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.696300] ata3.00: configured for UDMA/100
[   17.696024] ata3.00: qc timeout (cmd 0xa0)
[   17.696111] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
[   17.696197] ata3: limiting SATA link speed to 1.5 Gbps
[   17.696282] ata3.00: limiting speed to UDMA/100:PIO3
[   18.576055] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   18.600301] ata3.00: configured for UDMA/100
[   23.600017] ata3.00: qc timeout (cmd 0xa0)
[   23.600104] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
[   23.600189] ata3.00: disabled
[   23.600284] ata3: hard resetting link
[   24.480053] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   24.480147] ata3: EH complete
```

---

### Post by syphr42 on 2009-12-03
Did you ever find a solution to this? I have the exact same drive and I have the same symptoms - the drive appears fine to the BIOS, doesn't seem to exist in Ubuntu, and my dmesg is identical to yours. However, I'm running 9.10 Karmic. Any help would be greatly appreciated.

Thanks.

---

### Post by syphr42 on 2009-12-05
I added my experience to a bug reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093)

The linked bug is marked "Fix Committed" so I guess that might mean it's not out, but it was committed before Karmic was released and I still see the problem in a daily build of the Lucid (10.04) live CD.

---

