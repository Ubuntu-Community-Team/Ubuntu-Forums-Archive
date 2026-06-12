---
title: "Help with Grub"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by anfy on 2008-12-28
Hi,

I am relatively new to linux, and I've been trying it out a bit on my Aspire One laptop.

At the moment, I am trying to boot my aspire one into the Linpus linux installed on a SDHC card (Linpus itself is not booting, but that's a different question for a different forum). The problem is, the internal SD expansion slot is wired via PCI-E (apparently), and the BIOS doesn't pass pcie to Grub when it is booting.

Currently, I have Win7, XP, and Ubuntu triple booting, with the Win7 bootloader as default, chainloading Grub to boot Ubuntu.

According to the SVN version of grub on savannah, support for SD/MMC loading has been added. However, after downloading the SVN version and attempting to install it (using the included install guide), nothing apparently changed in Grub. The version number is still the same, and it still doesn't see the SD/MMC card. I heard that there might be a way to add the sdhc-pci module to the Grub kernel and compile it, but I'm not sure how to do that, and nobody else has apparently been able to do it.

Another way to do this is to move the /boot folder from the SDHC card to another partition on my internal hard drive, have grub boot into that partition, then have that partition load sdhci-pci, sdhci, mmc_block, etc, which loads the SDHC card, then boot into Linpus. I'm not entirely sure how this is done either.

Knowing the above two methods might work, I don't really want to create any more partitions on my internal HDD (got 6 or 7 partitions on that thing already), so is it possible to move the /boot folder from the SDHC to another folder (e.g. /bootlinpus) on the Ubuntu partition, and point grub there, and use method 2 above to boot into the SDHC?

I hope that this is not too complicated, and if it's possible for grub to load the SDHC directly, that would be the best possible scenario. Help would be greatly appreciated.

Thanks

---

