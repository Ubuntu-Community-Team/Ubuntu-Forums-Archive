---
title: "calibration feisty fawn touchscreen egalax evtouch"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by Cortexbuster on 2007-06-03
Hi
I had no problem installing the evtouch driver from [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html)
 on Kunbuntu 7.04 feisty fawn. This one seems to be right for my touchscreen, lsusb says:
Bus 001 Device 003: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Mkay, after some changes to xorg.conf, according to the instruction on the evtouch website it was basically working, but somehow it seems to be twisted, e.g. no mather what options I set in xorg.conf the pointer doesn't follow my movement on the screen. I tried all combinations of 
Option "SwapX"
Option "Swapy"
Option "Rotate" "cw"
Option "Rotate" "ccw"

If i touch the upper left of the screen, the pointer appears in the upper left, if I touch the upper right of the screen the pointer appears in the lower right corner. Has anybody already notices such behaviour? I caught the right /dev/input/event (2 in my case). Now I'm kind of stuck. Previously I ran the panel under windows xp with the drivers from the egalax / eeti website [http://www.eeti.com.tw/web20/drivers](http://www.eeti.com.tw/web20/drivers) 
I calibrated it with the windows tool, which seems to write directly to the screens built in controller chip. Might this have caused the problems? Back in windows it worked nice and precise. No twists at all. 
I would appreciate any help.

---

### Post by bofu on 2007-06-17
the event2 on my machine (hp tx1000) does not stay the same, it swaps with the touchpad when i reboot.. so i would think about that first of all...


next, grep your /var/log/Xorg.0.log for evtouch and see if the module is loading properly... i am having these 2 issues with my tablet.

---

### Post by v.cecchetto on 2007-07-08
> **bofu said:**
> the event2 on my machine (hp tx1000) does not stay the same, it swaps with the touchpad when i reboot.. so i would think about that first of all...


next, grep your /var/log/Xorg.0.log for evtouch and see if the module is loading properly... i am having these 2 issues with my tablet.

[http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000&page=3](http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000&page=3)

---

### Post by Beacon11 on 2007-11-30
> **Cortexbuster said:**
> If i touch the upper left of the screen, the pointer appears in the upper left, if I touch the upper right of the screen the pointer appears in the lower right corner.

Graphics are rendered in a negative cartesian fashion. What I mean by this is that someone with no experience rendering graphics would assume that rendering would start in the lower-left corner. Positive y is up, positive x is to the right. That's not the case. It starts in the upper-left corner. Positive y is down, positive x is to the right. So in your case, it kinda sound like your y-axis is being overridden by your x-axis. If you touch in other locations, does this seem plausible? In other words... if you touch at the dead center at the top of the screen, is the cursor in the dead middle of the screen? If so, then I'd check that.

---

