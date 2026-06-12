---
title: "Laptop screen Dims to save power but never returns to full brightness"
date: 2008-08-19
forum: Hardware
---

### Post by miatawnt2b on 2008-08-19
I have my laptop set to dim the screen during inactive periods to save battery.  This seems to work, but when I com back to the machine the screen will only brighten so far and I need to manually increase the brightness the rest of the way. I'm not sure if there is a setting I am missing somewhere to tell the screen to brighten 100% or what.  Can anyone lend a hand?  This is an NVIDIA chipset running the latest driver from Nvidia.

-J

---

### Post by Sam Lars on 2008-08-19
Run
```
sudo gconf-editor
```
and navigate to
apps > gnome-power-manager > backlight
Do your settings seem to be fine there?

---

### Post by miatawnt2b on 2008-08-25
Thanks!

I edited the brightness_battery setting to 100. We'll see if that does the trick.

-J

---

