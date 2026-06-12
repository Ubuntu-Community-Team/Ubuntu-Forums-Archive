---
title: "ETPS/2 Elantech Touchpad recognized and enabled but not working 14.04"
date: 2015-04-01
forum: Hardware
---

### Post by tommasosebastianelli on 2015-04-01
Hi everyone,
i'm posting this after looking for similar issues and trying lots of possible solution without luck.

I've installed Elementary OS Freya beta 2 (14.04 LTS) and my touchpad is completely ko, even if is recognized and marked as "enabled".
It's pretty strange because with the previous OS version (OS Luna - Ubuntu 12.04 based) touchpad worked out of the box!
edit: My laptop is an ASUS f550ze-xx072h.

My xinput:
```
Device 'ETPS/2 Elantech Touchpad':    Device Enabled (145):    1
    Coordinate Transformation Matrix (147):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (274):    1
    Device Accel Constant Deceleration (275):    2.500000
    Device Accel Adaptive Deceleration (276):    1.000000
    Device Accel Velocity Scaling (277):    12.500000
    Synaptics Edges (299):    123, 2974, 114, 2005
    Synaptics Finger (300):    1, 1, 0
    Synaptics Tap Time (301):    180
    Synaptics Tap Move (302):    165
    Synaptics Tap Durations (303):    180, 180, 100
    Synaptics ClickPad (304):    1
    Synaptics Middle Button Timeout (305):    0
    Synaptics Two-Finger Pressure (306):    282
    Synaptics Two-Finger Width (307):    7
    Synaptics Scrolling Distance (308):    -75, -75
    Synaptics Edge Scrolling (309):    0, 0, 0
    Synaptics Two-Finger Scrolling (310):    1, 1
    Synaptics Move Speed (311):    1.000000, 1.750000, 0.053305, 0.000000
    Synaptics Off (312):    0
    Synaptics Locked Drags (313):    0
    Synaptics Locked Drags Timeout (314):    5000
    Synaptics Tap Action (315):    0, 0, 0, 0, 0, 0, 0
    Synaptics Click Action (316):    1, 3, 0
    Synaptics Circular Scrolling (317):    0
    Synaptics Circular Scrolling Distance (318):    0.100000
    Synaptics Circular Scrolling Trigger (319):    0
    Synaptics Circular Pad (320):    0
    Synaptics Palm Detection (321):    0
    Synaptics Palm Dimensions (322):    10, 200
    Synaptics Coasting Speed (323):    20.000000, 50.000000
    Synaptics Pressure Motion (324):    30, 160
    Synaptics Pressure Motion Factor (325):    1.000000, 1.000000
    Synaptics Resolution Detect (326):    1
    Synaptics Grab Event Device (327):    1
    Synaptics Gestures (328):    1
    Synaptics Capabilities (329):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (330):    32, 31
    Synaptics Area (331):    0, 0, 0, 0
    Synaptics Soft Button Areas (332):    1548, 0, 1737, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (333):    18, 18
    Device Product ID (265):    2, 14
    Device Node (266):    "/dev/input/event7"

```

also, my [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/bus/input/devices output:[/FONT][/COLOR]
```
tommaso@tommaso-laptop:~/Downloads$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0003 Vendor=1532 Product=001c Version=0111
N: Name="Razer  Razer Abyssus"
P: Phys=usb-0000:00:12.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input14
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=0
B: EV=17
B: KEY=7f0000 0 0 0 0
B: REL=103
B: MSC=10


I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input13
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.1/sound/card0/input15
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:14.2/sound/card1/input17
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HD-Audio Generic Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:14.2/sound/card1/input16
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0003 Vendor=0bda Product=57b4 Version=0013
N: Name="USB Camera"
P: Phys=usb-0000:00:13.2-4/button
S: Sysfs=/devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0/input/input18
U: Uniq=
H: Handlers=kbd event11 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input19
U: Uniq=
H: Handlers=rfkill kbd event12 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10


tommaso@tommaso-laptop:~/Downloads$ I: Bus=0019 Vendor=0000 Product=0001 Version=0000

```

What i tried with no result:
```
xinput float "ETPS/2 Elantech Touchpad"
xinput reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"

```

i also tried reloading the drivers:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rv psmouse[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v psmouse[/FONT][/COLOR]
```


Could someone help me please?

---

### Post by aljosa2 on 2015-04-01
hello,
if i try the following command as root

> echo 1 > /sys/devices/platform/i8042/serio4/reg_07

then everything becomes perfect with elantech touchpad.

if that helps to you too, then take a look here:

[https://bugzilla.kernel.org/show_bug.cgi?id=94981](https://bugzilla.kernel.org/show_bug.cgi?id=94981)

[http://www.spinics.net/lists/linux-input/msg37678.html](http://www.spinics.net/lists/linux-input/msg37678.html)

---

### Post by tommasosebastianelli on 2015-04-01
That worked unbelievably well, thank you so much! I also red the first link but i'm not a power-user, so i didn't understand much!
It seems it's an asus problem since my laptop is an ASUS as well (F550ze-xx072h).

---

### Post by aljosa2 on 2015-04-02
great :)
please comment (with your laptop's specification) a bug that i've reported to kernel developers:

[https://bugzilla.kernel.org/show_bug.cgi?id=94981](https://bugzilla.kernel.org/show_bug.cgi?id=94981)

---

### Post by tommasosebastianelli on 2015-04-02
ok, i'll report that.
Could some admin put the "solved" tag on the thread title?

---

### Post by slickymaster on 2015-04-02
> **tommasosebastianelli said:**
> ok, i'll report that.
Could some admin put the "solved" tag on the thread title?
You can/must do it yourself. Just follow the link in my sig on how to do it.

---

