---
title: "How do I get all devices installed so there are no unknowns in the device manager"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by SnowPunk98 on 2007-02-05
I would like to get all my devices installed and I think some were not found during installation. If there ends up being a device that offers me no more information than "unknown" how do I figure out what it is and get the appropriate drivers installed?

---

### Post by jd65pl on 2007-02-05
What devices do you refer to could you be a little more specific?

---

### Post by tommcd on 2007-02-06
In terminal type <lshw> to get a list of all your hardware. Then type <lspci -v> to get a list of all PCI devices. AFAIK anything that comes up in lspci should have a driver automatically installed. Does all your hardware work? Do have sound and can you access the net? These seem to be the most common problems with hardware, excluding peripheral devices. A lot of things listed in device manager may say "unknown" but it does not mean they are not installed and working.

---

