---
title: "Mouse Malfunctioning"
date: 2008-08-01
forum: General Help
---

### Post by neoaddict on 2008-08-01
Yeah, a series of mouse malfunctions.  o_O  One minute it was working fine, next it started to malfunction.

1) Middle-click does nothing
2) Whenever I click a menu in GNOME, it appears and disappears in a split second
3) Can't left-click on a panel launcher
4) Nautilus is interpreting my singleclick as a doubleclick

Any ideas?  :confused:

---

### Post by Sef on 2008-08-01
1) What make and model mouse do you have?

2) How is it plugged in?

---

### Post by neoaddict on 2008-08-01
1) Generic PS/2 mouse.
2) Via the mouse port in the back.

---

### Post by neoaddict on 2008-08-01
Never mind, it appears to be working now.  :).

Changed my xorg.conf with:

```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "True"
EndSection
```

---

