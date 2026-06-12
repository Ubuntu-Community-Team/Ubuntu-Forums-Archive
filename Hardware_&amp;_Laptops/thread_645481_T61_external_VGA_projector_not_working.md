---
title: "T61 external VGA projector not working"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by chuckNbanna on 2007-12-20
Hello - I am running 7.10 on a ThinkPad T61.  I am using the out of the box nvidia drivers and did nothing to configure the monitors.

I just bought a sanyo projector and tried to use it using the System->Admin->Screens... route.

On that screen, I change Screen 2 to secondary, mirror default, and click 'OK'

nothing happens, it does not accept the input.  clickclick - nothing happens.

when I go back to Screen 1, it shows the same attributes as Screen 2.

Any help?

Thanks in advance.

---

### Post by jerone on 2008-01-06
So the display configuration tool is majorly broken (sad but true). The way you do it is you run xrandr. So to expand over to your projector , open a command terminal and do one of the following commands:

to expand your desktop:
           xrandr --output VGA --right-of LVDS --auto

to clone your desktop:
           xrandr --output VGA --same-as LVDS --auto
         *Note that you are going to want your laptop screen at the same res of the projector the projector may not be able to display everything that is on your screen.

---

