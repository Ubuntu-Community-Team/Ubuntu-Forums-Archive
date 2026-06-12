---
title: "[UNSOLVED] Toshiba L40 and xrandr"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by grozni on 2008-02-14
Hi guys,


I'm trying to run xrandr, it works, but not in the way I want. My card is intel 3100, driver intel. For example if I run:


```
xrandr --output LVDS --mode 1280x800 --output VGA  --mode 1280x1024  --left-of LVDS
```


after this command "bar" with aplication, places, system and my shortcuts is moved to external monitor. On my laptop screen all opened windows and desktop icons are left untouch. What I'm I missing here I don't want to drag anything to external monitor in this case this bar. What should I do, I just  want external monitor as virtual workspace, why is he dragging ubuntu startup bar? My laptop monitor is running 1280x800 resolution, external monitor is LCD max capable for 1280x1024 @ 60hz., in xorg.conf virtual is set to 3000 2000. Thanks

---

