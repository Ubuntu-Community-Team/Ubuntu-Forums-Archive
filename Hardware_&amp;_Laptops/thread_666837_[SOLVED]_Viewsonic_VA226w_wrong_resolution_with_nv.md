---
title: "[SOLVED] Viewsonic VA226w wrong resolution with nvidia-legacy"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Paul Moir on 2008-01-13
When using the restricted nvidia-legacy driver on a NV34 card, my Viewsonic VA226w was  detecting 1400x1050 even though the driver was going to 1680x1050, causing fine fonts and such to look bad.  The problem wasn't present with the nv driver.

If anyone else runs into this problem, the solution is to simply add this modeline to the Monitors section of /etc/X11/xorg.conf file:

```
Section "Monitor"
... 
        Modeline "1680x1050"   146.25   1680 1768 1944 2240   1050 1053 1059 1089 +hsync -vsync
...
EndSection

```

If there are any other Modelines referring to 1680x1050, they should be commented out or deleted.

This corrects the mis-detection and centres the display up nicely.

---

