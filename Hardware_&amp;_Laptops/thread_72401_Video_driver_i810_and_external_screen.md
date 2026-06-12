---
title: "Video driver i810 and external screen"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by edoardo on 2005-10-06
Running Colony5 on a Dell D610 (which comes with the i195 chipset).
installed fine, xorg uses i810 driver.

when connecting the laptop to external screen Dell 2001FP capable of 1600x1200
the screen is a virtual 1600x1200 but panning a 1400x.. or 1280x...

if I cahneg the xorg driver to vesa, I get the native 1600x1200 but the graphics are noticebaly slower, even for development work.

anyone know how to get the 1600x1200 using the i810 driver ?

looking at the log, I believe the problem is 

*(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 160MHz

thanks,
Edo

---

### Post by heimo on 2005-10-06
What kind of refresh rate do you get using vesa driver? I think the problem is that modes exceed dot clock - graphic cards ability to drive the signal and lowering refresh rate a bit should help - but if I'm correct that would mean vertical refresh rate at 59Hz which is ... quite low.

You can test my theory by putting this line to your monitor section of /etc/X11/xorg.conf file:
 ```

# 1600x1200 @ 59.00 Hz (GTF) hsync: 73.22 kHz; pclk: 158.15 MHz
  Modeline "1600x1200_59.00"  158.15  1600 1704 1880 2160  1200 1201 1204 1241  -HSync +Vsync

```

---

### Post by edoardo on 2005-10-06
[QUOTE=heimo]What kind of refresh rate do you get using vesa driver? I
[/QUOTE]
the OSD for my external monitor says 1600x1200@60Hz

I'm going to try your modeline now

---

### Post by edoardo on 2005-10-06
your modeline WORKS. The OSD reports 1600x1200@59Hz

thanks!

now I have to go and find how to write modelines to experiment and maybe push further. any links BTW ?

---

