---
title: "Cannot increase resolution past 1024x768"
date: 2014-06-28
forum: Hardware
---

### Post by crazyskeggy on 2014-06-28
System info:
Ubuntu 12.04
Intel Graphics Card

I have recently changed monitors from my 1280x1024 screen to a 720p TV with VGA input.

I have connected my PC (with Ubuntu 12.04) to the TV via a VGA cable.
(I noticed that one of the pins on the second row isn't on the cable - is that a problem?)

While my monitor worked well and Ubuntu recognised it and let me use the full resolution in "Screen Displays", when I changed the monitor to the TV, the monitor was labelled "Unknown" and it wouldn't let me go above 1024x768.

I have looked around on the internet and using cvt and xrandr works, but gets deleted after reboot.

Is there a way to fix the problem?

(To get it working, I used the following commands:
```

xrandr
cvt 1280 768 60
xrandr --newmode "1280x768_60.00" (bunch of numbers)
xrandr --addmode VGA1 "1280x768_60.00"

```

but it gets deleted on reboot)

---

### Post by tgalati4 on 2014-06-28
That missing pin (which is not normally used) is now used for [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data")--which allows for resolution negotiation between your computer and the display.  Find a 15-pin cable or write a script that runs at boot to set those settings or add your cvt modeline to /etc/X11/xorg.conf.

---

### Post by crazyskeggy on 2014-06-29
If xorg.conf doesn't exist, do I just create it?

EDIT: I made xorg.conf

Upon reboot, I got a black screen, so I had to boot into a live CD to remove xorg.conf and xorg.conf.failsafe

I am working on an init script to run xrandr at boot, but I haven't made one before.

---

### Post by sp40140 on 2014-06-29
Buddy, are you sure your TV is 720p?
The standard resolution for 720p is 1280 X 720. 
So, Ubuntu might be handeling it correctly. 
You can double check this by looking up the specs of your TV. It should tell you the max resolution supproted.
If your TV supports better / higher resolution, please post the make and model of the TV.

Cheers,

---

### Post by tgalati4 on 2014-06-29
You have to create a properly-formatted [xorg.conf]("http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file") file--otherwise you will get a black screen.

Put the [modeline]("https://help.ubuntu.com/community/NvidiaResolutionXorgConf") in the correct place.  Your numbers will be different.

tgalati4@Mint14-Extensa ~ $ cvt 1280 768 60
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

I don't know why the *xrandr* mode is not sticking across sessions.  Maybe you need to use *sudo*.  I've always used the old school method: xorg.conf.

---

