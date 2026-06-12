---
title: "nvidia gtx750 ti in mac pro 1.1 no 16x pcie lane support"
date: 2015-01-05
forum: Hardware
---

### Post by millerthegorilla on 2015-01-05
Hi, I have just bought an Nvidia GTX 750 ti (asus) and want to fit it to my Mac Pro 1.1 running lubuntu.  I know there is a bottleneck as the motherboard only supports pcie 1.1 spec but I wanted the open gl 4.4 support.  The card works ok with the Nvidia Proprietary Driver, but only in slot 2 or 3 where I can only get 1 lanes worth of bandwidth and it seems to be running at 1 speed rather than 4.

The main slot is slot 1.  This runs at 1.1 but with 4 lanes of 4 speed, so 16x bandwidth.  However, when I fit the card to slot 1 the machine does not detect it, so at the moment I am running it in slot 2.  It works and I get the pretty graphics but at such slow speeds I might as well stick with my 8800gts.

I have tried using a load of different boot options for grub, and have just recompiled my kernel, but to no avail.

Does anyone have any suggestions?  I know that if I were able to install osx there is a pci lane configuration utility, but I don't know how to get it working on linux.  Is it possible to flash nvidia roms under linux?

Many thanks in advance.

---

