---
title: "Asus a7a266 motherboards, ali magik chipset dma problems [solved]"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by reformist on 2005-05-20
If you have na asus a7a266 motherboard, or another motherboard with an ali magik chipset, then you may have problems turning DMA on when you boot into ubuntu hoary hedgehog. This chipset is flaky with many kernel versions and with large disks; kernels greater than 2.6.8  but less than 2.6.12 will crash if you try and turn on dma for drives hooked up to this chipset. Hoary ships with a 2.6.10 kernel, which does not support this chipset.

The problem has been documented throughout the history of the motherboard, and most recently here:
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg00704.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg00704.html)

Thankfully, with a patch attached, which fixes the errors and allows you turn on dma with this chipset without crashing. The patch was applied sometime during the 2.6.11 series. To get it in your kernel, you can either build a 2.6.11 (not sure which version has the patch in it) or 2.6.12 kernel manually, or, you can get the 2.6.12 kernel in the breezy archive, which is packaged nicely, in the same fashion as the hoary kernel. Beware, the breezy kernels are under heavy development and testing and may cause breakage. At the time of writing, the kernel upgrade was very smooth and without problems. It is the only package I use from breezy.

To get breezy packages, change your /etc/apt/sources.list file to refer to "breezy" rather than hoary (you can also make this change through Synaptic package manager).

---

