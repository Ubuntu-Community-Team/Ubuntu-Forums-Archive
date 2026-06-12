---
title: "display not filling screen"
date: 2009-07-11
forum: Hardware
---

### Post by wcasper4 on 2009-07-11
I tried hooking up my tv to the s-video output on my toshiba satellite m-100. after messing with the display i put it back at 1024x768. but, it no longer fills the entire screen... any suggestions?

---

### Post by markeet on 2009-07-17
I am having the exact same problem.  I think it just started in the last week+.

Help, it's driving me nuts!

---

### Post by wcasper4 on 2009-07-17
welll

I haven't exactly gotten the s-video to work the way I want it, but I did solve the problem with the display not filling the screen. 
You need to figure out the correct display resolution that you want. I did this by going back to windows and seeing what was set as default. For me it was 1280x800.

Then in terminal you can:

$ cvt 800 600

this will give you a modeline, ex: "# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync"

then enter this modeline into the --xrandr command:

$ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

hope this helps

if you need more info: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

