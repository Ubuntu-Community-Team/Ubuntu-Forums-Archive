---
title: "Joypad (PSX-&gt;USB) detected but not working?"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Kupopo on 2006-06-09
Hi, I've been having difficulty with my joystick.  It's a "Super Joybox 2" which allows two playstation pads to be plugged into a USB port.  When I plug it in, it gets detected by the kernel and /dev/input/js0 is installed:

dmesg tells me this:
```
[4721665.854000] usbcore: registered new driver hiddev
[4721665.897000] input: USB HID v1.00 Joystick [0925:8866] on usb-0000:00:1d.3-1
[4721665.897000] usbcore: registered new driver usbhid
[4721665.897000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
```

lsmod shows (among other things):
```
gameport               14472  0
usbhid                 30688  0
```

But when I run jstest /dev/input/js0, it sees the correct number of axes and buttons, but all I ever get is
```
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off 19:off 20:off 21:off 22:off 23:off
```
and no amount of pressing buttons or directions will ever change this.  Likewise, jscal, or jscalibrator, or any other joystick-using program.  Also, I've tried
```
$ cat /dev/input/js0
iiiiiiiii       i
i
 i
iiiiiiiiiiiiiiiiiii     i
i

```
I always get the same shape with some random symbol or pair of symbols (i, H9, &#65533;, r@, and tons of others...)

I've had the same problem on my gentoo desktop as well as my (k)ubuntu (5.10) laptop.  However, win xp has no problem with it :confused: 

Thanks,
-steve

---

### Post by RobMBaker on 2007-02-11
Did you ever solve this?
I just got a crappy little joypad to play on GSnes9x - but it won't recognise the joypad.
Again, I get the same cat result as you.

---

### Post by honeybear on 2007-02-11
> **RobMBaker said:**
> Did you ever solve this?
I just got a crappy little joypad to play on GSnes9x - but it won't recognise the joypad.
Again, I get the same cat result as you.

did you try with zsnes ?

---

### Post by Kupopo on 2007-02-14
> **RobMBaker said:**
> Did you ever solve this?
I just got a crappy little joypad to play on GSnes9x - but it won't recognise the joypad.
Again, I get the same cat result as you.

I never resolved it in Ubuntu.  I found a workaround for my Gentoo box, since it uses hotplug.  I made a quick hack to hotplug.functions, as described here:

[http://www.pelennorfields.com/matt/2006/01/31/howto-ddr-dance-pads-in-linux-super-dual-box/](http://www.pelennorfields.com/matt/2006/01/31/howto-ddr-dance-pads-in-linux-super-dual-box/)

So if you've got hotplug in Ubuntu, or can figure out something analogous, then it's worth a try.  But I didn't seem to have the /etc/hotplug/hotplug.functions file in Ubuntu, so no dice.

-steve

---

### Post by RobMBaker on 2007-02-25
Never mind, actually; as I got it working just by fiddling ...
Turns out I hadn't been using the correct method for mapping the buttons.

Sorry I can't help you with your problem.

---

