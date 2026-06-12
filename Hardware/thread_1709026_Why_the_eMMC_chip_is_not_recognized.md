---
title: "Why the eMMC chip is not recognized?"
date: 2011-03-17
forum: Hardware
---

### Post by Fanatico on 2011-03-17
I have Intel Atom based development board which has eMMC chip.
I can successfully boot Ubuntu on this board from SATA drive.
However Ubuntu doesn't see this eMMC chip as external storage.
The "fdisk -lu" command doesn't show presence of any mmc device.

Can anyone advise how to start to troubleshoot this problem?

Here is part of boot log that might help to understand the problem:

Mar 10 12:46:03 localhost kernel: Registered led device: mmc0::
Mar 10 12:46:03 localhost kernel: mmc0: SDHCI controller on PCI [0000:02:04.0] using DMA
Mar 10 12:46:03 localhost kernel: sdhci-pci 0000:02:04.1: SDHCI controller found [8086:880a] (rev 1)
Mar 10 12:46:03 localhost kernel: sdhci-pci 0000:02:04.1: Invalid iomem size. You may experience problems.
Mar 10 12:46:03 localhost kernel: Registered led device: mmc1::
Mar 10 12:46:03 localhost kernel: mmc1: SDHCI controller on PCI [0000:02:04.1] using DMA
Mar 10 12:46:03 localhost kernel: mmc0: unrecognised EXT_CSD structure version 3
Mar 10 12:46:03 localhost kernel: mmc0: error -22 whilst initialising MMC card

What do the last two error messages mean?

Thanks

---

