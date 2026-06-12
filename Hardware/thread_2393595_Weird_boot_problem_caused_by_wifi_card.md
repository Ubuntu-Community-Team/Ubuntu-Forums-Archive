---
title: "Weird boot problem caused by wifi card"
date: 2018-06-05
forum: Hardware
---

### Post by pidgin08 on 2018-06-05
Hi all, I hope someone will be able to help with this as I've tried everything I can think of. I am running Xubuntu 16.04

I recently brought a new PCI express wifi card (Gigabyte GC-WB867D-I) which runs on an intel chip. Initially the PC booted fine but only the bluetooth on the card worked, not the wifi. I found that this was because I had an older kernel version (4.4.something) and the drivers were only included in kernels 4.6 and later. I upgraded my kernel and the card appeared to work fine after that.

However recently there has been a weird problem. The PC will not boot past the BIOS splash screen on the first attempt, instead it continually reboots immediately on reaching the splash screen. I cannot even get into the BIOS. If I remove the card then the PC boots fine and everything else works as expected.

Bizarrely I have found that if I reinsert the card, that the PC will boot correctly the first time and everything (including the wifi!) works fine in xubuntu. However as soon as the PC is rebooted the same restart loop occurs. Until I remove the card, reboot once, then reinstall it and it works fine again for one more boot!

Any help greatly appreciated.

---

