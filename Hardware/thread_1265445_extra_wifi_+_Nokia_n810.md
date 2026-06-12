---
title: "extra wifi + Nokia n810"
date: 2009-09-13
forum: Hardware
---

### Post by haxer on 2009-09-13
Hello. 

Since there is one usb port on Nokia n810 tablet pc. Is there any way of getting an wifi extra on usb?

---

### Post by haxer on 2009-09-14
Bump

---

### Post by tgalati4 on 2009-09-14
I have an n800.  If you mean, can I susbsitute the internal wifi for an external/usb wifi?  Yes, but it's fiddly.

You need USB host/control mode.  Set to host and plug in USB stick.  Load the appropriate Debian driver for it.  To find the module, run a Debian-based linux desktop and do an lsmod.  Plug in the USB wifi then do an lsmod again and look for the additional module(s) loaded.

Find the module precompiled for the ARM architecture or grab the source code if it's an open driver and cross-compile yourself for ARM architecture yourself.

Load onto the n810 and in a root terminal:

modprobe yourusbdriverthatyoufoundorcompiledforARMarchitecture

ifconfig

Look for eth1, wlan0 or wlan1, ath0, depending on the brand of USB.  Let's call it eth1.

iwconfig eth1 (add the rest of appropriate settings)

The final hurdle is that the USB port doesn't put out full current (500 mA).  I can use a USB GPS puck at 70 mA, but I'm sure wireless requires more current.  So if it drops out, you need to fabricate a custom cable to provide 5 VDC with 500 mA or more with an external battery pack.

Like I said, it's fiddly.

---

### Post by haxer on 2009-09-15
Ok thank you. :) now im happy theres still hope for the little man. I will try this tonight and then ill come back with answers. If it works or not :) .

---

### Post by tgalati4 on 2009-09-15
Did your wireless chip crap out?  Is this why you need to use an external USB wireless?

---

### Post by haxer on 2009-09-15
No actually i didnt have money to buy the wifi real modell from china so i ordered copy from china :) only 950 swedish kronor. Its like 180dollar or something. So it was really cheeeeap. Im a student now :(

---

### Post by tgalati4 on 2009-09-15
So it's an imitation nokia n810 without wifi?  How interesting.

I remember that the wifi chip that nokia used is proprietary, without open source drivers, so perhaps it is difficult to get.

Wifi is kind of critical for a handheld web device.

---

