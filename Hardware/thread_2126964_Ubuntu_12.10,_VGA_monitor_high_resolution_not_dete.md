---
title: "Ubuntu 12.10, VGA monitor high resolution not detected - low resolution only"
date: 2013-03-18
forum: Hardware
---

### Post by peterny on 2013-03-18
Clean Ubuntu 12.10 (64-bit) install on a new PC (Shuttle XH61V, Intel Core i3 - 3220T, Intel HD 2500 grahpics).

My VGA Monitor is connected via a DVI to VGA adapter (no direct VGA interface available), and resolution is automatically set to 1024x768.
System settings / display show only resolutions 1024x768 and 800x600.

I need 1280x1024 resolution, and I know for sure my monitor can do this (works without problems on another PC (Asrock core 100ht) with Ubuntu 12.10 (worked also with several earlier Ubuntu versions also).

Don't know whether the problem could be related to the the DVI to VGA adapter or to the Shuttle system/graphics card/driver.

I can actually make 1280x1024 work, kind of, doing:
$  xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

$  xrandr --addmode VGA1 1280x1024_60.00

$  xrandr --output VGA1 --mode 1280x1024_60.00

However, after this my system will not boot correctly (either black screen, or a screen notifying of a graphics problem, which cannot be resolved.

Any suggestions to make 1280x1024 resolution work correctly?

Thanks,

/ Peter

---

