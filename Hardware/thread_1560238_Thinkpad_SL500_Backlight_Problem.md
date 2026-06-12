---
title: "Thinkpad SL500 Backlight Problem"
date: 2010-08-24
forum: Hardware
---

### Post by CompBio on 2010-08-24
I've been running ubuntu 8.10 on a thinkpad SL500 for about a year.  Recently we bought a Samsung 22" LCD monitor for watching videos off the laptops via VGA connections.  It's been great.  I've been able to use it with both our laptops (the other is a ThinkPad R61i) without any problems.

Until yesterday.  My wife was using the SL500 disconnected from the new monitor for several hours when suddenly its display went dim (unclear at this point whether this was after a suspend/shut down).  She tried rebooting but got the same nearly invisible screen.  It's not blank, just very, very, ***very*** dim.

To diagnose, I hooked the computer up to the monitor again and started digging.  I went into the /sys/devices/virtual/backlight directory and I found two subdirectories: acpi_video and thinkpad_screen.  The values for each are as follows:

acpi_video
actual_brightness:0
bl_power:7
brightness:7
max_brightness:13

thinkpad_screen
actual_brightness:15
bl_power:0
brightness:15
max_brightness:15

I'm a little confused by what I see.  In one directory, actual brightness is 0 (true enough for my laptop).  In the other, bl_power is 0.  I suspect this is a software problem, but I don't know what to do next.  I'd appreciate any constructive ideas the community might have.

---

### Post by CompBio on 2010-08-24
I should mention that I've tried some obvious things: with/without AC power, used Fn-Home/Fn-End to adjust the brightness, but to no avail.

---

