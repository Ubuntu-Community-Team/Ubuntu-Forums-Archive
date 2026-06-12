---
title: "Ubuntu 10.04 + Dual Head, Touchscreen + Standard LCD"
date: 2011-02-24
forum: Hardware
---

### Post by dsigma on 2011-02-24
I have ubuntu 10.04 installed on a machine with DVI + VGA output. I have an Elo Technologies 17" LCD plugged into the VGA port, and a 20" normal LCD on the DVI port. (1280x1024 and 1600x1200 respectively). 

The Elo touchscreen is usb, and when running single head, works just works... I had to invert the x-axis and that's it. However, when I plug in the 2nd monitor, re-configure the video display settings, and touch the touch screen, the X component of the touch screen scales across to the 2nd monitor (it's not limited to the first LCD). 

For instance, if I touch the far left of the touch screen, the mouse hops to where my finger touched. If it touch about the middle of the touch screen, the mouse hops near the boundary of the first/second monitors. If I touch the far right of the touch screen it hops to the far right of the 2nd monitor. the X-axis seems to be scaled wrong.

I tried running xinput_calibration and clicking the red pluses with my mouse, and applying the generated command line but it didn't help at all.

I've been having a hard time finding anyone else trying to do this online or having a similar issue and thus I'm posting about it...

I guest my question, is this configuration even expected to work? I've never setup a touchscreen under linux before and am note sure what I can and can't expect to work? If it is expected to work, what should I be looking at/changing for this x-scaling issue?

Thanks,
-d

---

### Post by 1-prop-head on 2013-01-05
Trying this myself and from what I see you will need additional configuration parameters to provide an offset for the left and right screen.
The current configuration will accept separate calibration values for each touch screen but will not limit the span of those values to the domain of the intended screen.  Other issue would be the consistant application of USB touch screen interface to a specific id.  If this is not consistant the result will be the configuration will move arround depending upon the order the USB devices are installed.

This is just a guess from my work with Ubuntu 12.04.  If someone knows of a way to configure 2 or 3 touch screens in an array lets get it out there.

---

