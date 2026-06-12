---
title: "Editing xorg.conf"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2008-01-11
This is a machine that I'm having trouble with: I'll have normal log-ins sometimes, then at other times the resolution will be all wonky. 
Does anyone have any input? 
Thanks in advance. 

```
Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
    Driver        "via"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Avitron"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
    Monitor        "Avitron"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection
```

---

### Post by mdpalow on 2008-01-11
what is this "Wonky" you speak of? ;)

Better description please...

---

### Post by teejay17 on 2008-01-11
> **mdpalow said:**
> what is this "Wonky" you speak of? ;)

Better description please...
Sorry. Wonky as in super stretched out and off, like the resolution is too high for what the monitor can display. 
Then, when I restart the computer, everything is fine again. 
Something, resolution wise, is happening in the back end.

---

### Post by zxscooby on 2008-01-11
what resolution mode is it in when its wonky? 
 
I would try removing that resolution mode from the screen section and see if that helps. not without making a backup copy first.
i think the safest mode to use is 1024x768
someone correct me if im wrong.

---

### Post by teejay17 on 2008-01-11
> **zxscooby said:**
> what resolution mode is it in when its wonky? 
 
I would try removing that resolution mode from the screen section and see if that helps. not without making a backup copy first.
i think the safest mode to use is 1024x768
someone correct me if im wrong.
Yeah, it's supposed to be 1024X768. So if I remove the other resolutions that shouldn't be there, then my machine won't load into resolutions that it shouldn't?

---

### Post by teejay17 on 2008-01-13
Everything worked out well. Thanks.

---

### Post by zxscooby on 2008-01-14
cool!

---

