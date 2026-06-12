---
title: "Confusing display resolutions"
date: 2015-05-05
forum: Hardware
---

### Post by zkab on 2015-05-05
I have an Ubuntu 14.04 LTS server with Intel 2nd Generation Core Processor Family Integrated Graphics Controller.
The server was recently connected via VGA to a KVM switch.
Now it complains ... [COLOR="#FF0000"]The current timing is not supported by the monitor display. Please change your input timing to 1920x1080@60 Hz or any other monitor listed timing as per the monitor specifications.[/COLOR]
The console is locked with that message but I can ssh login to the server as usual.
Right now the display shows with its menu system that the resolution is 720 x 400 @ 70 Hz ... hmmm ... so why is it complaining - that resolution is specified as an display option ... confusing
How can I set all the resolutions that my display can handle so I can try another one.
There is no /etc/X11/xorg.conf

Preset Display Modes (Dell U2212HM) from the manual.

VESA, 720 x 400 31.5 70.0 28.3 -/+
VESA, 640 x 480 31.5 60.0 25.2 -/-
VESA, 640 x 480 37.5 75.0 31.5 -/-
VESA, 800 x 600 37.9 60.3 40.0 +/+
VESA, 800 x 600 46.9 75.0 49.5 +/+

VESA, 1024 x 768 48.4 60.0 65.0 -/-
VESA, 1024 x 768 60.0 75.0 78.8 +/+
VESA, 1152 x 864 67.5 75.0 108.0 +/+
VESA, 1280 x 1024 64.0 60.0 108.0 +/+
VESA, 1280 x 1024 80.0 75.0 135.0 +/+
VESA, 1600 x 1200 75.0 60.0 162.0 +/+
VESA, 1920 x 1080 67.5 60.0 148.5 +/+

---

### Post by dino99 on 2015-05-05
you might need to set the correct modelines, ubuntu and Dell values can differ
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by zkab on 2015-05-05
OK - I'll check the documentation ... thanks

---

### Post by zkab on 2015-05-07
The first command  I entered showed an error message ...

$ xrandr
Can't open display

---

