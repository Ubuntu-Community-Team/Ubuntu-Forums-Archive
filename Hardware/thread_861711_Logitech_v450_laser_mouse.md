---
title: "Logitech v450 laser mouse"
date: 2008-07-16
forum: Hardware
---

### Post by zenkaon on 2008-07-16
Hello,

I have a nice new Logitech v450 laser mouse. It works well, but not perfectly. It has forward and backwards buttons on the wheel and I can't get them working.

The mouse section of my xorg.conf looks like this:
```


Section "InputDevice"

        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name"                          "Logitech USB Receiver"
        Option          "Dev Phys"                      "usb-0000:00:1d.2-1/input0"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
        Option          "SendCoreEvents"                "true"

EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```

which has been hacked together form these forums. No matter what I try (I have been varying this a bit) I get nothing from the left/right buttons in xev.

Mouse works fine in windows with the Logitech software.

Anyone got any ideas?

Cheers

---

