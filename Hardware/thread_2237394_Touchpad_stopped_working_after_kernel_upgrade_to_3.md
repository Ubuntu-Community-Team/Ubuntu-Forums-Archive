---
title: "Touchpad stopped working after kernel upgrade to 3.13.0-32"
date: 2014-08-01
forum: Hardware
---

### Post by pgratz on 2014-08-01
I recently performed an an apt-get upgrade on my HP Spectre 13 X2 which installed a new linux kernel and it appears to have broken support for my laptop's touchpad (touch screen still works though).  The upgrade took me from 3.13.0.30-generic to 3.13.0.32-generic.  When I boot back to 3.13.0.30 the touchpad works again.  I also noticed that in the new kernel the touchpad is not listed in xinput (nor can it be seen under /proc/bus/input/devices).   For now I'm booting to -30 but that probably isnt a good long term solution.

Incidentally, this is listed a synaptics touchpad V 1.03U2 (when the kernel can detect it).

Thanks for any help!
Paul

---

### Post by pgratz on 2014-09-17
I just wanted to bump this back up to the top.  I still have this problem even with the latest kernel. 3.13.0-35-generic.  Does anyone have any advice on how to go forward?  It would be bad if 14.10 no-longer supported my mouse...

---

