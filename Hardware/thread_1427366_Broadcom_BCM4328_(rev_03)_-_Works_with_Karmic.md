---
title: "Broadcom BCM4328 (rev 03) - Works with Karmic"
date: 2010-03-11
forum: Hardware
---

### Post by sjanarth on 2010-03-11
Apologise if this has been posted before.

To cut a long story short:

Ubuntu 9.10 Karmic Koala brings some good improvements with it. If you are one of those forsaken souls using bcm4328 with nvidia or have troubles with your usb audio driver or multiple monitors, you should seriously consider upgrading to 9.10.

I have a Broadcom BC4328 (rev 03) wireless adapter on my HP dv6500z. I had to go through hoops to do wireless with Gutsy, Hardy and Intrepid. The restricted drivers did not seem to work for me and I had to fall-back to using ndiswrapper. I also have an NVIDIA display card. ndiswrapper and nvidia apparently do not go well together - random crashes, screen freezes requiring hard reboots (something to do with IRQs I read).

I'm a great fan of ubuntu and did not want to switch back to Windows just because wireless wasn't working well. I tried the 9.10 live CD without installing from it. Surprisingly, after enabling the restricted drivers (the wl1 driver), wireless worked like a charm. Some of my problems with usb sound and multiple monitors are also gone.

I decided to install 9.10 fresh over my existing 8.10 installation. After installation, tried enabling the restricted drivers and it will not activate (no error messages/dialogs too). I was pretty sure 9.10 had support for my wireless card as the live cd worked like a charm.

I had to enable the CDROM repository in Synaptic Package Manager > Settings > Repositories, insert the live cd and tried installing the restricted driver - it installs and works fine.

---

