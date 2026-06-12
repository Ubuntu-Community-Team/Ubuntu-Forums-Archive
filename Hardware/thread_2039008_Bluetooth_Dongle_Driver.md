---
title: "Bluetooth Dongle Driver?"
date: 2012-08-07
forum: Hardware
---

### Post by HoCo xXSamXx on 2012-08-07
So I broke down and bought a USB Bluetooth Dongle as apposed to getting the actual card for my laptop. I couldn't find any local hardware stores that sell it, and I can't get it offline because I'm 16 and my parents don't like using their credit card on me, anyways! It came with an installation CD, that I put in my laptop. In it there was an exe file that I ran. I don't know if it ran from WINE or not, but a window came up asking me if I have windows 7 or xp. I tried clicking both but nothing happened. Is there any way I can install the driver manually? See screenshot.

Thanks!
HoCo

[IMG]http://i1168.photobucket.com/albums/r481/HoCo_xXSamXx/BluettothSC.png[/IMG]

---

### Post by ahallubuntu on 2012-08-07
What's the output of

lsusb

?

Figure out from that the hardware ID and maybe you can find out how to build a kernel module for it.

FYI, the cheapo dongles I get for $1 from Asia via ebay never require a driver - they are automatically recognized by Ubuntu.

Can't beg your parents to buy you one of the cheapo ones and wait a few weeks?

---

### Post by Petro Dawg on 2012-08-07
If you have 12.04 you may not need the drivers on the cd anyway.  The pre-installed drivers worked fine for my cheap walmart bt dongel.  You can also get bt software from the software center which seem to work well for me.

---

### Post by HoCo xXSamXx on 2012-08-07
lusb yields:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 002 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 003: ID 05ac:024f Apple, Inc. 
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 007 Device 005: ID 0a5c:2154 Broadcom Corp. 

```

---

### Post by HoCo xXSamXx on 2012-08-07
Ahh! I got it, I plugged the dongle into my laptop's USB port as apposed to the port on the hub in my keyboard. Thanks for your responses!

---

