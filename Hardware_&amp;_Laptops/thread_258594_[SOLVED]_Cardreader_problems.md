---
title: "[SOLVED] Cardreader problems"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2006-09-16
My cardreader on my laptop is not working.
It shows this from the dmesg

```

[17180339.072000] sdhci: ============== REGISTER DUMP ==============
[17180339.072000] sdhci: Sys addr: 0x00000000 | Version:  0x00000000
[17180339.072000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17180339.072000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17180339.072000] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000001
[17180339.072000] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[17180339.072000] sdhci: Walk up:  0x00000000 | Clock:    0x00008007
[17180339.072000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
[17180339.072000] sdhci: Int enab: 0x01ff00cf | Sig enab: 0x01ff00cf
[17180339.072000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17180339.072000] sdhci: Caps:     0x01e021a1 | Max curr: 0x00000055
[17180339.072000] sdhci: ===========================================
[17180349.072000] mmc0: Timeout waiting for hardware interrupt. Please report th is to <sdhci-devel@list.drzeus.cx>.

```

---

### Post by Jaxilian on 2006-09-16
I thought i could get the full dmesg in here, but it's too long.

---

### Post by Jaxilian on 2006-09-16
I zipped it down instead :D

---

### Post by Jaxilian on 2006-09-19
anyone knows something about this?

---

### Post by Jaxilian on 2006-09-21
bump

---

### Post by xmux on 2006-09-21
Card reader is a stupid thing, since one year i am trying to solve the problem but its not working i have a Ubuntu Dapper Drake on a Toshiba laptop and the sd card reader is not working... i heard its because of the Texas Instruments.. They is no driver for linux...

---

### Post by dcosmin on 2006-11-13
I found this [http://developer.berlios.de/projects/tifmxx/](http://developer.berlios.de/projects/tifmxx/)
"Alternative attempt to develop linux driver for TI FlashMedia xx12/xx21 storage controllers." maybe it can be of use.

---

### Post by dcosmin on 2006-11-13
I have a Toshiba laptop too and I managed to make my card reader work using the driver I mentioned.
$ lspci |grep Texas
07:06.0 CardBus bridge: Texas Instruments Unknown device 8039
07:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
07:06.2 Mass storage controller: Texas Instruments Unknown device 803b
07:06.3 Class 0805: Texas Instruments Unknown device 803c

After inserting the modules into the kernel it imediatly detected the mmc card

#fdisk -l

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   ?    12158374    29994462   570754815+  72  Unknown

So there is a driver for this device. Good luck!

---

