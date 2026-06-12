---
title: "iMON Pad (device 15c2:ffdc) driver problem"
date: 2012-10-06
forum: Hardware
---

### Post by Skerit on 2012-10-06
This device hasn't worked since Ubuntu 11.10.
There are multiple items on the device: the LCD, the knob and the ir received.

The LCD and knob work fine. The IR received does absolutely nothing.

I do believe the wrong driver is loaded, it's using rc_imon_mce, but it should use rc_imon_pad. I tried blacklisting the former, but it still loaded after boot.

Any idea what to do now?

---

### Post by Skerit on 2012-10-06
I just tried my Windows remote on the received, and it picked up the commands just fine. So something really is wrong with the driver. Anyone know what it could be?

---

