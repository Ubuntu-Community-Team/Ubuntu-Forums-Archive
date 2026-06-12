---
title: "delay in tap responding on touchpad"
date: 2008-05-14
forum: Hardware
---

### Post by m3alnemer on 2008-05-14
Hi!:)

I have been reading a lot of threads to configure my touch pad setting.
I could set everything as i want, but still there is one that i don't know how to figure out. There is a pet of a second delay when tapping on touch pad. you may feel it if you compare it with the click button. Ubuntu takes respond faster if button clicked than if tapped.

My laptop TOSHIBA M70
Ubuntu Gusty (7.10)

```

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"            "/dev/psaux"
    Option	  "Protocol"	      "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "25"
    Option  "FingerHigh"            "30"
    Option  "MaxTapTime"            "180"
    Option  "MaxTapMove"            "220"  #fdfsgfs
    Option  "MaxDoubleTapTime"      "180"
    Option  "ClickTime"  	    "50"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "50"
    Option  "HorizScrollDelta"      "30"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "1.00"
    Option  "AccelFactor"           "0.030"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "1"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection
```]

This slow tapping is killing me.(*,)
So any suggestions ?

---

### Post by m3alnemer on 2008-05-15
No Suggestions?:confused:

---

### Post by prshah on 2008-05-15
> **m3alnemer said:**
>  There is a pet of a second delay when tapping on touch pad. you may feel it if you compare it with the click button. 
```

Section "InputDevice"
<snip>
    Option  "ClickTime"  	    "50"
<snip>
EndSection
```]


Maybe you should try commenting out the above option? (edit the /etc/X11/xorg.conf file as sudo, then locate this line, and place a "#" in front of it.). Save, quit, logout, restart X server with Ctrl+Alt+BkSpace. Is it OK now?

---

### Post by m3alnemer on 2008-05-15
Did, Still button faster than tap.

Is there something different for the alps touch pad?

I was trying to set options and by chance changed protocol or device(not sure which one). there were a sitting that faster than now. I tried to look for it but never found it again:(

---

### Post by m3alnemer on 2008-05-17
The same situation in Hardy in my other laptop:( Slow tap respond

Is setting the Wireless mouse hard on ubuntu:confused:?

---

### Post by tirade on 2008-12-23
I've got this problem too on Intrepid using my Vaio VGN-FS640/W.

I haven't tried anything yet, but I'll post here if I find a solution.

---

### Post by tirade on 2008-12-23
I used the instructions here:
[http://www.ubuntumini.com/2008/11/configure-synaptics-touchpad-ubuntu-810.html](http://www.ubuntumini.com/2008/11/configure-synaptics-touchpad-ubuntu-810.html)
and installed gsynaptics, and under the Tapping tab I checked "enable faster tapping."

It appears to have worked to a slight degree, but I don't think I've truly fixed the problem. Let me know how it works for you, if you're still trying to solve this.

---

