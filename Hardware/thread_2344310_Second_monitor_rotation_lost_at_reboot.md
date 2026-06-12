---
title: "Second monitor rotation lost at reboot"
date: 2016-11-24
forum: Hardware
---

### Post by No_I_wont on 2016-11-24
I have a dual monitor setup with the right one rotated -90°.
With the default Ubuntu display setup (nouveau driver?) this works very well. I wasn't happy with the display quality though, with tears and banding, so I switched to the Nvidia driver.

Now I can set up the displays with the right one rotated, but after each boot or restart the monitor is back to normal rotation.(Yes, I do save to xorg.conf)

1: 1920x1080
2: 1050x1680, Rotate left.

Nvidia driver version: 367.57
GeForce GTX 480

Why is this setup not persistent?

---

### Post by No_I_wont on 2016-11-28
Found a workaround. Running a bash-script at startup having xrandr rotate the second monitor.
(xrandr --output DVI-I-3 --rotate left)

---

