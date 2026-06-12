---
title: "Still no GUI"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by jitesh on 2006-06-06
After installing Ubuntu on the HP nx6125 laptop I can't load the GUI. I the edited the file /etc/X11/xorg.conf by adding under Devices the following line, Option "NoAccel" "True" but still no luck. I then also edited, the resolution from 1024x768 to 640x480, and still nothing. Any further ideas.

---

### Post by bikeboy on 2006-06-06
Under the section "Device", what driver is listed? And if possible, can you tell us what sort of graphics card/chip your computer uses?

---

### Post by jitesh on 2006-06-06
Managed to fix the bug, did'nt edit the xorg.conf file properly. Thanks

---

