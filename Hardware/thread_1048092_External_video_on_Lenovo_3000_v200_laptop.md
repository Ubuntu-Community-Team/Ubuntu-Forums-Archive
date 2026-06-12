---
title: "External video on Lenovo 3000 v200 laptop"
date: 2009-01-23
forum: Hardware
---

### Post by kemal on 2009-01-23
When I boot MS Windows, Fn+F7 directs the screen to external projector, but that key sequence does not work for Ubuntu 8.10 desktop.

Any suggestions please?

TIA

Kemal from Turkey

---

### Post by TheGoblin on 2009-04-19
Try running the command

xrandr --output LVDS --mode 1024x786 --output VGA --mode 1024x768 --same-as LVDS

to clone the screen at 1024x768 resolution to the VGA output (this is the highest shared resolution between the two outputs).

Running the commands

xrandr --output VGA --off
xrandr --output LVDS --auto

should turn off the external video and reset the LCD screen to native resolution. Or you can just disconnect the VGA cable and reboot (just restarting the X server isn't sufficient).

---

### Post by kemal on 2009-04-19
Thanks :)))

---

