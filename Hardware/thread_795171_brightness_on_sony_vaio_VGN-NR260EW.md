---
title: "brightness on sony vaio VGN-NR260E/W"
date: 2008-05-15
forum: Hardware
---

### Post by cost@s on 2008-05-15
Hi.

I put ubuntu 8.04 with wubi on a sony vaio VGN-NR260E/W laptop.
But the brightness of the screen doesn't work.
&#921; tried to reduse it from F5 ,F6 buttons and from the icon of the brightness.
Neither of these tries works.

Is anyone who knows a solution ?

---

### Post by cost@s on 2008-05-15
Please help.

---

### Post by darthpaul on 2008-06-16
i have the exact same problem with another vaio model. please help.

---

### Post by bhi24 on 2008-07-04
exactly same problem on sony vaio VGN NR260E, with ubuntu 8.04. tried
a) xbacklight (says there is no display with backlight property). 
b) tried the xrandr option - comes up with a 4 line error message.
c) tried downloading video_brightnessup.sh and down scripts from [http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html), and this didn't work.

this is the one thing that keeps me from using ubuntu more than my windows vista partition - ah if only this could be solved!

with thanks to anyone who might suggest other workarounds!
b.

---

### Post by blackened on 2008-10-10
> **bhi24 said:**
> b) tried the xrandr option - comes up with a 4 line error message.

Which xrandr option?

I have a VGN-NR385E and got it working by doing the following:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

and then control it with xbacklight -set commands. I may have used sudo on the xrandr command.

---

### Post by paraglider on 2009-10-05
Have the same problem, any fixes yet?

cheers

---

