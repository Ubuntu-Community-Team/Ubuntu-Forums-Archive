---
title: "Setting video resolution on T60"
date: 2013-02-04
forum: Hardware
---

### Post by murrayim on 2013-02-04
Hi All,

I've inherited a IBM T60...should have ATI 1300, and a maximum resolution of 1400 x1050... But Xrandr only 1024 x 768...

Anyone have an idea on what the modeline should be...and how do check that the lcd screen does have 1400 x 1050 pixels

I've used xrandr to add the follwoing modeline
Modeline "1400x1050_60.00" 121.75 1400 1488 1632 1864 1050 1053 1057 1089 -hsync +vsync

but when I try to activate it..the screen goes nuts...forcing a reboot

---

### Post by Yellow Pasque on 2013-02-04
Post/attach /var/log/Xorg.0.log

---

