---
title: "Laptop hardware buttons don't work as expected."
date: 2018-02-26
forum: Hardware
---

### Post by alanwalterthomas on 2018-02-26
I resuscitated an old Toshiba Satellite P100 or P105 with xubuntu 17.10 32-bit. It mostly works, but the hardware buttons aren't properly configured.
The FN + Brightness Keys (F6, F7) cause a brightness indicator to appear and change, but the actual screen brightness does not change at all.
There is a media app key which does nothing. I'd like it to open vlc.
There is also a web browser key. If I press it, it opens a seemingly unlimited number of firefox instances as quickly as possible, which freezes the machine in less than a minute by consuming all RAM.
I'd like it to open just one instance.

How can I fix this?

Thanks!

---

### Post by kerry_s on 2018-02-26
settings-> keyboard-> shortcuts

---

### Post by alanwalterthomas on 2018-05-29
I looked at that. It doesn't help.
In XFCE Settings->Keyboard lets me choose from Behavior;Application Shortcuts;Layout tabs. Application shortcuts has a list. I can enter a command triggered by what's identified as XF86MonBrightnessDown, but what should that command be? xbacklight -set 0 has no effect.

---

### Post by kerry_s on 2018-05-30
find your monitor, mine is LVDS1
```
xrandr --listmonitors
```

try command, this is for 50%
```
xrandr --output LVDS1 --brightness 0.50
```

100%
```
xrandr --output LVDS1 --brightness 1.0
```

if those work we can move forward from there.

---

