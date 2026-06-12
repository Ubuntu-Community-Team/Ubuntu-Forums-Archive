---
title: "dell 5537 touchpad malfunction Ubuntu 14.4"
date: 2014-06-13
forum: Hardware
---

### Post by Picek on 2014-06-13
Hi all!

I have just installed Ubuntu 12.04 on my new Dell Inspiron 5537, but due to hybrid graphics issues I decided to upgrade to 14.04.  Aftef that graphics run smoothly, but I have encountered problem with touchpad, namely it does not work. It is worth mentioning that after first succesfull booting to desktop there was a "serious system error" message, which I did not investigate.  Touchpad seems to be detected, as output of 
```
cat /proc/bus/input/devices
``` 
contains
```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: PROP=1
B: EV=b
B: KEY=e520 30000 0 0 0 0
B: ABS=660800011000003

```
also outcome of ```
xinput
``` looks normal:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Multi-Smart Mouse                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]


```

in case it helps I also add output from ```
xinput --watch-props 12
```

```
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (263):    0
    Device Accel Constant Deceleration (264):    1.000000
    Device Accel Adaptive Deceleration (265):    1.000000
    Device Accel Velocity Scaling (266):    10.000000
    Device Product ID (253):    2, 7
    Device Node (254):    "/dev/input/event5"
    Evdev Axis Inversion (267):    0, 0
    Evdev Axis Calibration (268):    <no items>
    Evdev Axes Swap (269):    0
    Axis Labels (270):    "Abs MT Position X" (288), "Abs MT Position Y" (289), "Abs MT Pressure" (290), "Abs Tool Width" (287), "None" (0), "None" (0), "None" (0)
    Button Labels (271):    "Button Left" (137), "Button Unknown" (256), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141)
    Evdev Middle Button Emulation (272):    0
    Evdev Middle Button Timeout (273):    50
    Evdev Third Button Emulation (274):    0
    Evdev Third Button Emulation Timeout (275):    1000
    Evdev Third Button Emulation Button (276):    3
    Evdev Third Button Emulation Threshold (277):    20
    Evdev Wheel Emulation (278):    0
    Evdev Wheel Emulation Axes (279):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (280):    10
    Evdev Wheel Emulation Timeout (281):    200
    Evdev Wheel Emulation Button (282):    4
    Evdev Drag Lock Buttons (283):    0

```

Also, in graphical mode in "Settings > mouse and touchpad " window there are no options like "enable touchpad" nor aything like that. Only sensitivity.

I would also like to attach dmesg output but it exceeds size limit for attachments.

I`ll be very gratefull for any help.

---

### Post by Picek on 2014-06-14
Found a solution myself. The reason was that psmouse wasn`t loading properly. this worked: [http://askubuntu.com/a/262364/293492](http://askubuntu.com/a/262364/293492) (still, if anyone can tell me what does this argument do I would appriciate).
Then I found it usefull to install two additional packages that were absent:

```
aptitude install xserver-xorg-input-synaptics gpointing-device-settings
```
now I am able to use touchpad and configure it via graphical tools

---

