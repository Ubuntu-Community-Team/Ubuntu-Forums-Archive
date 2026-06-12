---
title: "No touchpad on HP DV4 1435dx"
date: 2012-04-13
forum: Hardware
---

### Post by IronEddie42 on 2012-04-13
My notebook is HP DV4 1435dx and I recently installed the Precise Pangolin Beta 2 release of Ubuntu 12.04 and everything seems to be working okay - except my mouse touchpad.  Neither the buttons (right/left click) or the mouse movement is working, but the on/off switch IS working - when I press the touchpad on/off button, I get a notification in the upper-right corner that tells me that it is on or off.

Not sure where to go on this one ... so a little help would be much appreciated.

Thanks!

---

### Post by TechZilla on 2012-05-21
I have 12.04 installed, my notebook model is HP DV4-1313dx.
I also have everything working, but no touchpad support of any kind.

It also seem like HP, has some sort of combined keyboard/mouse device.
Its identified as, "MCE IR Keyboard/Mouse (ene_ir)"

So it's not any of the three old school touchpad brands.

I actually found an answer for my problem at askubuntu.com
This is what worked for me,

```
echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse
```

---

