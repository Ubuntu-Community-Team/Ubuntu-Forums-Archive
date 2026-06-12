---
title: "Intel NUC Experiences - 14.04.02 LTS vs 15.04"
date: 2015-06-09
forum: Hardware
---

### Post by remerson on 2015-06-09
Hello,

I got a NUC5i3RYH a couple of months back and installed 14.04.2 LTS on it. Initially, I was pleasantly surprised to find it actually worked at all. For the first month, it was all good and I was really happy. A few kernel/package updates later, things have been going downhill:

- Bluetooth module (Intel AC7260) occasionally vanishes after resume from suspend. The kernel does not see the hardware. The NUC needs to be power cycled for the module to come back; a reboot isn't enough. This seems to an issue with the Intel Bluetooth module and power states, rather than the NUC itself. Avoid Bluetooth mouse.
- Intel graphics driver has corruption/stability issues; going back to the older UXA driver is a workaround but is sluggish/much slower than the snappy SNA driver. [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1432194](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1432194)
- Resume from suspend not working properly. Particularly, the power button does not always work to bring the NUC out of suspend, and the latest Intel 0247 BIOS makes this worse for me despite containing an "Ubuntu suspend fix." In this situation, if you pull the power on the NUC you'll brick it (!). This is a hardware/software interaction.
- A silly little issue with UEFI /boot being default sized just about big enough for two and a half kernels, causing unnecessary wasted time every new kernel upgrade happens, as I need to go and manually remove stuff.

Suspend is a critical feature for me. Even going back to the previous Intel 0246 BIOS, I still get often (1 in 4?) failures to resume from suspend - just a black screen, or no monitor signal and interactive/keyboard terminal login/X all completely unresponsive. Power-cycling is the only option. With the latest 0247 BIOS, it's about 50/50 whether the power even button works to bring the NUC back at all.

I'm drawing the conclusion that this hardware isn't ready for prime time and may well toss it.

But...! Wait!

What about 15.04? It's not ideal but if it works (suspend/graphics) then it's an option - I can also fix the stupidly sized /boot if I re-install.

Is 15.04 any better? It's on a later kernel and I believe has "native" Broadwell graphics support, rather than being backported.

Please share your 5th-gen NUC 15.04 experiences!!

---

