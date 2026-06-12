---
title: "Mouse / Touchpad issues."
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by teevee on 2005-10-18
Plugged in a standard PS/2 three-button wheel mouse on a Gericom Webboy. But wheel is not working. :-/ Left, middle and right buttons all behave normally. xorg.conf seems to be set up correctly, xev also doesn't recognize "buttons" 4+5.

Also, tapping on the touchpad is not possible if the mouse is plugged in. Otherwise it works as normal.

xorg.conf relevant sections:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "5"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```

---

### Post by civilwarlord on 2005-10-18
Below is my mouse section, when my external mouse is plugged in, everything works, but mine is only 3 buttons: left, right & scroll wheel button.  I noticed you have the "Emulate3Buttons" option set to "false".  Have you tried setting it to "true"?  Also, the "Buttons" section in your xorg.conf, did you put that in yourself or was it automatic?  You could also try removing it, but it might make things worse, though you can always put it back in.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "MaxTapTime"            "0"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "MaxTapTime"            "0"
        Option          "HorizScrollDelta"      "0"
EndSection

```

---

### Post by luopio on 2005-12-05
Just tweaked my touchpad to perfection :). Here are the relevant parts from my xorg.conf. The circular scrolling feature is excelent when browsing through long documents or reading ebooks. Just do a circle with your finger to scroll (and I think windows users don't get this with regular synaptics touchpads!)

Section Module:
```
Load		"synaptics"
```

Section InputDevice:
```
Section "InputDevice"
    Driver    "synaptics"
    Identifier    "Synaptics Touchpad"
    Option     "Device"        "/dev/input/mouse0"
    Option    "Protocol"       "auto-dev" # "event"
    # Option    "LeftEdge"      "1700"
    # Option    "RightEdge"     "5300"
    # Option    "TopEdge"       "1700"
    # Option    "BottomEdge"    "4200"
    Option    "FingerLow" "25"
    Option    "FingerHigh"    "30"
    Option    "MaxTapTime"    "180"
    Option    "MaxTapMove"    "220"
    Option    "VertScrollDelta" "100"
    Option    "MinSpeed"  "0.06"
    Option    "MaxSpeed"  "0.12"
    Option    "AccelFactor" "0.0010"
    Option   "SHMConfig" "on"
    Option          "Buttons"               "6"
    # Option   "Repeater"  "/dev/ps2mouse"
    Option     "CircularScrolling"    "1"
    Option     "CircScrollDelta"      "0.1"
    Option     "CircScrollTrigger"    "4"
    # Trigger region on the touchpad to start circular scrolling
    # 0=All Edges, 1=Top Edge, 2=Top Right Corner, 3=Right Edge,
    # 4=Bottom Right Corner, 5=Bottom Edge, 6=Bottom Left Corner,
    # 7=Left Edge, 8=Top Left Corner
EndSection
```

Section ServerLayout:
```
       InputDevice "Keyboard1" "CoreKeyboard"
        InputDevice	"Synaptics Touchpad" "AlwaysCore"
	InputDevice	"USB Mouse"
```

Actually the 'Option     "Device"        "/dev/input/mouse0"' line is redundant, cos' auto-dev assings it automatically to the relevant event*-device, but it doesn't hurt. I'm not sure if you need the "Buttons" variable for synaptics, but I have it there, just for fun. I guess I could add emulate3buttons also, but I'll leave it for now :)

---

### Post by mohitcool_buddy on 2005-12-05
this is so................................boorrrrring

---

### Post by atoponce on 2005-12-05
[quote=mohitcool_buddy]this is so................................boorrrrring[/quote] What do you expect coming to a technical support forum?  Women jumping out of a cake while playing Doom 3?  Just curious.

---

