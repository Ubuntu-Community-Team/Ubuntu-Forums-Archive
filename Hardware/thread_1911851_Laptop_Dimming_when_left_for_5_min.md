---
title: "Laptop Dimming when left for 5 min"
date: 2012-01-19
forum: Hardware
---

### Post by mechchild on 2012-01-19
Hello,

I have recently installed ubuntu 11.10 on by Dell Latitude D610 - If I walk away for 5 minutes it goes back. I touch the mouse it comes back to full light, but ever so slowly goes dim, finally going black again. From this it will not come back, other than shut down and restart. 

I have changed all the power settings to do nothing when lid closed or left, even if on battery.

Any ideas?

Tim

---

### Post by Toz on 2012-01-24
If the D610 has an intel video card, try updating your computer to the newest kernel (I believe we are now at 3.0.0-15.26). There was an intel backlight fix included in 3.0.0.15-17. See: [http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/7078]("http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/7078") and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652")

---

