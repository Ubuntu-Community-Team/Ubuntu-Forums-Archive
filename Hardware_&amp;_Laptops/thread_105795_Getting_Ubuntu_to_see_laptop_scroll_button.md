---
title: "Getting Ubuntu to see laptop scroll button"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by bruce147 on 2005-12-19
My laptop has a rocker button that is used for scrolling up and down a page in Windows XP. Under Ubuntu 5.10 it does not scroll a window. However, Ubuntu does see *something* from the device. If press the rocker in the down direction when I am over a link, that link gets opened in a new tab under firefox. Pressing in the up direction does nothing as far as I can tell.

So is there a way I can work with this to get the rocker button to scroll? Or does this require that someone has written a driver for this device? 
something
I have looked under System/Adminstration/Device Manager but I can't find this button. Is there another way to it?

---

### Post by gkasinath on 2006-12-13
Same problem here, mate! Have you resolved yours? 

Can you post a how-to if you have? I have seen quite a few posts regarding this issues (especially with Fujitsu notebooks, which I also have). 

Thanks. 

Cheers
Gautham

---

### Post by volty on 2007-09-21
I am also having issues with the rocker. The down button shows up as a button, but the up does not. I've been looking for the past couple of days with no success.

If anyone out there has any luck, please post!

---

### Post by sisco311 on 2007-09-21
can you post the output of xev when you scroll up and down?

---

### Post by volty on 2007-09-21
The down button:

```
KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  77  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MotionNotify event, serial 29, synthetic NO, window 0x3000001,
    root 0x4d, subw 0x0, time 778115, (85,15), root:(95,112),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 29, synthetic NO, window 0x3000001,
    root 0x4d, subw 0x0, time 778126, (101,5), root:(111,102),
    state 0x0, is_hint 0, same_screen YES

```

Oddly enough, the same thing occurs for a normal left button click.

The up-button does not register.

I've been looking, and it appears to be difficulties in Ubuntu with recognizing the Alps touchpad device as an Alps device. 

When I run cat /proc/bus/input/devices, I get the following:
```
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 ts1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

But no mention of the Alps pad. tpconfig finds:
```
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

Which is wrong, again. How the crap do I get Ubuntu to recognize the trackpad as an Alps trackpad, and gimme some function? lol

---

