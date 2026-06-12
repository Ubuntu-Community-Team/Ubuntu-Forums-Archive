---
title: "NX6125 wireless button on Dapper 6.06RC"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by Davor281 on 2006-05-27
Hello!

Anyone here that managed to fully work with wirelles button on NX6125?

When I press the button, the wi-fi card is activated, but then I have to manually set ESSID or restart the networking in order to connect to my AP.

I am using ndiswrapper with latest hp drivers for Broadcom 4318 rev. 02.

No problems in dmesg with ndiswrapper, the only strange thing that appears now and then is the following message:

"eth1: no IPv6 routers present".

Also, anyone else noticed, that ndiswrapper installs "wlan0" but network-manager identifies the card as "eth1".

Thanx!

ENjoY!

Davor.

---

### Post by Davor281 on 2006-05-27
Answering myself and all interested ...

The only joke was to rename the eth1 - which was my wireless (due to MAC address) - in /etc/iftab to wlan0.
After that, the button and connection works perfect.

ENjoY!

Davor.

---

### Post by baiki on 2007-11-23
Didn't work on my nx6125. If i wanna enable the wlan0 device it'll disabled after 1 second again. And if I press the wireless button I get this message:

atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0)

I guess my card is working but OFF??!?!?!?

Any ideas?

---

