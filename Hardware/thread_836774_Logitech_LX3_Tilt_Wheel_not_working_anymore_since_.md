---
title: "Logitech LX3 Tilt Wheel not working anymore since upgrade to 8.04"
date: 2008-06-21
forum: Hardware
---

### Post by LingLing on 2008-06-21
I need some help with my Logitech LX3 mouse. I got used to using the tilt wheel to do horiz. scrolling and switch back and forward in firefox under ubuntu 7.10. Unfortunately it's not working any more in 8.04.

This is what i did to get it working in 7.10 (/etc/X11/xorg.conf):

```
Section "InputDevice"
        Identifier      "Logitech"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
	Option "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

And this is what I found on another web page to get it working in 8.04

```
Section "InputDevice"
        Identifier      "Logitech2"
        Driver          "evdev"
        Option          "Name" "Logitech USB-PS/2 Optical Mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        
"/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
EndSection

```

And this is Section Serverlayout

```

	Inputdevice     "Logitech2" "SendCoreEvents"

```

Unfortunately both versions don't get the tilt wheel working in 8.04. Any suggestions?
Thanks!

---

### Post by LingLing on 2008-06-28
I'd like to bump this because it's still bugging me.
Isn't there anybody out there that got the tilt wheel working? maybe with another model than LX3?

---

### Post by blaser on 2008-08-02
This is how I got my LX3 to work ```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
    Option         "SendCoreEvents" "true"
#    Option         "HWHEELRelativeAxisButtons" "7 6"
    Option         "RelHWHEELMapTo" "Buttons 7 6 1" 
EndSection

```    

Looks like the "HWHEELRelativeAxisButtons" option has been removed. I found a bug report [http://www.mail-archive.com/debian-x@lists.debian.org/msg72490.html]("http://www.mail-archive.com/debian-x@lists.debian.org/msg72490.html") that talks about it.

---

### Post by LingLing on 2008-08-08
Thanks alot for the input.
But alas, it still does not work on my box. :confused:

I tried both, the back/forward switching in firefox and the sidescrolling in documents and neither worked.

Do you have any special entries in Section ServerLayout?

---

### Post by dli8ilb on 2008-12-31
this worked for me:

```
Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "evdev"
   Option      "CorePointer"
   Option      "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
   Option      "RelHWHEELMapTo" "Buttons 7 6 1"
EndSection
``` 

add this extry to the "ServerLayout" section
```

InputDevice   "Mouse0"      "CorePointer"
```


save and restart Xserver (Ctrl+Alt+Backspace)

---

