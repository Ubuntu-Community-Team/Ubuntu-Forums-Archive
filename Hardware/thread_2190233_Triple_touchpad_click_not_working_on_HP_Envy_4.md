---
title: "Triple touchpad click not working on HP Envy 4"
date: 2013-11-26
forum: Hardware
---

### Post by goldstein2034 on 2013-11-26
Hello everyone. 

I have been trying to make the triple touchpad click work (Ubuntu 12.04 on HP Envy 4), but it seems impossible... I paste all info I think could be helpful (sorry for the flooding...):

>> xinput --list-props 12
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (308):    1
    Device Accel Constant Deceleration (309):    2.500000
    Device Accel Adaptive Deceleration (310):    1.000000
    Device Accel Velocity Scaling (311):    12.500000
    Synaptics Edges (312):    1766, 5392, 1641, 4515
    Synaptics Finger (313):    25, 30, 256
    Synaptics Tap Time (314):    180
    Synaptics Tap Move (315):    236
    Synaptics Tap Durations (316):    180, 180, 100
    Synaptics ClickPad (317):    1
    Synaptics Tap FastTap (318):    0
    Synaptics Middle Button Timeout (319):    0
    Synaptics Two-Finger Pressure (320):    282
    Synaptics Two-Finger Width (321):    7
    Synaptics Scrolling Distance (322):    107, 107
    Synaptics Edge Scrolling (323):    0, 0, 0
    Synaptics Two-Finger Scrolling (324):    1, 1
    Synaptics Move Speed (325):    1.000000, 1.750000, 0.037195, 40.000000
    Synaptics Edge Motion Pressure (326):    30, 160
    Synaptics Edge Motion Speed (327):    1, 430
    Synaptics Edge Motion Always (328):    0
    Synaptics Off (329):    2
    Synaptics Locked Drags (330):    0
    Synaptics Locked Drags Timeout (331):    5000
    Synaptics Tap Action (332):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (333):    1, 3, 0
    Synaptics Circular Scrolling (334):    0
    Synaptics Circular Scrolling Distance (335):    0.100000
    Synaptics Circular Scrolling Trigger (336):    0
    Synaptics Circular Pad (337):    0
    Synaptics Palm Detection (338):    0
    Synaptics Palm Dimensions (339):    10, 200
    Synaptics Coasting Speed (340):    20.000000, 50.000000
    Synaptics Pressure Motion (341):        ... of unknown type CARDINAL

    Synaptics Pressure Motion Factor (342):    1.000000, 1.000000
    Synaptics Resolution Detect (343):    1
    Synaptics Grab Event Device (344):    1
    Synaptics Gestures (345):    1
    Synaptics Capabilities (346):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (347):    66, 47
    Synaptics Area (348):    0, 0, 0, 0
    Synaptics Soft Button Areas (349):    0, 0, 0, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (350):    8, 8
    Device Product ID (251):    2, 7
    Device Node (252):    "/dev/input/event11"

 cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=20000 20 0 0 500f02100002 3803078f900d401 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input4
U: Uniq=
H: Handlers=event4 js0 
B: PROP=0
B: EV=9
B: ABS=7

I: Bus=0003 Vendor=1bcf Product=2c0e Version=0314
N: Name="HP Truevision HD"
P: Phys=usb-0000:00:1a.0-1.1/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=33
B: KEY=4000000000 0 1000700000000 2100400 0 0
B: MSC=10
B: SW=22

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse0 event11 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0003 Vendor=046d Product=c00e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input12
U: Uniq=
H: Handlers=mouse1 event12 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10


cat /var/log/Xorg.0.log | grep Syn
[     4.592] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[     4.592] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     4.592] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     4.592] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     4.592] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.728] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5686
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4748
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     4.728] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.728] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.796] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[     4.796] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     4.796] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[     4.796] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[     4.796] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     4.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     4.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     4.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     4.796] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.796] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     4.796] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"



I don't really understand all these outputs... but I read the touchpad debugging and it seems these are important...

Thank you for your help!

---

