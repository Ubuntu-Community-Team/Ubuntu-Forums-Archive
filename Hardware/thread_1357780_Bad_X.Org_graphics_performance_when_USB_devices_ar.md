---
title: "Bad X.Org graphics performance when USB devices are not connected"
date: 2009-12-17
forum: Hardware
---

### Post by w-sky on 2009-12-17
I think this is really strange and hope to get some help, how to find out what exactly causes this problem:

When **no** USB device like a mouse, printer or bluetooth dongle is connected, all graphics performance (like Compiz effects or screensavers) is really bad, bucking like slow motion. But when I plug in one of those devices, the graphics performance is good instantly.

The system is a freshly installed Ubuntu 9.10 Karmic on a FSC notebook model of 2006 with AMD Sempron 3400+ processor and ATI Mobility Radeon X200 graphics. This is a rather low-end onboard chipset, that isn't even supported by the current proprietary ATI driver anymore, and so I am instead using the standard X.Org drivers.

I even tried this: With Compiz set to "extra", and an USB device plugged in, using the touchpad I move that elastic window around on the screen. Instantly when I remove the USB device, the graphics start bucking, and instantly when I plug the USB device back in, the effects are smooth again.

Important to mention that the mouse pointer still moves perfectly smooth, it is not bucking, so it really, most probably, is not a problem with the mouse or the touchpad.

Not "helping" in this case were a memory stick and an USB harddrive.

Also I could not see any strong CPU usage. What is happening here?

---

