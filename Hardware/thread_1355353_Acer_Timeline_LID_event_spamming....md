---
title: "Acer Timeline LID event spamming..."
date: 2009-12-14
forum: Hardware
---

### Post by wolfier on 2009-12-14
Computer: Acer Timeline 1810TZ.
Setup: usually used it with the lid closed and connect to an external monitor thru D-sub.
Running Karmic.


With the lid closed, the laptop seems to send LID button events, that causes the external monitor to power down.  I tried editting /etc/acpi/ files, disabling events, etc. but it won't stop the monitor from being powered down.  So it seems to be something in the kernel that does it.

One strange thing is, merely *reading* /proc/acpi/button/lid/LID0/state seems to have the same effect as pushing the button. (i.e. cat, grep, less, etc.)

Short of recompiling the kernel (it's not something i desire to do), is there a way to make it behave in a way that the lid button would not affect the external monitor?

My work-around right now is, whenever it happens, open and close the lid again and quickly execute xrandr --output LVDS1 --auto --output VGA1 --auto, but it's annoying as hell...

---

### Post by wolfier on 2009-12-16
Isn't anyone using Acer Timeline laptops?

---

