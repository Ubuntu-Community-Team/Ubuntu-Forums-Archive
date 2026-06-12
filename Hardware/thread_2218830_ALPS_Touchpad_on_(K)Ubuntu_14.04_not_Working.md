---
title: "ALPS Touchpad on (K)Ubuntu 14.04 not Working"
date: 2014-04-22
forum: Hardware
---

### Post by Odak on 2014-04-22
Hi all,
on my Sony Vaio (model VPCEH2C5E) I've got an ALPS Touchpad that doesn't work. 
xinput output:
```
xinput -list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                           id=13   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                  id=11   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad          id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                            id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer           id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
```

I'm using Kubuntu 14.04 with the latest kernel.

Thanks for help!

---

### Post by Odak on 2014-04-26
Hi,
some logs:
```

Xorg.log
[    20.618] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event12)
[    20.618] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    20.618] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    20.618] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    20.618] (**) DualPoint Stick: always reports core events
[    20.618] (**) evdev: DualPoint Stick: Device: "/dev/input/event12"
[    20.618] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    20.618] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    20.618] (--) evdev: DualPoint Stick: Found relative axes
[    20.618] (--) evdev: DualPoint Stick: Found x and y relative axes
[    20.618] (II) evdev: DualPoint Stick: Configuring as mouse
[    20.618] (**) Option "Emulate3Buttons" "true"
[    20.618] (**) Option "EmulateWheel" "true"
[    20.618] (**) Option "EmulateWheelButton" "2"
[    20.618] (**) Option "YAxisMapping" "4 5"
[    20.618] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    20.618] (**) Option "XAxisMapping" "6 7"
[    20.618] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    20.618] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.618] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event12"
[    20.618] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 13)
[    20.618] (II) evdev: DualPoint Stick: initialized for relative axes.
[    20.618] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    20.618] (**) DualPoint Stick: (accel) acceleration profile 0
[    20.618] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    20.618] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    20.618] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
[    20.618] (**) DualPoint Stick: Ignoring device from InputClass "touchpad ignore duplicates"
[    20.618] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event13)
[    20.618] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.618] (II) Using input driver 'evdev' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    20.618] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    20.618] (**) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Device: "/dev/input/event13"
[    20.618] (II) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Using mtdev for this device
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Found 3 mouse buttons
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Found absolute axes
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Found absolute multitouch axes
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Found x and y absolute axes
[    20.619] (--) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Found absolute touchpad.
[    20.619] (II) evdev: AlpsPS/2 ALPS DualPoint TouchPad: Configuring as touchpad
[    20.619] (**) evdev: AlpsPS/2 ALPS DualPoint TouchPad: YAxisMapping: buttons 4 and 5
[    20.619] (**) evdev: AlpsPS/2 ALPS DualPoint TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.619] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event13"
[    20.619] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 14)
[    20.619] (II) evdev: AlpsPS/2 ALPS DualPoint TouchPad: initialized for absolute axes.
[    20.619] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    20.619] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
[    20.619] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    20.619] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    20.619] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
[    20.619] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
```

xinput list-props
```
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
        Device Enabled (142):   1
        Coordinate Transformation Matrix (144): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (271):     0
        Device Accel Constant Deceleration (272):       1.000000
        Device Accel Adaptive Deceleration (273):       1.000000
        Device Accel Velocity Scaling (274):    10.000000
        Device Product ID (260):        2, 8
        Device Node (261):      "/dev/input/event13"
        Evdev Axis Inversion (275):     0, 0
        Evdev Axis Calibration (276):   <no items>
        Evdev Axes Swap (277):  0
        Axis Labels (278):      "Abs MT Position X" (295), "Abs MT Position Y" (296), "Abs Pressure" (294), "None" (0), "None" (0)
        Button Labels (279):    "Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149)
        Evdev Middle Button Emulation (280):    0
        Evdev Middle Button Timeout (281):      50
        Evdev Third Button Emulation (282):     0
        Evdev Third Button Emulation Timeout (283):     1000
        Evdev Third Button Emulation Button (284):      3
        Evdev Third Button Emulation Threshold (285):   20
        Evdev Wheel Emulation (286):    0
        Evdev Wheel Emulation Axes (287):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (288):    10
        Evdev Wheel Emulation Timeout (289):    200
        Evdev Wheel Emulation Button (290):     4
        Evdev Drag Lock Buttons (291):  0

```
Strange thing: my laptop doesn't have a Stick.
Thanks again

---

