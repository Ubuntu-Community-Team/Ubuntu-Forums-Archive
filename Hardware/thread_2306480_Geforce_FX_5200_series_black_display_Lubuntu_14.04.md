---
title: "Geforce FX 5200 series black display Lubuntu 14.04"
date: 2015-12-15
forum: Hardware
---

### Post by Smokin Whale on 2015-12-15
I've since moved back to Windows XP, but for anyone attempting to install Lubuntu 14.04, just be aware that no Geforce FX 5xxx series cards work. This probably includes the FX 5500, FX 5600, FX 5700, FX 5800 and cards along those lines. I can get a display if I boot to recovery mode, but that's about it. Tried on a 1080p and an older 1280x1024 display. It's ancient so I'm not going to bother diagnosing, so I thought I'd create a thread to give people the heads up if they want to get their old hardware going.

Weirdly enough, I have a Radeon 9200SE in another PC that works just fine in Lubuntu at 1080p. I don't even think that one supported DX9.

---

### Post by chrisllemay on 2015-12-15
I had similar issues with Mint and some other Ubuntus based Distros with FX5200 cards. When you boot add nomodeset option to the initial boot, then install your operating system. On reboot use safe mode and then install nvidia drivers.  At least that worked for me. 

If the correct driver don't show up in the Additional Drivers utility I use this procedure:  [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

Chris

---

