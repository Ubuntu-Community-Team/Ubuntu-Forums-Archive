---
title: "Laptop, External Monitor Problem"
date: 2011-07-13
forum: Hardware
---

### Post by idlemind324 on 2011-07-13
My System:
Operating System: Ubuntu 11.04 Desktop 32-bit
Model: IBM ThinkPad Z60m
Processor: 2.00GHz Pentium M
RAM: 2GB
Video Card: ATI Mobility Radeon X600
Built-in Display: ~15" screen 1280 x 800 native resolution ( supports 1024 x 768 )
External Monitor: Dell 19" Monitor

If I boot up my laptop without an external monitor attached the video displays fine on the built in screen without an issue at 1280 x 800.

If I boot up my laptop with my external monitor connected and my screen open the login window for Ubuntu comes up and displays fine on my primary display (laptop screen). Once I login the screen becomes a blur of colors and nothing is displayed. I can hit ctrl+alt+f1 and get to a console and login but I'm not sure what I need to do from there to properly configure my displays.

Thanks in advance.

-=-=- Update #1 -=-=-

I attached a screenshot (old school picture style) of what my desktop is doing. I will gather the logs when I can. This is my work machine so I have to do it when I have down time.

---

### Post by idlemind324 on 2011-07-22
Bump, anyone have some pointers?

---

### Post by realzippy on 2011-07-22
When you log in at console and run

```
startx
```

What happens?
Errors?

Does /var/log/Xorg.0.log file give a clue ?

Does Fn + F4 work?
If so,what happens when disabling external monitor before logging in
and re-enabling it when session runs?

---

### Post by teddks on 2011-08-24
I have the same notebook and the same issue.

fn-f4 seems to be the suspend function, so while I presume that would work, I don't think it's really relevant here. fn-F7, the key I think is "cycle through dualscreen/only laptop screen/only monitor" doesn't work -- it generates a new picture like the OP posted, but besides that nothing happens.

Control-alt-backspace, if configured to do so, does kill the X server successfully. 

On another laptop with an ATI card, I had a similar, but less severe problem. On that system, I could launch a terminal that would be displayed on my laptop screen, and run "compiz --replace&" or "unity --replace&". This would flicker the screen for a few seconds, and then it would restart compiz in a working configuration on both screens. That doesn't seem to be working now.

The Xorg logs are filled with entries like this as soon as I plug in the VGA cable:

[ 44482.214] (II) RADEON(0): EDID vendor "IBM", prod id 10375
[ 44482.214] (II) RADEON(0): Printing DDC gathered Modelines:
[ 44482.214] (II) RADEON(0): Modeline "1680x1050"x0.0  122.00  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (64.1 kHz)
[ 44482.214] (II) RADEON(0): Modeline "1680x1050"x0.0  101.67  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (53.4 kHz)
[ 44483.224] (II) RADEON(0): EDID vendor "IBM", prod id 10375
[ 44483.224] (II) RADEON(0): Printing DDC gathered Modelines:
[ 44483.224] (II) RADEON(0): Modeline "1680x1050"x0.0  122.00  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (64.1 kHz)
[ 44483.224] (II) RADEON(0): Modeline "1680x1050"x0.0  101.67  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (53.4 kHz)
[ 44493.622] (II) RADEON(0): EDID vendor "IBM", prod id 10375
[ 44493.622] (II) RADEON(0): Printing DDC gathered Modelines:
[ 44493.622] (II) RADEON(0): Modeline "1680x1050"x0.0  122.00  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (64.1 kHz)
[ 44493.622] (II) RADEON(0): Modeline "1680x1050"x0.0  101.67  1680 1712 1776 1904  1050 1051 1054 1066 -hsync -vsync (53.4 kHz)

as if I'm continually plugging and unplugging the cable.

---

