---
title: "does not work SD cardreader"
date: 2008-11-20
forum: Hardware
---

### Post by dog_simpson on 2008-11-20
ubuntu 8.04 / card - kingston SD 2gb

lscpi
> 07:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
07:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
07:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

lsmod | grep sd
> sdhci                  19076  0
mmc_core               51460  1 sdhci
sd_mod                 30720  6
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata

lsmod | grep mmc
> mmc_core               51460  1 sdhci

dmesg | tail
> [ 2251.887136] mmc1: unrecognised SCR structure version 1
[ 2251.887154] mmc1: error -22 whilst initialising SD card

how to solve this problem ?

---

