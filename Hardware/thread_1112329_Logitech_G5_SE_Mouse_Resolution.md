---
title: "Logitech G5 SE Mouse Resolution"
date: 2009-03-31
forum: Hardware
---

### Post by codeseer on 2009-03-31
I have the Logitech G5 mouse; it's the newer SE (with only one button on the side). This may sound kind of lazy and distant, but I'm looking for some way to automatically set the tracking resolution to 2000 dpi. It has the ability to be set to 2000/800/400, with the press of the plus or minus buttons behind the scroll wheel. Each time I restart, it defaults to 800, which is pretty annoying. Anybody know how to set it? Perhaps a command?

---

### Post by codeseer on 2009-04-01
*bump*

Sorry, if I'm not supposed to bump; I seem to remember reading something about waiting 24 hours to bump a post, so I did for this one. However, I cannot seem to find any rules on this. Let me know if I missed something.

Edit:

With further searching, I discovered lomoco; however, it apparently doesn't work with the G5.

```
:~$ lomoco -p c041 -4
001.004: 046d:c041 G5 Laser Gaming Mouse (M-UAC113) Caps: RES SMS 
lomoco.c:496
Writing to USB device: RES: Broken pipe

:~$ lomoco -p c041 -g
001.004: 046d:c041 G5 Laser Gaming Mouse (M-UAC113) Caps: RES SMS 
lomoco.c:496
Writing to USB device: RES: Broken pipe
```

So, if someone else with a different mouse finds this post and wonders how to set the resolution, give lomoco a try; it's in the repository.

_I am still in search of a solution for the G5._

---

### Post by codeseer on 2009-04-04
Bump?

---

### Post by codeseer on 2009-04-07
I tried changing my xorg.conf as well. I implemented evdev as the driver and tried to set the 'Resolution' option. This did not work either.

Here is the relevant part of xorg.conf:

```

...

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    #InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Logitech-G5" "SendCoreEvents"
EndSection

...

Section "InputDevice"
    # generated from default
    #Identifier     "Mouse0"
    #Driver         "mouse"
    #Option         "Protocol" "auto"
    #Option         "Device" "/dev/psaux"
    #Option         "Emulate3Buttons" "no"
    #Option         "ZAxisMapping" "4 5"
    Identifier     "Logitech-G5"
    Driver         "evdev"
    Option         "Device" "usb-Logitech_USB_Gaming_Mouse-event-mouse"
    Option         "RelHWHEELOptions" "invert"
    Option	   "Resolution" "2000"
EndSection

...

```

Any ideas?

---

### Post by codeseer on 2009-04-16
Bump.

---

### Post by irpg on 2009-07-06
Still interested? I have G5 too, and I want to play with mouse speed same way as SetPoint does in windows. I don't have yet full app finished, but I can already set speed to max, change report rate, switch led's :)

And, btw, isn't SE is that with TWO buttons on the side?

---

### Post by codeseer on 2009-07-06
Yes, I'm still interested in how to do it. The SE is the one with one button on the side.

---

### Post by irpg on 2009-07-06
Try this shortie:
[http://depositfiles.com/files/bo4yv0z43](http://depositfiles.com/files/bo4yv0z43)

If it will work for your mouse, you can set this app in autorun.
You'll need libusb-1.0 installed.

Run it in console first time. Make sure you got message about finding G5 mouse. I check for two IDs - 46d:c041 and 46d:c049

---

### Post by irpg on 2009-07-07
Well, does it work for you?
I have 046d:c049 mouse, and I wonder if your c041 has the same protocol.

---

### Post by codeseer on 2009-07-28
It just keeps saying:

> 
./g5: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory


even though I have my path set to /usr/local/lib and even tried the libusb in the same directory as g5.

---

### Post by irpg on 2009-07-30
Ok, here's sources. Compile for you system.
[http://depositfiles.com/files/uf8kbmxnd](http://depositfiles.com/files/uf8kbmxnd)

---

### Post by Amios on 2010-04-20
> **codeseer said:**
> *bump*

```
:~$ lomoco -p c041 -4
001.004: 046d:c041 G5 Laser Gaming Mouse (M-UAC113) Caps: RES SMS 
lomoco.c:496
Writing to USB device: RES: Broken pipe

:~$ lomoco -p c041 -g
001.004: 046d:c041 G5 Laser Gaming Mouse (M-UAC113) Caps: RES SMS 
lomoco.c:496
Writing to USB device: RES: Broken pipe
```

Get the same Problem with MX1100. Those Links are not up anymore.
> 003.002: 046d:c526 Receiver for MX1100 Laser (C-BUF34) Caps: CSR RES SMS
lomoco.c:495
Writing to USB device: RES: Broken pipe

 Pls reply.

---

