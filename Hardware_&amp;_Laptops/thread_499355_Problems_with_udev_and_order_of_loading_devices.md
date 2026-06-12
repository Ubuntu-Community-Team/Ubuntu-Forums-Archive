---
title: "Problems with udev and order of loading devices"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by Saubazi on 2007-07-12
I have this problem with my dvb cards - they are loaded automatically by udev or whatever during the boot.
The problem is that it does not seem to happen always in the same order - therefore sometimes one is adapter0 and the other one adapter1 or vice versa. The main problem is coming from the fact that one is DVB-C and ond is DVB-T and I need to have them on the assigned places for mythtv.

So can I solve this with udev-rules so that certain adapter is always adapter0 and the other one adapter1 or is there a way to blacklist these devices and load the modules manually?

---

