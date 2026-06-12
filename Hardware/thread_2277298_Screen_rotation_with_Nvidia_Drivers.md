---
title: "Screen rotation with Nvidia Drivers"
date: 2015-05-07
forum: Hardware
---

### Post by sephy7killermech2 on 2015-05-07
[COLOR=#000000]I have been scouring google for two days trying to fix my screen rotation problem. I can rotate my screen no problem with the Nouveau drivers, but those drivers pretty much make my games unplayable, which is not acceptable to me. With the Nvidia 331.113 drivers my games perform well but I cannot rotate my screen. I tried editing my xorg.conf file by placing "RandRRotation" "on" under both device and screen, I did each of these tests separately, but had no success with the command line. I tried both xrandr --output LVDS1 --rotate inverted and I tried xrandr -o inverted. with the former I get this.[/COLOR]

[COLOR=#000000]xrandr: output LVDS1 cannot use rotation "inverted" reflection "none"[/COLOR]

[COLOR=#000000]And with the latter the screen flashes but no change is made. [/COLOR]

[COLOR=#000000]I would love to continue using Ubuntu but this might be a deal breaker for me. I need to mount my laptop upside down at work and since I'm there for weeks at a time I need to be able to relax with my games as well. I can't tell you all how much I'd appreciate some help on this matter. Thank you for your time.[/COLOR]

---

### Post by gordintoronto on 2015-05-08
Run Nvidia X Server Settings. Select "X Server Display Configuration" on the left. The fourth item on the right is "orientation".

---

### Post by sephy7killermech2 on 2015-05-08
My options are "Layout", which has a big empty pink box. "Selection" which has only one option X screen 0. "Color Depth", which has a few options but of course it won't have anything to do with orientation. Then there are a few buttons below that "Apply", "Detect Displays", "Advanced", and "Reset". Clicking advanced gives me a "Meta Mode" option. I don't seem to have an "orientation" option.

---

### Post by sephy7killermech2 on 2015-05-09
If anyone else has any ideas it would definitely still be appreciated. Thank you all very much for your time.

---

