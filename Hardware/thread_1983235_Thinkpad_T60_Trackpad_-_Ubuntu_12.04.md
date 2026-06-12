---
title: "Thinkpad T60 Trackpad - Ubuntu 12.04"
date: 2012-05-19
forum: Hardware
---

### Post by lsheaves on 2012-05-19
hi All,

I have been having some problems in getting 12.04 working properly on my Lenovo T60 (8741-8BM)

The problem I am seeing is that the Pointer on the keyboard (ie Red thingy) and it's associated buttons below the space bar work 100%, however I seem to be unable to get the touch pad to be recognised AT ALL.  I would appear that the system IS recognising that the pad is there, but the Mouse control panel does not show a TAB at the top to allow me to configure the touchpad.

Any assistance would be MUCH appreciated.   FYI,  I have tried installing the following packages: SYNAPTIKS.  

Some system info:
lukes@LukePC:~$ xinput list-props "TPPS/2 IBM TrackPoint"
Device 'TPPS/2 IBM TrackPoint':
    Device Enabled (137):    1
    Coordinate Transformation Matrix (139):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    0
    Device Accel Constant Deceleration (259):    1.000000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    10.000000
    Device Product ID (254):    2, 10
    Device Node (255):    "/dev/input/event6"
    Evdev Axis Inversion (262):    0, 0
    Evdev Axes Swap (264):    0
    Axis Labels (265):    "Rel X" (147), "Rel Y" (148)
    Button Labels (266):    "Button Left" (140), "Button Middle" (141), "Button Right" (142), "Button Wheel Up" (143), "Button Wheel Down" (144), "Button Horiz Wheel Left" (145), "Button Horiz Wheel Right" (146)
    Evdev Middle Button Emulation (267):    0
    Evdev Middle Button Timeout (268):    50
    Evdev Third Button Emulation (269):    0
    Evdev Third Button Emulation Timeout (270):    1000
    Evdev Third Button Emulation Button (271):    3
    Evdev Third Button Emulation Threshold (272):    20
    Evdev Wheel Emulation (273):    1
    Evdev Wheel Emulation Axes (274):    6, 7, 4, 5
    Evdev Wheel Emulation Inertia (275):    10
    Evdev Wheel Emulation Timeout (276):    200
    Evdev Wheel Emulation Button (277):    2
    Evdev Drag Lock Buttons (278):    0

lukes@LukePC:~$ dmesg | grep IBM
[    1.366527] pnp 00:09: Plug and Play ACPI device, IDs IBM3780 PNP0f13 (active)
[    1.367261] pnp 00:0a: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
[   13.407544] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   13.922369] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.938766] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input6

---

### Post by lsheaves on 2012-05-19
1 Additional think of note from the X11 logs:

[    14.681] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    14.681] (**) TPPS/2 IBM TrackPoint: Applying InputClass "TPPS/2 IBM TrackPoint"
[    14.681] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    14.681] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    14.681] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    14.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.681] (**) TPPS/2 IBM TrackPoint: always reports core events
[    14.681] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    14.682] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    14.682] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    14.682] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    14.682] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    14.682] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    14.682] (**) Option "Emulate3Buttons" "true"
[    14.682] (**) Option "EmulateWheel" "true"
[    14.682] (**) Option "EmulateWheelButton" "2"
[    14.682] (**) Option "YAxisMapping" "4 5"
[    14.682] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    14.682] (**) Option "XAxisMapping" "6 7"
[    14.682] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    14.682] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTime
out: 200
[    14.682] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    14.682] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 10)
[    14.682] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    14.682] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    14.682] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    14.682] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    14.682] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    14.682] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[    14.682] (**) TPPS/2 IBM TrackPoint: Applying InputClass "TPPS/2 IBM TrackPoint"
[    14.682] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    14.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.682] (**) TPPS/2 IBM TrackPoint: always reports core events
[    14.682] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/mouse0"
[    14.683] (EE) TPPS/2 IBM TrackPoint: Couldn't open mtdev device
[    14.683] (EE) evdev: TPPS/2 IBM TrackPoint: ioctl EVIOCGID failed: Inappropriate ioctl for device
[    14.712] (EE) PreInit returned 8 for "TPPS/2 IBM TrackPoint"

---

### Post by 2F4U on 2012-05-20
Do the basic functions work on the touchpad? If yes, you could try a manual configuration:

[http://www.thinkwiki.org/wiki/Synaptics_TouchPad_driver_for_X](http://www.thinkwiki.org/wiki/Synaptics_TouchPad_driver_for_X)

---

### Post by lsheaves on 2012-05-20
Sadly, nothing on the touchpad works at all

---

### Post by 2F4U on 2012-05-20
If nothing (not even usual movement?) works at all, could it be a hardware defect? I own a T60 myself and on any Linux distribution I tried at least the basic functionality worked out of the box.
One other thought: did you disable the touchpad in the BIOS? On a T60, you can enable/disable trackpoint and touchpad separately in the BIOS.

---

### Post by steeldriver on 2012-05-20
it looks to me like it is using the basic evdev driver - I'm confused about exactly what package you tried to install? try

xserver-xorg-input-synaptics

---

