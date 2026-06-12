---
title: "No Video on Resume"
date: 2009-04-09
forum: Hardware
---

### Post by professor_rumsdiegeige on 2009-04-09
Hi,

I'm using Ubuntu 8.10 64bit and the proprietary (restricted) Nvidia drivers. The Mainboard is an ASUS P5Q with an Intel Core 2 Duo T8xxx.

Everything working except for Hibernate & Suspend: after resuming, the screen remains blank, more precise: the LCD displays even do not show a blank screen but rather remain powered off (no video signal).

In xorg.conf, I activated "NvAGP = 1".
In "/etc/.../acpi-support", I set "SAVE_VBE_STATE = false" and "POST_VIDEO=false".
Next, I blacklisted other AGP modules (intel_agp for me).

Still, the problem remains. Do I need to change BIOS settings - e.g. "ACPI 2.0 Support" is turned off - is that right?

Thanks for your help!
Sabine Lorentz

---

