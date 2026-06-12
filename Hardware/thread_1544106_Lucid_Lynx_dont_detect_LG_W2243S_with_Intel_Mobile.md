---
title: "Lucid Lynx dont detect LG W2243S with Intel Mobile 4 Series"
date: 2010-08-02
forum: Hardware
---

### Post by Don_Jorgito on 2010-08-02
Hello,

I have installed a Ubuntu Lucid Linux 10.04 64 bits desktop into a Toshiba PORTEGE M800.

This laptop comes with a Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

My problems is that I have an external monitor LG W2243S, that support 1920x1080, but xrandr command dont detect this resolution.

I try it with another laptop, and it works fine, it detects LG W2243S as Goldstar 22'' and I can set the higher resolution. But in the PORTEGE M800 with Intel Mobile 4 Series i cant.

Thank you for your help!

---

### Post by efflandt on 2010-08-02
man xrandr

You can use xrandr to add video modes.  You could find modelines with **cvt 1920 1080** or **gtf 1920 1080 60**.

This is an example of a script I use on a laptop for an LG 32" HDTV based on what /var/log/Xorg.0.log showed for the modeline for DVI to HDMI connection on another computer.  Even though the laptop display is 1280x800, when both were connected it tended to come up with both as 1024x768.  It is somewhat different than cvt or gtf show, but my HDTV is set to Just Scan, so it auto sync's to it.  Although, you may need to change device names based on what xrandr shows for yours.

#!/bin/bash
# Set external monitor resolution
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
# switch off laptop display
xrandr --output LVDS1 --off
# switch external to 1080p
xrandr --output VGA1 --mode 1920x1080_60.00
exit

If you create a **bin** directory in your home directory you could put it there (would be included in your PATH next time you login).  Then you could put a launcher on your desktop or top panel to run it with double click.

---

### Post by Don_Jorgito on 2010-08-03
Thank you efflandt!!

LG W2243S still shows it as 'Unknown monitor' but using your script to add new modes to xrandr now I can set 1920x1080 resolution.

---

