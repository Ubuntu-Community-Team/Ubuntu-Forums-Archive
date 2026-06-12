---
title: "Wireless dongle kills my USB ports!!!"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by kvonb on 2007-08-09
This is a good one:

I plug my Netgear WG111 (fake v2 which is actually a v1.5) wireless USB dongle/adapter into a USB port on my Acer Travelmate 240 laptop and it kills the other USB ports!

The USB mouse stops working, and all the other ports die as well.

Fortunately they come back when I turn the laptop off and on again.

The dongles work perfectly on my desktop, and also on this same laptop when running Windows.

Any ideas?


Kev :)

---

### Post by kvonb on 2007-08-10
wakey wakey!

---

### Post by kvonb on 2007-08-11
Just in case there is anyone else still alive in here this is the solution:

It's a conflict with another wireless driver that is being loaded by default, I simply followed phossals excellent howto here:

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

These damned Netgear WG111 series 'dongles' come in 3 versions, v1, v2(mislabelled), and v2(real).  You can find out which one you have by opening a terminal and typing lsusb.

If it returns: 0846:4240 NetGear, Inc. WG111 WiFi (v2), it's the v2(mislabelled) one, and you will need the appropriate Windows driver for ndiswrapper.

---

