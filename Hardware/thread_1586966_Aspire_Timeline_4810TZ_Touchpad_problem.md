---
title: "Aspire Timeline 4810TZ Touchpad problem"
date: 2010-10-02
forum: Hardware
---

### Post by chanchicto on 2010-10-02
Hi,
The Synaptics Touchpad from my laptop suddenly stopped working in an strange way. Can anybody help? Thanks.

Here is what I've tried:
-Aspire 4810T
Ubuntu 10.04.1
uname -r --> 2.6.32-21-generic

-The Touchpad works perfectly in the splash screen. 
-When I start session, it stops working.
-The Touchpad tab appears in System>Preferences>Mouse
-None of the workarounds in [https://help.ubuntu.com/community/AspireTimeline/Fixes#Touchpad%20On/Off%20button](https://help.ubuntu.com/community/AspireTimeline/Fixes#Touchpad%20On/Off%20button) works.

-**cat /proc/bus/input/devices** shows:
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=1f
B: KEY=837fff 2c3027 bf004444 0 0 1 f84 8a27c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10

I: Bus=0003 Vendor=04f2 Product=b160 Version=1659
N: Name="CNF9113"
P: Phys=usb-0000:00:1d.7-5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0001 Vendor=10ec Product=0269 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=40001
B: SND=6

-**sudo evtest /dev/input/event9** looks like it recognizes the Touchpad (there is output when touching it)

-**xinput list** shows:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; CNF9113                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

-**xinput list-props 13** shows:
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (129):    0
    Device Accel Profile (252):    0
    Device Accel Constant Deceleration (253):    1.000000
    Device Accel Adaptive Deceleration (255):    1.000000
    Device Accel Velocity Scaling (256):    10.000000
    Synaptics Edges (272):    1752, 5192, 1620, 4236
    Synaptics Finger (273):    24, 29, 255
    Synaptics Tap Time (274):    180
    Synaptics Tap Move (275):    221
    Synaptics Tap Durations (276):    180, 180, 100
    Synaptics Tap FastTap (277):    0
    Synaptics Middle Button Timeout (278):    75
    Synaptics Two-Finger Pressure (279):    280
    Synaptics Two-Finger Width (280):    7
    Synaptics Scrolling Distance (281):    100, 100
    Synaptics Edge Scrolling (282):    1, 0, 0
    Synaptics Two-Finger Scrolling (283):    0, 0
    Synaptics Move Speed (284):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (285):    29, 159
    Synaptics Edge Motion Speed (286):    1, 401
    Synaptics Edge Motion Always (287):    0
    Synaptics Button Scrolling (288):    1, 1
    Synaptics Button Scrolling Repeat (289):    1, 1
    Synaptics Button Scrolling Time (290):    100
    Synaptics Off (291):    0
    Synaptics Guestmouse Off (292):    0
    Synaptics Locked Drags (293):    0
    Synaptics Locked Drags Timeout (294):    5000
    Synaptics Tap Action (295):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (296):    1, 1, 1
    Synaptics Circular Scrolling (297):    0
    Synaptics Circular Scrolling Distance (298):    0.100000
    Synaptics Circular Scrolling Trigger (299):    0
    Synaptics Circular Pad (300):    0
    Synaptics Palm Detection (301):    0
    Synaptics Palm Dimensions (302):    10, 199
    Synaptics Coasting Speed (303):    0.000000
    Synaptics Pressure Motion (304):    29, 159
    Synaptics Pressure Motion Factor (305):    1.000000, 1.000000
    Synaptics Grab Event Device (306):    1
    Synaptics Gestures (307):    1
    Synaptics Capabilities (308):    1, 1, 1, 0, 0
    Synaptics Pad Resolution (309):    100, 64
    Synaptics Area (310):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (311):    0

-**xinput --set-prop 13  "Device Enabled" 1** doesn't do anything.

---

### Post by miegiel on 2010-10-02
> **chanchicto said:**
> Hi,
The Synaptics Touchpad from my laptop suddenly stopped working in an strange way. Can anybody help? Thanks.

Here is what I've tried:

*... snip ...*

-**xinput --set-prop 13  "Device Enabled" 1** doesn't do anything.

try:
```
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
```

---

### Post by chanchicto on 2010-10-02
Nothing :/

---

### Post by lidex on 2010-10-02
When was the last time you updated your system? I believe lucid kernel is up to 2.6.32.25
You may find this helpful:
[http://www.linlap.com/wiki/acer+aspire+timeline+4810t](http://www.linlap.com/wiki/acer+aspire+timeline+4810t)

---

### Post by chanchicto on 2010-10-02
Yes, my kernel is not the last updated one. I compiled ALSA for that old kernel, so I prefer to wait to see if somebody finds a fix before updating and recompiling ALSA (that probably will work). Notice that the Touchpad worked perfectly with the old kernel.

---

### Post by lidex on 2010-10-03
> **chanchicto said:**
> Yes, my kernel is not the last updated one. I compiled ALSA for that old kernel, so I prefer to wait to see if somebody finds a fix before updating and recompiling ALSA (that probably will work). Notice that the Touchpad worked perfectly with the old kernel.

You lost me.
Did you read the linked page?

---

### Post by chanchicto on 2010-10-03
:( I'm sorry if I didn't express myself very well. Let me try again:
-The kernel of my laptop is not the last update.
-If I updated it, I'd have to compile again ALSA.
-That would probably solve the issue (I hope so), but I prefer not to do all that tedious process. Also it would be nice to know why the !@#$% the mouse stopped working suddenly.

 Yes, I took a look on the linked page, and I didn't find anything useful. :(

---

### Post by chanchicto on 2010-10-03
Something in my user account was ruined (in the splash screen it responded). I created a new account and the Touchpad was working again. Weird...

---

