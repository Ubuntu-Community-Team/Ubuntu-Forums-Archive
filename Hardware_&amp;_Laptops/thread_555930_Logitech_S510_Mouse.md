---
title: "Logitech S510 Mouse"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by gsoft on 2007-09-20
Im not too worried about the media keys not working on the keyboard, although i am aware of a patch. My issue is the mouse that comes with it. When I am scrolling up no matter which program tried Gnome and KDE so I think its a xserver issue, that the floated menu dock is displayed when scrolling "up" its Ok when scrolling down however.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

This is my xorg.conf file in terms of mouse configuration.

---

### Post by gsoft on 2007-09-21
bump

---

### Post by hebetude on 2007-12-01
open xev.
Mouse to the window that pops up, use your scroll wheel.  Scroll up is button 5 and scroll down is button 4.  This will tell you what those have been mapped to.  If they aren't correct them type this in to correct a broken xmodmap:
```
xmodmap -e "pointer = 1 2 3 4 5 6 7"
```

These functions work out of the box, so either you have mapped the keys incorrectly with some sort of software or there's a hardware problem with your mouse.  As a last resort, you may try the ps/2 connections instead of the USB plug.

If it still doesn't work you should apply the quirk for this keyboard set.  
My howto: [http://ubuntuforums.org/showthread.php?p=3797198](http://ubuntuforums.org/showthread.php?p=3797198)
Reference: [http://ubuntuforums.org/showthread.php?t=82844&highlight=s510](http://ubuntuforums.org/showthread.php?t=82844&highlight=s510)

---

