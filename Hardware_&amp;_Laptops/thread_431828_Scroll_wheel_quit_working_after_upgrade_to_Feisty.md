---
title: "Scroll wheel quit working after upgrade to Feisty"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by eladner on 2007-05-03
I have a Microsoft (don't ask.. corporate desktop junk) IntelliMouse Optical 1.0A (at least 8 buttons, maybe 9) that doesn't scroll view panes horizontally any more (i.e. in Firefox, etc).

Opening up xev shows that NO events are coming from the buttons.  Middle mouse button paste doesn't even work any more.

I tried setting the Protocol to IntelliMouse and the Buttons to various values in the xorg.conf, but it didn't make a difference. 

Here's the xorg.conf section for the mouse (vanilla, just removed the Emulate3Buttons line)

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

```

This was copied forward from my old xorg.conf from before the upgrade...

Ideas?

---

### Post by Churnd on 2007-05-03
Add these options:

```
Section "InputDevice"
    ...
    Driver "mouse"
    ...
    Option "Emulate3Buttons" "false"
    Option "Buttons"         "7"
    Option "ButtonMapping"   "1 2 3 6 7"
    Option "ZAxisMapping"    "4 5"
    ...
EndSection
```

---

### Post by eladner on 2007-05-03
Changes in effect, but no change to the behavior.  Scroll wheel doesn't work, button 2 doesn't paste the X clipboard and button 2 or scroll wheel events do not register in "xev"

Here's what the mouse section looks like now:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Emulate3Buttons" "false"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
EndSection

```

---

### Post by gusuntu on 2007-05-06
i'm having the same problem w/the same config.   any recommendations out there?

---

### Post by gusuntu on 2007-05-06
following the instructions here worked for me, fyi:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_.26_Configure_IMWheel](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_.26_Configure_IMWheel)

---

