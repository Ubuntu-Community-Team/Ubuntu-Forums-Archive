---
title: "WIFI with G1 tethering"
date: 2009-04-15
forum: Hardware
---

### Post by here.david on 2009-04-15
Ubuntu 9.04 wifi works on laptop, I can tether G1 to N800 yet not on Ubuntu 9.04 any suggestions.  G1 wifi tethering shows up on Ubuntu 9.04 yet will not connect, tried various "help" suggestions found with search yet still can not get the G1 to connect (fyi - laptop with xp&Vista do connect to the G1 tethering).

Tx's...

---

### Post by resplin on 2009-05-15
You need to connect in ad-hoc mode. In 8.04 the GUI tools can't do it, so you need to disable network manager and connect on the command line. Add to /etc/network/interfaces:
iface wlan0 inet dhcp

Then in terminal type:
iwconfig wlan0 mode ad-hoc essid G1
ifup wlan0

I bet it's the same problem in 9.04.

---

