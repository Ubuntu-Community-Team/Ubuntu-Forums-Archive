---
title: "Dell Latitude D600 resolution problem."
date: 2009-10-14
forum: Hardware
---

### Post by arkashkin on 2009-10-14
Hello every body.
For along time a have a problem to setup the screen of my laptop for it's maximum resolution. I have found on the internet some workaround of somebody who uses Kubuntu:

> 
Dell Latitude D600 still shows the bug running karmic beta 1:
Displaysize is notauto detected and dpi set to 96 dpi instead of the
real 124 dpi.  With the size im mm adjusted to the artificial 96dpi.
xdpyinfo:

...
screen #0:
 dimensions:    1400x1050 pixels (370x277 millimeters)
 resolution:    96x96 dots per inch
...


Workaround: as karmic does not use xorg.conf in the default setup, I've modified /etc/kde4/kdm/kdmrc to
start the xserver with the options -dpi 124.

Sadly, it looks like radeon driver will never get it right :(
Achim

Please tell me how I can start the xserver with the options -dpi 124 in _Ubuntu_.
Thanks a lot.

---

