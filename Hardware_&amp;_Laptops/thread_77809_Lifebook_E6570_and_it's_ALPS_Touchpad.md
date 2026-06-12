---
title: "Lifebook E6570 and it's ALPS Touchpad"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Chrissss on 2005-10-17
Hi!

Right now i'm trying to configure my touchpad on my laptop (Fujitsu-Siemens Lifebook E 6570) fully. Currently it works just as a mouse (pointing and clicking is ok), but all those fancy features like scrolling when you slide your finger on the right or bottom border don't.

On the synaptics driver page there the following hint:
> If you are using a 2.6 linux kernel, check the /proc/bus/input/devices file. The touchpad must be identified a "SynPS/2 Synaptics TouchPad" or an "AlpsPS/2 ALPS TouchPad". If it is identified as a "PS/2 Generic Mouse" or "PS/2 Synaptics TouchPad", something is wrong.
[http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt](http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt)

Well, of course i get the wroing result here:
```
# less /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=event1 mouse0 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
```

So i tried all the tips they give on that page. But neither changig my Bios settings, nor disconnectiong my usb mouse, nor ensuring that usbcore is loaded before psmouse helps.

Inside this forum there's a [patch](http://www.ubuntuforums.org/showthread.php?t=60494) for the synaptics x-server module. But even that doesn't help.

Is here someone who uses a similar notebook and was able to get the touchpad fully working?

Thanks
 Christoph

---

