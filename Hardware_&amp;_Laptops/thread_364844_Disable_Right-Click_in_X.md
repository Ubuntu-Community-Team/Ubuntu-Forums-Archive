---
title: "Disable Right-Click in X"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by HowardDrake on 2007-02-18
I'm setting up an Ubuntu box for a kiosk-like application. The problem is that the users want to attempt to mess with the system by right-clicking on the top panel to attempt to add buttons, add apps, etc. How do I modify xorg.conf so that the right mouse button is also the left mouse button? I'm guessing that it has to do with the ButtonMapping option in the conf file, would this work?

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
# Added Option
Option "ButtonMapping "1 1"
#End of Add

        Option          "Emulate3Buttons"       "true"
EndSection

```

Also this is a global option, can I modify this for a given user, so that when I connect as an admin it doesn't do it? If I have to I'll go in and manually comment out the line, but it would be nice.

TIA

-Howard

---

