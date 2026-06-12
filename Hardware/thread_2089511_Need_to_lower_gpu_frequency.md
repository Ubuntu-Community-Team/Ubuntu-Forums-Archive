---
title: "Need to lower gpu frequency"
date: 2012-11-29
forum: Hardware
---

### Post by swoll1980 on 2012-11-29
I have a ati x1200. Ati dropped support for this card a while back, so I'm stuck with the xserver-xorg-video-radeon one. Is there a way to lower the gpu frequency w/o using fglrx driver?

---

### Post by 2F4U on 2012-11-29
Yes, power management with the open source drivers is possible:

[http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/](http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/)

The obvious choice would be the dynamic method, however, in my experience it causes the screen to flicker every time the frequency changes.

---

### Post by swoll1980 on 2012-11-29
Thanks! Got another problem now about to post new thread.

---

