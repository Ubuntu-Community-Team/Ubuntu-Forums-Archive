---
title: "HP Pavilion A64 X2 - SATA trouble"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by daffy_ on 2005-11-14
I have a HP Pavilion w5296 (similar to w5295). It has the MSI MS-7184 motherboard (ATI Radeon Xpress 200 chipset).

However, I can't get any of the linux-distro's I have tried to be able to read my s-ata drive. So I believe that the S-ATA controller is not supported (out of the box) as of now. Has anyone got any ideas on what I can do to fix this? (Other than changing motherboard...)

I have no free pci slots, so a new s-ata controller is out of the question.

Further research: It seems that the culprit is the ATI SB400 chipset (southbridge). I have noticed several people having this chipset and having trouble with the s-ata controller. I tried the RR4 distro (release 2.65), since it had the 2.6.14 kernel, and I was able to boot the system just fine. It also was able to display my hard-disk partitions, although not the content of them. So I believe that support for this controller is in the making. But until then, I'm stuck in window-land ! :(

(Unless someone can help me out of this mess?)

---

### Post by daffy_ on 2005-11-17
Apparently, the controller uses the sata_sli driver, but is not correctly recognized. Is there a way to specify what driver to use during boot? I am currently running opensuse 10.0, and I really really miss apt-get/aptitude.

The only distro's I've found that correctly recognizes my controller are opensuse 10.0 and Fedora Core 4 (FC4).

---

