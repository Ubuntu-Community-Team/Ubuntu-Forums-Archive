---
title: "enermax aurora premium keyboard / audio works with karmic"
date: 2009-12-05
forum: Hardware
---

### Post by ansicplusplus on 2009-12-05
Hy
finally the integrated usb audio of the enermax aurora premium keyboard is supported in ubuntu. I just switched to karmic and it works, although the soundquality is somehow disturbed. 
You have to options snd-usb-audio index=-2 ignore_ctl_error=1 in /etc/modprobe.d/alsa-base.conf since the card has no mixer.
Yours ansicplusplus

---

