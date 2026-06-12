---
title: "Extra mouse button and firefox"
date: 2008-09-11
forum: General Help
---

### Post by mikeyfbi on 2008-09-11
Hey Guys,

I'm not sure where this should go, so please move it if it's in the wrong place.

I just upgraded to a fresh install of 8.04.

I'm using a Logitech MX Revolution mouse.  With my previous version of Ubuntu (Gusty) and FF2, one of the side buttons (Button8 I think) was very very handy...when I hovered over a link, and clicked it with that button, it would open in a new tab.  I don't know how many times I used that a day, but it was a phenomenal feature.

Also, when I hovered over a tab, and clicked it with that button, it would close it.

But now, Button8 and 7 are used for Forward and Back in the browser, and I have NO idea how to revert it back to what it use to do :confused:

If anyone has any ideas, it would be much appreciated!

Mike

---

### Post by kerry_s on 2008-09-11
```
Section “InputDevice”
Identifier “Mx Rev”
Driver “evdev”
Option “Protocol” “Auto”
Option “Name” “Logitech USB Receiver”
Option “Phys” “usb-*/input0
EndSection
```

---

### Post by 16777216 on 2008-09-11
> **kerry_s said:**
> ```
Section “InputDevice”
Identifier “Mx Rev”
Driver “evdev”
Option “Protocol” “Auto”
Option “Name” “Logitech USB Receiver”
Option “Phys” “usb-*/input0
EndSection
```


Just incase you didn't know the above replaces the mouse part of your **/etc/X11/xorg.conf** file.

To edit it you must have administrator privileges, this is simple press **alt+F2** to open the run dialog and type.. ```
gksudo gedit /etc/X11/xorg.conf
``` save it and log out then back in and you should be good to go. ( I think. )
My instructions are good but I don't know about kerry_s's because the defaults work fine for me, I have never spent more than 5 USD for a mouse. :lolflag:

---

### Post by mikeyfbi on 2008-09-12
> **kerry_s said:**
> ```
Section “InputDevice”
Identifier “Mx Rev”
Driver “evdev”
Option “Protocol” “Auto”
Option “Name” “Logitech USB Receiver”
Option “Phys” “usb-*/input0
EndSection
```

Thanks, it's just missing a " on the last one there...found that out the hard way :lolflag:

But it didn't seem to change anything...lol!  I'm not sure if there is an extra step or what this really did...:confused::)

Mike

---

