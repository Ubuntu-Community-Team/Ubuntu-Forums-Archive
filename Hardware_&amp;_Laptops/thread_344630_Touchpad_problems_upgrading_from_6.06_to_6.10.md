---
title: "Touchpad problems upgrading from 6.06 to 6.10"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by jacod on 2007-01-23
A few days ago I upgraded an ACER TM4020 laptop from 6.06 to 6.10 and the touchpad stopped working. It seems to be correctly configured and loaded, but it doesn't work. There is also a USB mouse configured and it is working correctly. Unplugging the USB mouse doesn't seem to affect the touchpad.

Relevant sections of /etc/X11/xorg.conf:
```

(...)
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
(...)
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
(...)

```

In /var/log/Xorg.0.log everything looks fine to me...
```

(...)
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
ProcXCloseDevice to close or not ?
(II) 3rd Button detected: disabling emulate3Button

```

, except for the "ProcXCloseDevice to close or not ?" line.

This is what dmesg says about the device:
```

(...)
[17179600.556000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[17179600.596000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
(...)

```

The touchpad is not disabled in synclient:
```

#~$ synclient -l | grep Touchpad
TouchpadOff          = 0

```

Any suggestions will be appreciated, thanks in advance.

David

---

### Post by ramjet_1953 on 2007-02-05
Hi, there!

Have you tried Fn+F7?

This toggles the touchpad on and off on an Acer Lappy.

Works on my Acer TravelMate 4101.

Regards,
Roger :cool:

---

