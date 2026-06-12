---
title: "TI SD Card Help"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by onewordanswer on 2007-05-31
I have a TI internal SD card reader on my laptop. I am running Feisty with the 2.6.20-16 kernel. I cannot get the card to work no matter what I do. I've probably tried 1000 things. Please help me out! PS: Dmesg does not respond to inserting or removing the card.

lspci output:
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

dmesg output.
[   11.456000] sdhci: Secure Digital Host Controller Interface driver
[   11.456000] sdhci: Copyright(c) Pierre Ossman
[   11.456000] sdhci: SDHCI controller found at 0000:03:0b.3 [104c:803c] (rev 0)
[   11.456000] sdhci: SDHCI controller found at 0000:03:0b.3 [104c:803c] (rev 0)
[   11.456000] mmc0: SDHCI at 0xff8ff700 irq 19 DMA

tifm_core, tifm_sd, mmc_core, mmc_block, tifm_7xx1, and sdhci are all loaded. The SD card is not defective.

---

### Post by onewordanswer on 2007-05-31
Update: I restarted the computer, and it mounted. However, the next time I rebooted, it acts like nothing ever happened. I saved logs of what it said when it mounted:

[   14.352000] mmc0: SDHCI at 0xff8ff700 irq 19 DMA
[   14.624000] mmcblk0: mmc0:9ffc SD01G 992000KiB
[   14.624000]  mmcblk0: p1

---

### Post by fishyf on 2007-07-12
I'm having a similar problem. Did you manage to get this sorted yet.

In my case, I install an XD card which is recognised by dmesg
```

tifm0 : demand removing card from socket 0:0
tifm_core: SmartMedia/xD card detected in socket 0:0
```

Sees it being removed and inserted again.

It wasn't automounted so I searched in /dev using ```
sudo find /dev -name "*xd*"
``` and I see

/dev/.udev/failed/%2fdevices%2fpci0000:00%2f0000:00:1e.0%2f0000:03:0b.2%2ftifm_xd0:0

Anyone know what this means?

---

### Post by goomior on 2007-08-10
I have the same problem. The card in general doesn't mount, but sometimes (very rarely) it is recognized and mounted.
```
#dmesg | grep mmc
[   19.676000] mmc0: SDHCI at 0xff8ff700 irq 19 DMA
```
```
#lsmod | grep tifm
tifm_7xx1               8960  0 
tifm_sd                12808  0 
tifm_core              11396  2 tifm_7xx1,tifm_sd
mmc_core               26756  2 tifm_sd,sdhci
```
My laptop: Toshiba Tecra A8-183

---

### Post by gottferdamnt on 2007-08-10
> **fishyf said:**
> I'm having a similar problem. Did you manage to get this sorted yet.

In my case, I install an XD card which is recognised by dmesg
```

tifm0 : demand removing card from socket 0:0
tifm_core: SmartMedia/xD card detected in socket 0:0
```

Sees it being removed and inserted again.

It wasn't automounted so I searched in /dev using ```
sudo find /dev -name "*xd*"
``` and I see

/dev/.udev/failed/%2fdevices%2fpci0000:00%2f0000:00:1e.0%2f0000:03:0b.2%2ftifm_xd0:0

Anyone know what this means?

I can't read xD card on my laptop (a dell inspiron 6400), It's not recognised by dmesg at all.

---

