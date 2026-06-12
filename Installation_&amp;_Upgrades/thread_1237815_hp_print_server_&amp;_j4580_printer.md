---
title: "hp print server &amp; j4580 printer"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2009-08-11
Have the above setup with a hp 2101 nw wireless printserver. The j4580 is conected to the usb port on the 2101. Am unable to figure out how to make the j4580 print. Anyone got any ideas? TIA

---

### Post by cdnLilwolf on 2009-08-11
> **jtmedin said:**
> Have the above setup with a hp 2101 nw wireless printserver. The j4580 is conected to the usb port on the 2101. Am unable to figure out how to make the j4580 print. Anyone got any ideas? TIA

In what way are you trying to set it up?  If memory serves you have to set up either as AppSocket/HP Jetdirect or LPD (I think the former).  Then your host ID and port.

I use the D-Link wireless and the device URI looks like...

socket://192.168.0.101:9100

---

### Post by jtmedin on 2009-08-11
I also have a d-link router. I notice that u use the ip address. Did u set aside that ip address for the wireless print server. I didnt set aside an address for the print server. I will see if that fixes it. Tnx

---

