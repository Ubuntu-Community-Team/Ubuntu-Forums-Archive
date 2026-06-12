---
title: "Touchpad Tap-Click"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by JPMaximilian on 2006-12-07
Is there a way to disable the touchpad "tap-click" the way I use my touchpad I tend to pick up my finger a lot and put it back down to move the mouse around, and this results in my accidentally clicking a lot of things.  I looked over xorg.conf and I don't see anything obvious to disable or change.  Thanks!

---

### Post by djf_jeff on 2006-12-07
Add these line to your xorg.conf in the synaptic section and restart X or reboot : 

Option          "MaxTapTime"            "0"

---

### Post by mandragor on 2006-12-09
This has been an issue for me ever since Dapper I think, I am unable to
turn off tapping! I have tried every tap-related setting and even
ksynaptics tells me that tapping is turned off. But it is not.
Also, if I after logging in to X restart it by pressing CTRL+ALT+BACKSPACE
it works, not if I do a complete reboot.

Here's the relevant sections from my xorg.conf:
Section "InputDevice"
        Identifier "ALPS"
        Driver "synaptics"
        Option "AlwaysCore"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "LeftEdge" "120"
        Option "RightEdge" "830"
        Option "TopEdge" "120"
        Option "BottomEdge" "650"
        Option "FingerLow" "14"
        Option "FingerHigh" "15"
        #set MaxTapTime to 0 to disable tap-to-click
        Option "MaxTapTime" "0"
        Option "MaxTapMove" "0"
        Option "MaxDoubleTapTime" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
        Option "ClickTime" "0"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "10"
        Option "HorizScrollDelta" "0"
        Option "MinSpeed" "0.45"
        Option "MaxSpeed" "0.75"
        Option "AccelFactor" "0.020"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "0"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "on"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "ALPS"
EndSection

---

### Post by sandman652001 on 2006-12-09
This helped me
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf)

---

### Post by whoismilan on 2006-12-09
I did it by following the instructions on: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

First I edited xorg.conf to include the touchpad, then I installed qsynaptics from the repositories.

---

