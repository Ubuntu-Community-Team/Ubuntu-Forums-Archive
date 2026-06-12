---
title: "Lost my screen high resolution"
date: 2009-12-22
forum: Hardware
---

### Post by dannygeist on 2009-12-22
Hi
The screen resolution on the VGA screen connected to my laptop has gone down to 1024x768. Could be due to an upgrade I performed (I often do that when prompted by the package manager)

The screen is "Unknown" and in the display preferences of the gnome menu system thats the max resolution.

I have a laptop with an Intel GMA 4500MHD
The monitor is a really a 22 inch noName with max resolution of 1680x1050 (and it worked until yesterday)

I tried:

1. changing /etc/X11/xorg.conf like the examples in some of the forum threads.

2. Upgrading the intel driver via the synaptic package manager

Thanks,
Danny

---

### Post by dannygeist on 2009-12-22
I added a line:
 Driver        "Intel"
in the Device section of /etc/X11/xorg.conf

Now when I used
 xrandr
 all of the sudden the high resolution modes appeared. 

I did

xrandr -s 1680x1050 

to switch and it worked

Danny

---

