---
title: "How to get mouse to turn touchpad on/off"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by eilu on 2007-02-04
So far I have things set so that the touchpad turns off whenever I connect a mouse. I did this by adding ```
Option “SHMConfig” “on”
``` to **xorg.conf**, then under **Preferences> Removeable Drives & Media> Input Devices tab** I enabled "automatically run program when USB mouse is connected" and put ```
synclient TouchpadOff=1
``` as the command. It works like a charm, and when I disconnect the mouse I use the hardware button to turn the touchpad on again.

Now I want to take things to the next level of automation (read: laziness): Is there a way to get dapper to automatically turn the touchpad on when I disconnect the mouse?

---

### Post by steveneddy on 2007-02-04
Cool - let me know if you get a reply to this - I would like to know this also.

---

