---
title: "power_management_delay"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by kunibert on 2007-11-15
hello, 

i just got my new notebook today and am configuring some stuff to make the battery last longer. i wanted to configure my notebooks backlight dimming similar to the macbooks, where the screen gets dimmed after about 30 secs of inactivity; but you can still see everything on the display, only the backlight is decreased. 
since i did not find a corresponding setting in the ubuntu config tools i messed around with the gconf-editor a bit and found "/apps/gnome-screensaver/power_management_delay". setting this value to 30 (seconds) does exactly what i intended to do, but it only works once. the backlight is dimmed after 30 seconds and the old light level restored after moving the mouse. but surpringsingly the power_management_delay value is set automatically to a seemingly random value after waking up the notebook again. 
does anyone of you guys have an explanation for this strange behaviour?

i am using ubuntu 7.10 (default install, no additional packets installed yet but fully updated) on a dell xps m1330.

regards,
kunibert

---

