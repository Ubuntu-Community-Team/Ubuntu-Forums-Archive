---
title: "Unable to get two GPUs to coexist under 8.10"
date: 2009-07-21
forum: Hardware
---

### Post by timmiroon on 2009-07-21
Hi,

I'm having problems installing two GPUs in a single machine under itchy ibis?! Ubuntu 8.10. Basically I have a GTX 295 which I want to use exclusively for CUDA work and a 9400 GT which I want to use exclusively for graphics. When both cards are physically installed I get the old 'fatal error: no screens found' from Xorg however when only one is installed, it doesn't matter which, there are no problems at all. 

In /etc/X11/xorg.conf for "Device" the only entries are:

-Identifier "Screen0"
-Driver "NVidia"
-VendorName "NVIDIA Corporation"

Perhaps there is something missing here so that Xorg addresses the correct card in the event that more than one are present. That seems reasonable to me but I've no clue what should be there...

Any help much appreciated!

---

