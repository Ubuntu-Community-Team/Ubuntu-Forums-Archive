---
title: "scrolling with mouse pad"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by domurtag on 2006-10-09
Hi,

I have Ubuntu 6.06 installed on a Toshiba Satellite laptop (and I love it dearly).

Is it possible to enable vertical (or horizontal) scrolling when you drag your finger down the right-hand side (or bottom) of the mouse pad?

Cheers,
Don

---

### Post by domurtag on 2006-10-15
Figured it out!

My xorg.conf used to look like this:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

I removed the "HorizScrollDelta" line, and I now have the scrolling behaviour I wanted

---

