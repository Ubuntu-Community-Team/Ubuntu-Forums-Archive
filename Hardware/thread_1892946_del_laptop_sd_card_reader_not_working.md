---
title: "del laptop sd card reader not working"
date: 2011-12-09
forum: Hardware
---

### Post by smxr on 2011-12-09
i have a ubuntu 11.10.

Sd card reader is not working on a vostro 1520 laptop, any idea how to fix it?

dmesg
```
[ 4065.204306] mmc0: error -110 whilst initialising SD card
[ 4075.232105] mmc0: Timeout waiting for hardware interrupt.
[ 4075.232112] sdhci: =========== REGISTER DUMP (mmc0)===========
[ 4075.232123] sdhci: Sys addr: 0x00000000 | Version:  0x0000c002
[ 4075.232133] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[ 4075.232143] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[ 4075.232153] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000005
[ 4075.232163] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[ 4075.232173] sdhci: Wake-up:  0x00000000 | Clock:    0x00000000
[ 4075.232183] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
[ 4075.232193] sdhci: Int enab: 0x00ff00c3 | Sig enab: 0x00ff00c3
[ 4075.232203] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 4075.232213] sdhci: Caps:     0x01f632b2 | Caps_1:   0x00000000
[ 4075.232224] sdhci: Cmd:      0x00000102 | Max curr: 0x00000064
[ 4075.232232] sdhci: Host ctl2: 0x00000000
[ 4075.232234] sdhci: ===========================================

```

---

### Post by pdv99 on 2012-01-15
Hi - Anyone got any resources that might help with this? 
I'm running a Dell Vostro 1310. Under Ubuntu 10.04, I could plug my (16Gb) SD memory card in and the OS regognised it, mounted it and opened a folder window to display the contents. 

Today I did an upgrade install to 11.10 Ocelot, and I now get the same error as above. 
So: Should 11.10 support 16Gb cards?
If so what can I do to try to track the source of the problem? I've tried googling MMC0 Error -110, but not found anything helpful.

Thanks folks

---

### Post by pdv99 on 2012-01-15
Update:

Disk utility sees the drive as /dev/mmcblk0, correctly determines its capacity but rports partitioning: unknown scheme.
but gparted doesn't see it. 

The data on the card can be read on other machines.

---

### Post by Mark Phelps on 2012-01-16
> **pdv99 said:**
> The data on the card can be read on other machines.

What versions of Ubuntu are the other machines (the ones that CAN read the card) running?

---

