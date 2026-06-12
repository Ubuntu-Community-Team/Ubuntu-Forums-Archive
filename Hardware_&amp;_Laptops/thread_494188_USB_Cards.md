---
title: "USB Cards"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Whitewater155 on 2007-07-06
Hey everyone,

I'm new here and fairly new to Ubuntu.

I'm currently running Xubuntu 7.04 on an old Pentium 3 600 Mhz 256 Ram with USB 1.1. I want to get a USB 2.0 card for it. I don't want to spend a lot of money on it though since it is an old computer. I do most of my online computer part shopping at ZipZoomFly or NewEgg.

I'm looking at getting the **Syba SD-V2-5U PCI USB 2.0 4+1 Port Controller Card**. It's based on the 
**NEC uPD720101 chipset **which will work under Linux. My question is since it's based on a chipset that works under linux, will the card work?

Thanks in advance
David

---

### Post by geraldm on 2007-07-06
I have a Syba card, no model numbers SD-V2-5U, and it works.
The kernel must have the eci_hcd.ko module; otherwise it falls back to 1.1 speeds.
I expect your card would work without any hassle.
Gerald

---

### Post by Whitewater155 on 2007-07-06
Hey Gerald,

Thanks for the quick reply.

Is the eci_hcd.ko module something I have to have the kernel load or is it loaded already in the generic kernel? I know when I was running SuSE on my main computer, the modules for the USB were detected and loaded automatically.

David

> **geraldm said:**
> I have a Syba card, no model numbers SD-V2-5U, and it works.
The kernel must have the eci_hcd.ko module; otherwise it falls back to 1.1 speeds.
I expect your card would work without any hassle.
Gerald

---

### Post by geraldm on 2007-07-06
The module should be included in any recent generic kernel.  It was not
on mine, because I was using options from before the USB-2.0 was common,
and had making the kernel with an oldconfig .
Gerald

---

### Post by Whitewater155 on 2007-07-07
Hey Gerald,

Thanks again. I've ordered the card and will post my results so that everyone else will know if it works or not. I noticed there is a hardware compatability section to these forums.

David :D

> **geraldm said:**
> The module should be included in any recent generic kernel.  It was not
on mine, because I was using options from before the USB-2.0 was common,
and had making the kernel with an oldconfig .
Gerald

---

### Post by Whitewater155 on 2007-07-16
Hey everyone,

Here's the results for this usb card. I installed the card today, fired up the pc with Xubuntu 7.04. The card was auto-detected and the kernel modules were loaded automatically. I plugged in an external USB Hard Drive. It read the drive and transfered files from the drive at high speed with no problems.

This card was worth the $15 I spent on it. It has 5 ports total, 4 external and 1 internal.

Thanks
David :)

---

