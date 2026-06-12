---
title: "Disable dma during boot?"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by amp_man on 2007-03-24
Hi, I'm working on a CarPC and using an IDE->CF adapter. The CF disk supports DMA, but the adapter doesn't work correctly with DMA enabled, so it has to be disabled. The kernel, during boot, will discover this and take care of it, but it takes forever. Is there any kernel option that I can pass to disable dma at boot? Hdparm is useless, since it runs well after the kernel has loaded.

Thanks,
Amp

Edit: forgot to mention, I only want to disable dma for the CF, since I have a normal hard drive that works just fine with DMA enabled. The compact flash drive acts as my /boot and swap space (for sw suspend), and the normal hard drive has the root partition.

Another edit: If anyone ever finds this and needs this info, I decided to use ide=nodma during boot, then use hdparm to re-enable dma on the hard drive later in the boot process.

---

