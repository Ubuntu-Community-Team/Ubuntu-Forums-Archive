---
title: "How Can a driver do this?"
date: 2008-07-16
forum: General Help
---

### Post by shamusl on 2008-07-16
I have a small vista partition on my drive (100gb), in the fresh windows installation I installed an nvidia driver, and a chipset driver. When the computer restarted, windows was dead. It wouldn't boot. So I decided my games weren't that important and decided to boot ubuntu instead (postponing me having to reinstall). When I booted into Ubuntu, my LAN was dead, it was not recognized at all. After a while of thinking I had thought resetting the CMOS would fix it, and it did. Was it the Chipset driver (in windows partition) that had stopped ubuntu from getting lan? Or just some other freak occurrence? And if so, how is this possible?

---

### Post by p_quarles on 2008-07-16
Basically, yes, it's very likely that the Windows driver is responsible for altering low-level settings on the device. I've heard of similar things on numerous occasions.

As for how it's possible: if the device manufacturer provides certain configuration procedure instructions to one developer (e.g., Microsoft), but does not provide these instructions to just anyone (i.e., the open source community), then it is possible for the former to both rely upon and control hidden features in the hardware that are not available to alternative kernels.

---

### Post by mempman on 2008-07-16
> **shamusl said:**
> I have a small vista partition on my drive (100gb), in the fresh windows installation I installed an nvidia driver, and a chipset driver. When the computer restarted, windows was dead. It wouldn't boot. So I decided my games weren't that important and decided to boot ubuntu instead (postponing me having to reinstall). When I booted into Ubuntu, my LAN was dead, it was not recognized at all. After a while of thinking I had thought resetting the CMOS would fix it, and it did. Was it the Chipset driver (in windows partition) that had stopped ubuntu from getting lan? Or just some other freak occurrence? And if so, how is this possible?


Yes its very possible that hardware drives from you windows install are changing the state of your hardwares, such that when you boot into ubuntu, the incorrect state settings are being read.

This type of incidents commonly occur with onboard audio codecs hardware.  Also, these problem are dependent on whether your windows is shutdown/suspended/hibernated.

---

### Post by thegodfaza on 2008-07-16
My desktop does this. Windows has to be set to allow WOL otherwise my networking doesn't work in linux. If you can't get into windows this trick works for me. Completely power down your machine and flip the power switch on the back so that your pc goes completely dead. It should take about 15-20 seconds. Then when you boot back up the networking should work.

---

