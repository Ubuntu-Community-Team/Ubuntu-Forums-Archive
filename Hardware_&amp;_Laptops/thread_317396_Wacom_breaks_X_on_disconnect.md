---
title: "Wacom breaks X on disconnect"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by MKR. on 2006-12-12
Before adding the necessary lines to my x config, my wacom would work, but it wasn't being tracked right (it would never be in the right place when I use the stylus).

I recently added the following lines:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

It works perfectly until I unplug it, at which point the whole system hangs - I can't even switch terminals or restart X. I noticed that when I unplug it, the log viewer shows a new entry just as it crashes, but when I boot back up, no entry is present.


I'm using the proprietary nvidia legacy driver with a geforce3.

So, what am I doing wrong here? :(

---

