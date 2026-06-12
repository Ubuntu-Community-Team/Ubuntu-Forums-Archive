---
title: "Can't get rid of weird &quot;two finger tap-scrolling&quot;, Ubuntu 10.04 32-bit"
date: 2011-01-06
forum: Hardware
---

### Post by black plague on 2011-01-06
I have an HP Mini 210-1030NR that I periodically fight with to get decent two-finger scrolling going.  It has a touchpad with the buttons integrated right into the touchpad surface, a la Apple.

Usually, messing with it, I'm not too afraid because most changes will usually be reset to the default with a reboot.  But recently I noticed my touchpad doing something really weird......if I press two fingers on the touchpad, it'll start scrolling, seemingly randomly either up or down the page.

I cannot figure out what the hell I did to enable this strange feature, but I also can't make it go away.  Between the X.org settings, the udev settings, etc., I don't know which group of settings is taking precedence, which one is being ignored, etc.

All I know is, from checking the bash history, at some point I input these commands

```
dan@killmachinejr:/etc/udev$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
dan@killmachinejr:/etc/udev$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
dan@killmachinejr:/etc/udev$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
dan@killmachinejr:/etc/udev$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```**I DON'T KNOW IF THAT'S WHAT'S CAUSED THIS STRANGE BEHAVIOR**, it's just the best I could do to retrace my steps.  I know I tried a lot of stuff I found on different threads here regarding enabling two-finger scrolling.

If anyone is willing to tackle this challenge, here is some troubleshooting info for you guys....


the X.org log
```
dan@killmachinejr:/etc/udev$ grep touchpad /var/log/Xorg.0.log
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found
```synclient settings
```
dan@killmachinejr:/etc/udev$ synclient -l
Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 64
    ClickFinger2            = 12
    ClickFinger3            = -17
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0
```the xinput properties
```
dan@killmachinejr:/usr/lib/X11/xorg.conf.d$  xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Webcam-50                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

dan@killmachinejr:/etc/udev$ xinput list-props 11
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (134):    1
    Device Accel Profile (250):    0
    Device Accel Constant Deceleration (251):    1.000000
    Device Accel Adaptive Deceleration (253):    1.000000
    Device Accel Velocity Scaling (254):    10.000000
    Synaptics Edges (255):    1752, 5192, 1620, 4236
    Synaptics Finger (256):    24, 29, 255
    Synaptics Tap Time (257):    180
    Synaptics Tap Move (258):    221
    Synaptics Tap Durations (259):    180, 180, 100
    Synaptics Tap FastTap (260):    0
    Synaptics Middle Button Timeout (261):    75
    Synaptics Two-Finger Pressure (262):    280
    Synaptics Two-Finger Width (263):    7
    Synaptics Scrolling Distance (264):    100, 100
    Synaptics Edge Scrolling (265):    1, 0, 0
    Synaptics Two-Finger Scrolling (266):    0, 0
    Synaptics Move Speed (267):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (268):    29, 159
    Synaptics Edge Motion Speed (269):    1, 401
    Synaptics Edge Motion Always (270):    0
    Synaptics Button Scrolling (271):    1, 1
    Synaptics Button Scrolling Repeat (272):    1, 1
    Synaptics Button Scrolling Time (273):    100
    Synaptics Off (274):    0
    Synaptics Guestmouse Off (275):    0
    Synaptics Locked Drags (276):    0
    Synaptics Locked Drags Timeout (277):    5000
    Synaptics Tap Action (278):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (279):    64, 12, -17
    Synaptics Circular Scrolling (280):    0
    Synaptics Circular Scrolling Distance (281):    0.100000
    Synaptics Circular Scrolling Trigger (282):    0
    Synaptics Circular Pad (283):    0
    Synaptics Palm Detection (284):    0
    Synaptics Palm Dimensions (285):    10, 199
    Synaptics Coasting Speed (286):    0.000000
    Synaptics Pressure Motion (287):    29, 159
    Synaptics Pressure Motion Factor (288):    1.000000, 1.000000
    Synaptics Grab Event Device (289):    1
    Synaptics Gestures (290):    1
    Synaptics Capabilities (291):    1, 1, 1, 0, 0
    Synaptics Pad Resolution (292):    97, 66
    Synaptics Area (293):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (294):    0
```There is nothing in my udev.conf or rules.d files in /etc/udev

Finally, the 10-synaptics.conf file in X.org
```
dan@killmachinejr:/usr/lib/X11/xorg.conf.d$ cat 10-synaptics.conf
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron embedded buttons quirks"
    MatchTag "inspiron_1011|inspiron_1012"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection
```Thanks in advance!

---

### Post by pi/roman on 2011-01-06
Is two finger scrolling enabled in gnome-mouse-properties?

---

### Post by black plague on 2011-01-06
In the normal Mouse Preferences, the "Two-Finger Scrolling" option is grayed out (and not selected), but "Edge Scrolling" is selected and works fine.

In gpointing-device-settings ("Pointing devices" in the Preferences menu), the "Enable vertical scrolling when dragging with two fingers" option is not selected.

---

### Post by pi/roman on 2011-01-06
Check to see that scroll method is not 2 here

```
gconftool -R /desktop/gnome/peripherals/touchpad | grep scroll_method
```Look for more configuration files:
```
sudo find /usr /etc -name '*synaptic*conf'
```Also check in /etc/X11/xorg.conf

also look for more udev rules
'```
sudo find /usr /etc -name *.rules | grep -iE 'touchpad|synaptic'
```

---

### Post by black plague on 2011-01-08
```
dan@killmachinejr:~$ gconftool -R /desktop/gnome/peripherals/touchpad | grep scroll_method
 scroll_method = 1
```

The only *synaptic*conf file it found was the 10-synaptics.conf from my first post.

No additional udev rules were found either.

The only xorg.conf file in /etc/X11 was titled xorg.conf.failsafe and here are the contents...

```
dan@killmachinejr:/etc/X11$ cat xorg.conf.failsafe
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by black plague on 2011-01-08
And now..................it's gone. :confused:

Once again, the first two rules of computer troubleshooting strike again.

First two steps to fix any problem
1.) Reboot
2.) Tell someone else to come look at the problem

Why is it that when someone else comes to see it, the issue almost always goes away :mrgreen:

Thanks for your help, pi/roman

---

