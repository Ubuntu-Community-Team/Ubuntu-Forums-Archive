---
title: "alps track pad problem - dell 9300"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by ghosthand on 2006-06-30
Just installed linux/ubuntu on this laptop for the first time last weekend.  My alps track pad is having a strange problem - I can not drag stuff very easily.  Dragging icons, resizing windows, moving windows - all those types of activities are hard to initiate.  I can sometimes resize windows by triple-tapping.  I have tapping enabled - I actually like tapping, and have never had any problems before.  Anybody ever heard of a problem like this?  Strange thing is that I had everything working fine earlier and then had to reinstall ubuntu - I saved my xorg.conf though, and just copied it back in /etc/X11 after ubunut finished installing.  Everything worked fine except my trackpad:

```
ection "InputDevice"
    Identifier     "Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "LeftEdge" "120"
    Option         "RightEdge" "830"
    Option         "TopEdge" "120"
    Option         "BottomEdge" "650"
    Option         "FingerLow" "14"
    Option         "FingerHigh" "15"
    Option         "MaxTapTime" "180"
    Option         "MaxTapMove" "110"
    Option         "EmulateMidButtonTime" "75"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "20"
    Option         "MinSpeed" "0.3"
    Option         "MaxSpeed" "0.75"
    Option         "AccelFactor" "0.015"
    Option         "EdgeMotionMinSpeed" "200"
    Option         "EdgeMotionMaxSpeed" "200"
    Option         "UpDownScrolling" "1"
    Option         "CircularScrolling" "1"
    Option         "CircScrollDelta" "0.1"
    Option         "CircScrollTrigger" "1"
    Option         "InputFashion" "Mouse"
    Option         "SHMConfig" "on"
    Option         "ZAxisMapping" "4 5"
EndSection

```

my Xorg.0.log doesn't show any errors either.

```
(II) Synaptics touchpad driver version 0.14.3
(--) Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "830"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "650"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "1"
(--) Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Touchpad touchpad found
ProcXCloseDevice to close or not ?

```

---

### Post by ghosthand on 2006-07-01
I think upgrading to kernel 2.6.15 686 version fixed this - the alps track pad is working perfectly now

---

