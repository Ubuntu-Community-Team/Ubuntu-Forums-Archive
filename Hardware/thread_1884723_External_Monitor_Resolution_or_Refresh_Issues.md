---
title: "External Monitor Resolution or Refresh Issues??"
date: 2011-11-21
forum: Hardware
---

### Post by daveosociologist on 2011-11-21
Just got a Westinghouse 32" (VR-3225) LCD HDTV.  Supposed to be running at 1920x1080.  When I first plug it in via VGA max resolution available is 1028x764.  I CAN add 1920x1080 and it looks okay for the most part, except when I put things in full screen.  If I put a video in full screen mode, for instance, there are all of these color distortions in the form of horizontal bars moving across up and down the screen.  It depends on what is being rendered, gray things look okay, orange things look greenish...  OR If I put my cursor to the left edge of the screen it creates a dark bar that runs all the way across the screen horizontally.  OR if I take the firefox window and put it half out off the left edge of the screen everything gets very dark with lots of horizontal lines.  

Not really sure how best to describe all this but when I plug in other devices they look fine so it seems like it has to be something in the refresh settings.. Any ideas what to do?

Running Ubuntu 11.04 on a Toshiba Satellite.  

Got this from $ cvt 1920 1080:

# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

---

### Post by daveosociologist on 2011-11-21
I appear to have figured it out following the following instructions:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

I think when I used xrandr to change the settings previously it was utilizing a modeline profile that wasn't quite right. Not sure exactly how that happened... but a few freeze ups and restarts and following those instructions seems to have done the deal.

---

