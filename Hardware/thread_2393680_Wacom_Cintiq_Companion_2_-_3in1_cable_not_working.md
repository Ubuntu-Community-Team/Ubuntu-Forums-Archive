---
title: "Wacom Cintiq Companion 2 - 3in1 cable not working"
date: 2018-06-06
forum: Hardware
---

### Post by bekast on 2018-06-06
I have a Wacom Cintiq Companion 2 which I have just installed Ubuntu 18.04 on. Everything is working beautifully as far as system, pen control, resolution, and touch. The problem I'm having is that the cable that allows the tablet to function as a simple touch enabled extra screen when connected to another PC is no longer working. 

Previously, I had Win10 installed on the device, and when I plugged the one end of the cable into the Wacom, and the other (which consists of an HDMI and USB connections) into the PC, the screen would switch over.

I guess I thought there was more of a BIOS passthrough for this event, but it looks like it's driver related? If that's the case, is there some way to patch the driver to support the "connect as a monitor" event?

---

### Post by bekast on 2018-07-31
Working!

So it is a BIOS feature that handles the Hybrid switching. Not sure if installing Ubuntu messed something up or the reinstalling of Windows on a small partition did it, but the BIOS bit wasn't right.

Wacom provides a [COLOR=#333333][FONT=&quot]Companion 2 Hybrid Update Utility : [/FONT][/COLOR]https://www.wacom.com/en/support/product-support/other

Running this sets the BIOS back to rights. (It's an .exe so Windows is still needed a little) I then booted into Ubuntu and used the power switch to "put the tablet to sleep" with the 2in1 cable plugged in. It switches over and is recognized now by the computer it's connected to!

Hopefully this helps some other Cintiq user in the future. If not, it shall simply stand as a monument to my conquering of the problem!

---

