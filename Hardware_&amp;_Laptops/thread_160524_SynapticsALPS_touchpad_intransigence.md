---
title: "Synaptics/ALPS touchpad intransigence"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by richardh on 2006-04-15
Trying to get my touchpad to work consistently.
](*,) 
When running breezy, changed xorg.conf as given elsewhere in forum (main thing is the "device /dev/input/event2 line", but other options nice). Touchpad worked.

Updated to dapper, initially no problem, then everything stopped working (viz., touchpad operated at minimal level - no acceleration no scrolling etc).

Found fix on forum, changed back to Xfree drivers. Touchpad worked.

Just rebooted this morning, touchpad not working again. What gives? 

I tried installing ksynaptics, which changed the drivers back to the xorg defaults. 

kynaptics does not work. On launch it gives an error about SHConfig, but that option is set to 'on' in my xorg.conf file.

Very frustrated.

---

### Post by oscar on 2006-04-15
Try using /dev/psaux as your device, it works for me. Your post inspired me to try to get dragging and dropping working properly. I have something but it's not quite right. When selecting text for example I have to tripple tap to start selecting, tap to stop, then double tap and drag to move but it doesnt seem consistent. Here is the relavent section of my xorg.conf. (I have a sony vaio vgn-s3xp with an alps touchpad).
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"        "true"
    Option        "Device"                "/dev/psaux"
    Option        "Protocol"              "auto-dev"
    Option        "SHMConfig"             "on"
    Option        "LeftEdge"              "100"
    Option        "RightEdge"             "950"
    Option        "TopEdge"               "80"
    Option        "BottomEdge"            "700"
    Option        "FingerLow"             "14"
    Option        "FingerHigh"            "15"
    Option        "MaxTapTime"            "180"
    Option        "MaxTapMove"            "110"
    Option        "EmulateMidButtonTime"  "0"
    Option        "VertScrollDelta"       "20"
    Option        "HorizScrollDelta"      "20"
    Option        "MinSpeed"              ".5"
    Option        "MaxSpeed"              "2"
    Option        "AccelFactor"           "0.015"
    Option        "EdgeMotionMinSpeed"    "200"
    Option        "EdgeMotionMaxSpeed"    "200"
    Option        "UpDownScrolling"       "1"
    Option        "CircularScrolling"     "1"
    Option        "CircScrollDelta"       "0.1"
    Option        "CircScrollTrigger"     "2 "
    Option        "ClickTime"             "50"
    Option        "MaxDoubleTapTime"      "500"
    Option        "LockedDrags"           "off"
EndSection
```

You can tune your settings using:
```
 synclient  -m  1
```

[edit]I improved my dragging behaviour by increasing max doubletaptime and turning locked drags off[/edit]

---

### Post by brallan on 2006-04-15
I'm working on a wiki, at [SynapticsTouchpadHowTo]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo")

please let me know if you see any mistakes or omissions.

thanks,
brian

---

### Post by brallan on 2006-04-15
I'm working on a wiki, at [SynapticsTouchpadHowTo]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo")

please let me know if you see any mistakes or omissions.

thanks,
brian

---

