---
title: "Acer Aspire 4310 02  Micro Card Reader"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by Flyn on 2007-10-17
I've bought a new Acer Aspire 4310 Laptop which has a 02 Micro Card Reader. It  doesn't appear anywhere, and there is no mmc0 in /dev.
lspci reports the following:
```
0a:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```dmesg reports the following:
```
[   17.860000] sdhci: Secure Digital Host Controller Interface driver
[   17.860000] sdhci: Copyright(c) Pierre Ossman
[   17.860000] sdhci: SDHCI controller found at 0000:0a:06.2 [1217:7120] (rev 2)
[   17.860000] ACPI: PCI Interrupt 0000:0a:06.2[A] -> GSI 22 (level, low) -> IRQ 21
[   17.860000] sdhci:slot0: Unknown controller version (2). You may experience problems.
[   17.860000] mmc0: SDHCI at 0xdc002800 irq 21 DMA
```
Does anyone have a suggestion?

---

### Post by barlaventoexpert on 2008-01-27
Flynn,

Just wondering if you have made any headway with the card reader and broadcom wifi on the Aspire 4310.

If so can you advise how!

Many Thanks

---

### Post by excogitation on 2008-03-18
It seems like some people already got it to work,
but I would prefer if there was an easier fix.

[02 Micro 4-1 card reader doesn't work5]("https://answers.launchpad.net/ubuntu/+question/2535")

---

