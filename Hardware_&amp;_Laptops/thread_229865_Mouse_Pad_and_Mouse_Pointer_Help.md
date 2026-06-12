---
title: "Mouse Pad and Mouse Pointer Help"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by adds2one on 2006-08-05
Hello,

How can I adjust the responsiveness of my Mouse Pad? Making changes in Gnome System->Preferences->Mouse->Motion doesn't change the response of my  Mouse Pad, just the responsiveness of the Mouse Pointer(that nubby little thing on the keyboard)

I would actually like to turn the Mouse Pointer thing off and just use the Mouse Pad. Is this possible?

Here is the mouse data from my xorg.conf file:
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection
```

---

### Post by wireddad on 2007-08-25
Anyone has ideas on this?  Or can provide a link to a tutorial?  Thanks.

---

