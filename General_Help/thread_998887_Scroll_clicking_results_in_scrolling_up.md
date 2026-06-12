---
title: "Scroll clicking results in scrolling up"
date: 2008-12-01
forum: General Help
---

### Post by Duranxl on 2008-12-01
Hi,

I've had this logitech optical mouse for a while, and it will always scroll up when i pressed down on the scroll button. I figured it was broken.
However today i bought a new mouse and it does the same thing.. so it must be ubuntu.
If I press down on the scroll button it will keep on scrolling up..so i can't scroll click on links in firefox

OS: Ubuntu 8.10 64bit
Mouse: Logitech RX1000
Config (not default, but that didnt work either):
```
Section "InputDevice"
        Identifier "Logitech RX1000"
        Driver "evdev"
        Option "Protocol" "evdev"
        Option "Name" "Logitech USB Optical Mouse"
        Option "Phys" "usb-*/input0"
        Option "Device"
        Option "Buttons" "8"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "1000"
        Option "CorePointer"
EndSection
```

Thanks

---

### Post by ohzopants on 2008-12-01
Check out this article:
[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

The specifics of your xorg might be slightly different, but that page explains how to find the proper values.

---

### Post by Duranxl on 2008-12-01
I'm now using this xorg:
```
Section "InputDevice"
        Identifier "Logitech RX1000"
        Driver "evdev"
        Option "Protocol" "evdev"
        Option "Name" "Logitech USB Optical Mouse"
        Option "Phys" "usb-*/input0"
        Option "Device"
"/dev/input/by-id/usb-Logitech_USB_Optical_Mouse-event-mouse"
        Option "Buttons" "8"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "1000"
        Option "CorePointer"
EndSection
```
From this site i found.

I now noticed that it works, but my rx1000 has this function that allows me to scroll up/down by moving the scroll-button left/right.
However i keep finding myself pushing it to the left or right when press down on the scroll-button.
Any way to assign all 3 (left, down, right) buttons of the scroll to "mousebutton3"?

Thanks

---

### Post by Duranxl on 2008-12-02
Bump

---

### Post by ohzopants on 2008-12-03
Check out this post:
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

Particularly the part about xvkbd and xbindkeys.  I think that's what you need to use.

good luck.

---

### Post by Duranxl on 2008-12-03
> **ohzopants said:**
> Check out this post:
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

Particularly the part about xvkbd and xbindkeys.  I think that's what you need to use.

good luck.

What about it? My site buttons work fine, i just want to re-assign them so that they are all "scrollCLICK".

---

### Post by ohzopants on 2008-12-03
You can use xbinkeys to bind the left and right scroll "buttons" to mouse button 3 (which is what i think middle click is).

---

### Post by Duranxl on 2008-12-04
> **ohzopants said:**
> You can use xbinkeys to bind the left and right scroll "buttons" to mouse button 3 (which is what i think middle click is).

It says 
> "Note: Same as before, if you have different mouse buttons use xev to find out what number they are and change the "b:6" and "b:7" in the above to the correct numbers"
However xev (little box?) doesnt detect anything, and neither does xbindkeys -k.
:(

---

### Post by Duranxl on 2008-12-29
bump

---

### Post by Duranxl on 2009-01-05
bump..!

---

### Post by Duranxl on 2009-01-12
Kick!

edit: why is there STILL no 64bit version of HIDpoint -.-....

---

### Post by Duranxl on 2009-03-18
Bump

---

