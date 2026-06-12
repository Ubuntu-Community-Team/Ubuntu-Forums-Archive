---
title: "8GB CF-&gt;SATA drive shows up as 283GB"
date: 2008-09-12
forum: Hardware
---

### Post by algernon83 on 2008-09-12
I just got an Asus M2N-VM DVI motherboard with nForce 630a chipset. I've connected a Syba CompactFlash->SATA adapter to it with an 8GB CompactFlash card. The BIOS correctly shows it as an 8GB card. However, when I boot the latest Ubuntu AMD64 live CD, GParted, Parted, and FDisk all think that the card is 283GB. GParted can make and delete partitions but can't format them. Why does Ubuntu misinterpret the size of this disk?

---

### Post by Toet on 2008-09-12
I tried this once with 2x 4GB to ATA, to get them in striped raid. Imagine the speed ;)

But it did not recognize the CF cards, because Linux (I guess the kernel) gave them the wrong amount of heads, cylinders and stuff. I remember to have set these manually, but that still got overruled by the Linux.

Tried several distro's, but all the same.

Ended up selling the cards to some photo enthusiasts, they were very high speed anyways, so they sold quite fast.

I hope you have more luck on setting this up.

---

### Post by algernon83 on 2008-09-12
Thanks for the info! I almost didn't mention that it was an adapted CF card since it's supposed to be transparent to the OS.

I found that there's a kernel parameter to specify the drive geometry (sda=xxx,xxx,xxx), but entering it there didn't make a difference. I tried changing the cylinders, heads, and sectors with fdisk but the change isn't saved after writing the partition table. I'm not sure what to do now.

---

