---
title: "Installing Ubuntu on New Dell XPS 13 (9300)"
date: 2020-04-28
forum: Hardware
---

### Post by makem2 on 2020-04-28
I have just purchased this machine and am checking to see what does not work out of the box.

I am using a live xubuntu 18.04 to do this.

So far I am having the following issues:

1. Mouse control.

a) Using the touch pad the pointer will keep stopping and starting
b) Sometimes it will split into two or more pointers and then join up again
c) It will hang in one place for long periods if left unused.
d) The pointer moves around the screen without a problem until it is used to select something when it will stop, hesitate, maybe split and then go on

This also noted when using a Bluetooth mouse.

2. Text input (Entering a password etc) will cause a lag between keypresses. You need to check if the entry has been made and wait a little to see it appear.

3. The screen will go black occasionally. (Not screensaver)

4. A line appears across the screen below the pointer position

5. Screen 'jittering' in a narrow band across the top of the screen occasionally

From Mouse and touch pad config:

Device: DLL096D:01 06CB-CDE6 TouchPad with alternative SynPS/2 Synaptics TouchPad

Wifi and sound work. Keyboard lights work.

I have updated xubuntu. I will try to get more info and add it.

Can I get any suggestions with any of the above while using a live usb or must I install xubuntu? I try to avoid this as I have 14 days to ask for a refund.

Edit:

```

xubuntu@xubuntu:~$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:8a52] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:096d]
    Flags: bus master, fast devsel, latency 0, IRQ 144
    Memory at 603c000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 4000000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:8a03] (rev 03)
    Subsystem: Dell Device [1028:096d]
xubuntu@xubuntu:~$ 

```

```

xubuntu@xubuntu:~$ xinput list-props 11
Device 'DLL096D:01 06CB:CDE6 Touchpad':
    Device Enabled (146):    1
    Coordinate Transformation Matrix (148):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (274):    1
    Device Accel Constant Deceleration (275):    2.500000
    Device Accel Adaptive Deceleration (276):    1.000000
    Device Accel Velocity Scaling (277):    12.500000
    Synaptics Edges (278):    51, 1248, 38, 684
    Synaptics Finger (279):    25, 30, 0
    Synaptics Tap Time (280):    180
    Synaptics Tap Move (281):    65
    Synaptics Tap Durations (282):    180, 180, 100
    Synaptics ClickPad (283):    1
    Synaptics Middle Button Timeout (284):    0
    Synaptics Two-Finger Pressure (285):    282
    Synaptics Two-Finger Width (286):    7
    Synaptics Scrolling Distance (287):    29, 29
    Synaptics Edge Scrolling (288):    1, 0, 0
    Synaptics Two-Finger Scrolling (289):    1, 0
    Synaptics Move Speed (290):    1.000000, 1.750000, 0.134590, 0.000000
    Synaptics Off (291):    0
    Synaptics Locked Drags (292):    0
    Synaptics Locked Drags Timeout (293):    5000
    Synaptics Tap Action (294):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (295):    1, 3, 0
    Synaptics Circular Scrolling (296):    0
    Synaptics Circular Scrolling Distance (297):    0.100000
    Synaptics Circular Scrolling Trigger (298):    0
    Synaptics Circular Pad (299):    0
    Synaptics Palm Detection (300):    0
    Synaptics Palm Dimensions (301):    10, 200
    Synaptics Coasting Speed (302):    20.000000, 50.000000
    Synaptics Pressure Motion (303):    30, 160
    Synaptics Pressure Motion Factor (304):    1.000000, 1.000000
    Synaptics Resolution Detect (305):    1
    Synaptics Grab Event Device (306):    0
    Synaptics Gestures (307):    1
    Synaptics Capabilities (308):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (309):    12, 12
    Synaptics Area (310):    0, 0, 0, 0
    Synaptics Soft Button Areas (311):    649, 0, 592, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (312):    7, 7
    Device Product ID (270):    1739, 52710
    Device Node (269):    "/dev/input/event10"
[COLOR=#4CE64C]**xubuntu@xubuntu**[/COLOR]:[COLOR=#295FCC]**~**[/COLOR]$

```

---

### Post by makem2 on 2020-04-28
All the problems so far were fixed when testing Xubuntu 20.04. It's only been a few hours but the latest OS seems to be the bees knees. A nice little machine, if a trifle heavy for it's size when compared withe the Asus Zenbook I was tempted to buy. It had an unusual touchpad and I fancied it. But I feel sure I would have trouble with Linux this early.

Whilst waiting for the machine to arrive I googled the OS and it was suggested that the latest version had Wi-Fi problems. It was recommended that an earlier LTS version was used, hence I tried 18.04.

I will mark solved.

---

