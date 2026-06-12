---
title: "Using the 686 kernel results in kernel panic"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by vandal43 on 2005-06-06
Hi guys,

I've been trying without vain to get a 686 optimized kernel running on my system. This happens with any distro I've tested that uses such a kernel, but the 386 one seems to work fine. I'd be curious if anyone can help me shed some light on this as I'd really like to be able to run against the later optimizations. My system specs are:

P4 3.2GHz 775 w/ HT
MSI 915P mother board
120 GB SATA drive.

I've googled all over without success, from what I read, it might be a SATA controller issue? Or a motherboard chipset problem? Any help would be greatly appreciated.

---

### Post by N'Jal on 2005-06-06
Na i can't see it being a sata problem coz i have an IDE drive with a simelar issue, bits of the kernel load but others don't that normally do in the i386.

Tried the repo's and tryed 'rolling my own' though i don't know is i have ever successfully compiled a kernel.

---

### Post by vandal43 on 2005-06-08
Finally found a solution to this, seems to be a result of the MSI motherboard of all 915 chipset flavors. Anyway, just add pci=nosort to the kernel line in GRUB.

---

