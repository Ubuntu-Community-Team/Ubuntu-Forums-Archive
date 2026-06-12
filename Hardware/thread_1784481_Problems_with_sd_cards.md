---
title: "Problems with sd cards"
date: 2011-06-17
forum: Hardware
---

### Post by grillosolitario on 2011-06-17
Hello,

I'm using Ubuntu 11.04 over a DELL XPS laptop I bought months ago. If I boot the PC with an SD card inserted in the laptop SD slot, it is detected and mounted. If I unmount it, and it's removed and placed again, it is automounted again.

However, if I boot the PC without the card, if I insert it later, the system doesn't even detect it. A sudo fdisk -l just lists the hard disk partitions. It didn't happen in the same laptop using Ubuntu 10.10.

Doing lsmod when booting with and without SD card, the differences are:

nls_iso8859_1 12617 1
nls_cp437 12751 1
vfat 17335 1
fat 55505 1 vfat

mmc_block 17704 2
sdhci_pci 13623 0
sdhci 22720 1 sdhci_pci

I tried to load those modules from the terminal, but the system still doesn't detect the SD card. Any sugerence?

Thanks!!

---

