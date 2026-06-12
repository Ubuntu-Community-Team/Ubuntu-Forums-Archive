---
title: "Touchscreen problems: listed in /proc/bus/input/devices but not in xinput"
date: 2014-11-24
forum: Hardware
---

### Post by ronniepinsky on 2014-11-24
My touchscreen is not working but appears to be listed in /proc/bus/input/devices as (a few details): NAME="Video Bus" Phys=LNXVIDEO/video/input0 Handlers=kbd event3 .  It is not listed in "xinput list".  "xev" registers no events at all.  Is this even the touchscreen or could it be the camera?  Where should I go from here?

edit:
Windows shows the touchscreen as "Goodix Touch HID".  I also suspect it is connected through the i2c bus.

edit 2: It works at a basic level!  The previous problem means your touchscreen is detected but has no driver.  I found this link:
[http://comments.gmane.org/gmane.linux.kernel.input/38267](http://comments.gmane.org/gmane.linux.kernel.input/38267)
which lead me back to a page I had looked at earlier and realized it was the same thing:
[https://github.com/hadess/gt9xx/tree/master](https://github.com/hadess/gt9xx/tree/master)
I compiled that kernel module against whatever kernel Kubuntu 14.10 comes with and after running "depmod -a" and rebooting the touchscreen started to work!

---

