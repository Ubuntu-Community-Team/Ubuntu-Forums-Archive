---
title: "Display Problem"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by arvindenrique on 2007-12-29
[SIZE="2"]i have an IBM thinkcentre pc with 17 inch monitor and intel 915gv motherboard.i am not getting a full screen display. i ve tried both 7.04 and 7.10 with no luck.the display size is much less than even in a 14 inch monitor.what is the problem.

my pc has 256 MB DDR2 533 MHZ ram installed in it.[/SIZE]

---

### Post by tgilber1 on 2007-12-29
You could try editing your system's xorg.conf file by adding the DisplaySize line in the Monitor section.  Make sure you backup your xorg.conf file before editing.

1.  Measure the width and height of your display with a ruler.  If you do not have a metric ruler, then use the formula 25.4*"width in inches" & 25.4*"height in inches."
2.  Edit the xorg.conf and populate something similar to what is below.
3.  Restart gdm or <CTRL>+<Backspace>

File: /etc/X11/xorg.conf

Section "Monitor"
    Identifier          "Monitor0"
    :
    DisplaySize         340 270 # display width & height
    :
EndSection

Note:  You can check to see what your system is reading for a display size with the following command "xrandr --query"

---

