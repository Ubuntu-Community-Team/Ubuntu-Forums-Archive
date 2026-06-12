---
title: "Nvidia and Reduced Blanking"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by haynold on 2005-06-15
Hello:

I'm trying to get an HP 2335 flat panel display to work with an Nvidia
Geforce 5500 FX. If I use an analog cable all works very well and I can
run X with 1920x1200 using the default mode selected by Xorg. With the
DVI-D cable things get more complicated, though. Up to 1600x1200
resolution everything works perfectly with the default settings. For
1920x1200, however, I need reduced blanking which doesn't seem to be an
Xorg default mode. That's where the trouble starts.

The monitor manual says that 1920x1200 should be run at 154.0 MHz,
74.04 kHz, 60.0 Hz. From these parameters I computed the following
Modeline:

ModeLine "1920x1200" 154.0  1920 1940 2012 2080   1200 1201 1204 1234

The sync pulses are just guesses because I couldn't find any
information on the right sync timing.

If X starts with these settings, the monitor claims there's no input
signal and goes to sleep. I noticed something in the Windows driver
manual for the card that apparently the older Nvidia cards can't modify
timing for digital output, but it didn't say whether there is a
predefined mode for reduced blanking that does work.

I'd be very grateful for any suggestions on how to make this work. In
particular, if anyone has the VESA timing information for the
1920x1200, 154.0 MHz, 60.0 Hz that would hopefully be useful.

       Oliver

---

