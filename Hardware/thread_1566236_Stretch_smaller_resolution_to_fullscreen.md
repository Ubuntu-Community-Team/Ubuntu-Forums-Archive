---
title: "Stretch smaller resolution to fullscreen"
date: 2010-09-02
forum: Hardware
---

### Post by Cuivienor on 2010-09-02
Hi,

I am currently a happy user of Ubuntu 10.04, but I have a question about screen resolutions:

I use an ATI X1250 with the radeon driver (ATI does not support the X1250 anymore). My physical screen resolution is 1360x768, and Ubuntu works perfectly at that resolution.

I use kernel 2.6.34 with modesetting.

The problem comes when I try to use smaller resolutions, which is useful when running games (via Wine or not):

-1024x768 is fine, uses exactly 1024x768 physical pixels on the screen: black bars to the left and right of the image
-800x600 is very small, it uses exactly 800x600 physical pixels, meaning it is in the middle of the screen, with black bars left, right, over, and below it, and looks tiny 
-640x480 is stretched out to the whole screen, using all the 1360x768 physical pixels, no black bars.

I don't understand why one resolution is stretched to the full screen (640x480) and others are not (800x600). This is the same behavior with or without modesetting.

Is there any way to control this? Specifically I'd like to stretch 800x600 to the whole screen, instead of it occupying a small area in the middle... I've tried a bunch of options with xrandr, but to no avail. Other posts referring to similar problems solved the problems with the Catalyst control center, but that is not an option for this legacy card.

Thank you very much!

Yannick

---

