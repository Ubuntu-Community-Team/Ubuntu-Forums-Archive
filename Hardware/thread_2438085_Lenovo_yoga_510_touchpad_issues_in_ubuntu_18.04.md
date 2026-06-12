---
title: "Lenovo yoga 510 touchpad issues in ubuntu 18.04"
date: 2020-03-05
forum: Hardware
---

### Post by jorzallan on 2020-03-05
Hello,

My touchpad doesn't behave correctly. Whenever i move the cursor diagonally, i moves in a zigzag manner. i believe it is something to do with sensitivity problem. Below is the output of
```
  xinput --watch-props 13 
```

output:
```

    Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (168):    1
    Coordinate Transformation Matrix (170):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (310):    1
    libinput Tapping Enabled Default (311):    0
    libinput Tapping Drag Enabled (312):    1
    libinput Tapping Drag Enabled Default (313):    1
    libinput Tapping Drag Lock Enabled (314):    0
    libinput Tapping Drag Lock Enabled Default (315):    0
    libinput Tapping Button Mapping Enabled (316):    1, 0
    libinput Tapping Button Mapping Default (317):    1, 0
    libinput Natural Scrolling Enabled (318):    1
    libinput Natural Scrolling Enabled Default (319):    0
    libinput Disable While Typing Enabled (320):    1
    libinput Disable While Typing Enabled Default (321):    1
    libinput Scroll Methods Available (322):    1, 1, 0
    libinput Scroll Method Enabled (323):    1, 0, 0
    libinput Scroll Method Enabled Default (324):    1, 0, 0
    libinput Click Methods Available (325):    1, 1
    libinput Click Method Enabled (326):    0, 1
    libinput Click Method Enabled Default (327):    1, 0
    libinput Middle Emulation Enabled (328):    0
    libinput Middle Emulation Enabled Default (329):    0
    libinput Accel Speed (330):    0.000000
    libinput Accel Speed Default (331):    0.000000
    libinput Left Handed Enabled (332):    0
    libinput Left Handed Enabled Default (333):    0
    libinput Send Events Modes Available (291):    1, 1
    libinput Send Events Mode Enabled (292):    0, 0
    libinput Send Events Mode Enabled Default (293):    0, 0
    Device Node (294):    "/dev/input/event4"
    Device Product ID (295):    2, 7
    libinput Drag Lock Buttons (334):    <no items>
    libinput Horizontal Scroll Enabled (335):    1


```

any help is much appreciated.

---

### Post by mörgæs on 2020-03-06
Hi, welcome to the fora.

18.04 should not be installed at this day and age. Several better alternatives exist.

First, how does the touchpad work in a live boot of the [daily build]("http://cdimage.ubuntu.com/daily-live/current/")?

---

