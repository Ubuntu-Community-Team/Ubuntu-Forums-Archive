---
title: "eee laptop problem with external monitor"
date: 2008-09-03
forum: General Help
---

### Post by boom2k1 on 2008-09-03
I am running on Ubuntu 8.04 (Ubuntu eee). I have been using Asus eeepc 701 with a 17" Samsung SyncMaster 172x external monitor, which has a native resolution of 1280x1024.



It took me very long to figure out by myself how to make it display the native resolution on the external monitor while turning off the eee's tiny screen.
This does not involve using any of those GUI tools, as none of those tools work AT ALL: the screen resolution GUI doesn't give me the right resolution of my monitor and the displayconfig-gtk  just gave me such a hard time starting X!
I was extremely disappointed in Linux because they haven't fixed this common display problem in the last 2 years!

(I didn't change a line in the default xorg.conf .... and I really can't figure out how to change it either...)

The way to get this to work is to type these lines into the command line.
```

#got from running cvt -v 1280 1024 60.0
xrandr --newmode 1280x1024  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync    
xrandr --addmode VGA 1280x1024
xrandr --output LVDS --off
xrandr --output VGA --mode 1280x1024

```
eeepc uses the intel driver, but the 8.04 "intel" driver just doesn't like these lines above if I specify Driver "intel" in the Device section of xorg.conf. 


Okay, so I get the resolution working. But the problem is, after I turn on the external monitor at this highest resolution for A WHILE (about half an hour?), it starts blinking (turns black, and then go back to the screen) like around every 30 seconds-a minute... and after that first blinks, it would continue to blink more and more often!!!!!!!
What is happening?!?!!

I am not sure why... was it because the numbers for 1280x1024 above were not correct? (But i got those numbers from cvt!)

More weirdly is that, on some blinks, even that power light switch off! The power light sometimes remains OFF, although the monitor still displays stuff... And if I really ignore all those periodic blinking, it would shut itself completely after a while!!!

What is happening, and how do I fix it???

I remember having no related problem with 7.10... how weird!! (but when I used 7.10, I really didn't need to use any xrandr to get the highest resolution to work, although I use xrandr to turn my oversized eeepc screen off)

[I thought it was the power management thing, but I have made adjustment to the power management already and that doesn't work!!]


also, it will not flash for a while after I turn the monitor off for a few minutes.


Help!
Thanks

---

