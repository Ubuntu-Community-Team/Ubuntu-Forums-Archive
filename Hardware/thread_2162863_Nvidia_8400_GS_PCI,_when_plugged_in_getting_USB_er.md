---
title: "Nvidia 8400 GS PCI, when plugged in getting USB errors"
date: 2013-07-16
forum: Hardware
---

### Post by hgu on 2013-07-16
I recently plugged in an Sparkle Nvidia GeForce 8400 GS **PCI**-card in my computer, when doing so it seemed to work with the noveau drivers (but extremely slow) but not with the nvidia drivers. When the nvidia drivers are used I get USB error like this:
[   16.644064] usb 1-3: device not accepting address 2, error -110
I don't get a graphical display either, but the non-X works. I run Ubuntu 12.04 and was using the nvidia current drivers (installed from settings -> hardware). I have a ABIT IL-90MV 945GT Mobile motherboard with built-in Intel GPU, its an 32-bit machine.

Is the USB error unimportant, is it a hardware fault on the card, or is it just so that I should continue fiddling with the xorg.conf to get it working? Any ideas for how I should figure out which is the likely problem?

---

