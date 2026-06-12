---
title: "Canon iP2700 not detected anymore"
date: 2012-05-31
forum: Hardware
---

### Post by roots on 2012-05-31
Hi there,

strange issue with 12.04: I've been printing happily yesterday on my Canon iP2700 using cups and Canon filter drivers.
Today, by some reason, the printer is not detected properly anymore. Tried to reinstall Canon drivers & cups to no avail - it says theres no printer connected!

Funny thing:

-lsusb shows a Canon device (this is the printer)
-I can print from a VirtualBoxed Windows without problems.

I'm suspecting todays updates - any suggestions ?!


Thx,
roots

Added at 2:30 p.m.

Solved the problem by purging all cups & canon drivers (incl. rm -r /etc/cups) and reinstalling only cups.

---

