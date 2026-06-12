---
title: "Wacom Tablet cannot use touch anymore"
date: 2012-05-22
forum: Hardware
---

### Post by WG- on 2012-05-22
since I installed 12.04 I cannot use my fingers anymore to navigate on my laptop. I can touch with my finger the screen and then can move the cursor by moving my finger. However when I touch the tablet the cursor stays at the same position it was before, i.e. the cursor doesn't move to the location I touch with my finger the screen...

---

### Post by Favux on 2012-05-22
Hi WG-,

Is touch in Relative and not Absolute Mode?  Check with:
```
xsetwacom get "Serial Wacom Tablet touch" Mode
```
If it is Relative try changing it with:
```
xsetwacom set "Serial Wacom Tablet touch" Mode Absolute
```

---

### Post by WG- on 2012-05-23
Yes that worked! Sadly when i change it in the system setting panel it doesn't.

---

### Post by Favux on 2012-05-23
Good!  :)

I didn't think the Wacom Graphics Tablet applet handled touch yet.  I'm not seeing anything for my tablet PC's touch.  I don't see a key value for touch either with dconf-editor in org>gnome>settings>daemon>peripherals

Say a question.  Do Toshiba tablet PC's send a signal indicating when they are in tablet or laptop mode?  Through ACPI or WMI?

Do you see anything in /sys/devices/platform such as /sys/devices/platform/toshiba?  And then in toshiba say tablet or something similar?  Changing value on rotation say 0 to 1.  It might even be called dock.

---

