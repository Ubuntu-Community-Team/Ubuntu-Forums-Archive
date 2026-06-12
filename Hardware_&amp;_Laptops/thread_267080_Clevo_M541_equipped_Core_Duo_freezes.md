---
title: "Clevo M541 equipped Core Duo freezes"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by kecsap on 2006-09-28
Hi,

I have installed an Ubuntu 6.06 LTS on my Clevo notebook which has the following elements:

Processor: Core Duo 2000 Mhz
Chipset: Intel 945GM + ICH7-M
Videochip: Intel Graphics Media Accelerator 950

If I'm using a kernel without SMP support (only one core), everything is fine and no problem. But if I'm booting with a kernel with SMP support, then the notebook logs in perfectly (all devices are working, I see the two core in statistics and gnome is logged in), but the notebook freezes randomly (after 1-30 minutes). I have tried more version of the kernel images 2.6.15-23-686, 2.6.15-27-686 and the result is the same.

I found such an option "Core scheduler" in kernel 2.6.18, but this kernel is too unstable on my notebook.

Has anybody idea?

Thanks,
  kecsap

---

### Post by kecsap on 2006-11-02
I figured out that the problem was the ndiswrapper....it's freezing and must install the newest version...

---

