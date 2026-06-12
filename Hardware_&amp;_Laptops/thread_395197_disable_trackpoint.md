---
title: "disable trackpoint"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by dj604 on 2007-03-27
HI,

My Toshiba Satellite Pro 6100 has a trackpoint pointer that has a mind of it's own.  It's definitely a hardware problem (occurs on several OS's), but there's no way in the BIOS to turn it off.  I'd like to just use an external USB mouse and disable it.  Is there anyway to do this?

Thanks!

---

### Post by josephus on 2007-03-30
*edit:  i don't think this actually works*

Too bad your trackpoint is on the fritz.  I don't know how I could live without mine.

Anyways, I haven't tried this out myself but I think that you can disable the trackpoint by playing with /etc/X11/xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

You'll probably want to make a copy of it first before messing around with it.

In my xorg.conf, this is the section which configures the trackpoint

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "EmulateWheel"          "on"
        Option          "EmulateWheelButton"    "2"
        Option          "EmulateWheelTimeOut"   "1"     # gets rid of the annoying middle button paste
        Option          "EmulateWheelInertia"   "20"
EndSection
```

you'll have something similar in your configuration file.

and this is the section which maps it to the x server

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
```

To remove the trackpoint, I think it's sufficient to just comment out the configured mouse (i.e # InputDevice "Configured Mouse")


Make the change and restart using (ctrl-alt-backspace)

*edit:  i don't think this actually works*

---

