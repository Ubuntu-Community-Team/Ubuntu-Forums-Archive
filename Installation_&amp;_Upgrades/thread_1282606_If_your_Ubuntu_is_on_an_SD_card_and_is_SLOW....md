---
title: "If your Ubuntu is on an SD card and is SLOW..."
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by maestrobwh1 on 2009-10-04
I find that if you install (at least Karmic) directly to an SD card, this will not generally be an issue so the installer may take care of this, but I installed it on a regular partition and decided I wanted it on on SD card (I used the dump command to copy the filesystem - another post), but when I booted from the card, it booted fast but was SO SLOW running, and was almost unusable with firefox.

At any rate, you can try this if you are running from an SD card:

Do this as root

Add to /initramfs-tools/modules
> 
mmc_core
mmc_block
sdhci
sdhci-pci 

Then run
> update-initramfs -u

Reboot.  

Wow, what a difference.

---

