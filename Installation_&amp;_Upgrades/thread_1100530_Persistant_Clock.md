---
title: "Persistant Clock"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Dj TweeX on 2009-03-19
So i have a persistant install of ubuntu on my 16 Gb flash drive. i notice that every time i start up with it, the clock is always wrong. depite me changing it back. 
how do i fix this?
~~Gabe~~

---

### Post by lemming465 on 2009-03-21
If *ntpdate* is installed and you have a network connection, /etc/network/if-up.d/ntpdate should be correcting the time from some NTP server somewhere.  If you have a permanent (e.g. ethernet) network connection, you might want full *ntp* installed.

Is your clock off by the number of hours between you and UTC?  If so, and it's a dual-boot system with windows, make sure that it says "UTC=no" in /etc/defaults/rcS.

---

### Post by Dj TweeX on 2009-06-10
sorry for the delay.
no its not a time zone issue. its randomly off. but i dont really use it anymore. a solution would be welcome anyway

---

