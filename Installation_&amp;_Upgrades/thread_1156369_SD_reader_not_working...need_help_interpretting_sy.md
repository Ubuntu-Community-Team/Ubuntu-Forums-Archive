---
title: "SD reader not working...need help interpretting syslog"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Scipio_Publius on 2009-05-11
I have been trying to get this SD card reader working.  I have an Acer Aspire One netbook with 8gig flash memory and 2 SD readers on left and right side of the box.  I get the below syslog messages after doing a mount -a



```
May 11 12:06:12 imp kernel: [    7.151622] sdhci: Secure Digital Host Controller Interface driver
May 11 12:06:12 imp kernel: [    7.151630] sdhci: Copyright(c) Pierre Ossman
May 11 12:06:12 imp kernel: [    7.157417] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
May 11 12:06:12 imp kernel: [    7.157463] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 11 12:06:12 imp kernel: [    7.158076] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
May 11 12:06:12 imp kernel: [    7.158110] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
May 11 12:06:12 imp kernel: [    7.158147] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 11 12:06:12 imp kernel: [    7.158164] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
May 11 12:06:12 imp kernel: [    7.158179] sdhci-pci 0000:04:00.2: PCI INT A disabled
```

If I plug or unplug the card from the interface I get the following log message.

```
May 11 13:00:16 imp kernel: [ 3255.643127] mmc0: error -84 whilst initialising SD card

```

Anyone know what these logs mean and better yet how can I fix the issue.

---

### Post by Scipio_Publius on 2009-06-08
My SD card says its made by samsung.  It works in other devices but not my acer after upgrading to ubuntu.  I stuck a sandisk SD card in the reader and it works fine (hot pluggable).  

Conclusion:  Driver issue?  All SD cards are equal but some are more equal then others.

---

### Post by evil_LT on 2009-06-26
I have the same problem - SD reader works with only Sandisk SD cards. I tested with 2GB and 4GD SDHC Sandisk - works perfect. Also tried 1GB and 4GB SDHC A-DATA cards - no luck, the same error -84.

---

