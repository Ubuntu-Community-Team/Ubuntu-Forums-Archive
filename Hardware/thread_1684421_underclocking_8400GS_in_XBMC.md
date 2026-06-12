---
title: "underclocking 8400GS in XBMC"
date: 2011-02-09
forum: Hardware
---

### Post by mihaiii on 2011-02-09
Any ideas on how can i do this? or at least activate powermizer (different frequencies for idle / playing movies?)
I installed XBMC from live CD to a usb drive
i have Option "Coolbits" "1" in xorg.conf

i tried nvclock and i get:

nvclock -n 312

Error: NVClock doesn't offer lowlevel overclocking on NV50/G8x/G9x/GT200 hardware (yet).
If you want to overclock your card using the Nvidia drivers instead add the line:
 Option "Coolbits" "1" to the screen or device section in your xorg.conf and then try NVClock again.

or 
nvclock -b coolbits -n 310

Can't switch to the Coolbits backend because X isn't loaded

Any ideas on how can i run X?

---

