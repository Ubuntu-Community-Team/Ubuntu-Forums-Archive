---
title: "Dell XPS 13 Developer Ed. - Multitouch Touchpad not working while Touchscreen does"
date: 2014-02-16
forum: Hardware
---

### Post by joostw on 2014-02-16
Hello folks,

I took the plunge and invested in the fine Linux only "Developer  Edition" (Haswell) Dell XPS 13 - 9333 and did a clean install of Ubuntu  14.04 (last update today).

The Touchscreen (note: the monitor/display) works without problems. The  crucial "multitouch" test for me is a 3 finger touch which showes resize  and move handles on the touched window. Also 4 finger touches to bring  up the dash work.

The touchpad works with single and two finger taps (bringing up button 3) and two finger scrolling.
But I believe, that at least three finger taps should also work like  they do e.g. on the touchscreen or on another brand/laptop like shown  here:

[http://askubuntu.com/questions/133207/how-can-i-disable-the-multitouch-gestures-in-ubuntu](http://askubuntu.com/questions/133207/how-can-i-disable-the-multitouch-gestures-in-ubuntu)

A general overview of supposedly supported gestures:
[https://wiki.ubuntu.com/Multitouch#Supported_Gestures](https://wiki.ubuntu.com/Multitouch#Supported_Gestures)

Touchegg and GINN btw. do not work anymore due to incompatibilities with Unity.

Some info:

```
root@silver:~# dmesg | grep ynaptic
[    1.781742] usb 2-3: Product: Synaptics Large Touch Screen
[   10.182791] input: SYNAPTICS Synaptics Large Touch Screen as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input10
[   10.183551] hid-multitouch 0003:06CB:0AF8.0001:  input,hiddev0,hidraw0: USB HID v1.11 Mouse [SYNAPTICS Synaptics Large  Touch Screen] on usb-0000:00:14.0-3/input0
[   11.283165] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1,  id: 0x1e2b1, caps: 0xd40123/0x840300/0x126800, board id: 2734, fw id:  1522295
[   11.331691] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6

```

```
root@silver:~# grep ynaptic /var/log/Xorg.0.log
[  1288.042] (II) config/udev: Adding input device SYNAPTICS Synaptics Large Touch Screen (/dev/input/event8)
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: Applying InputClass "evdev touchscreen catchall"
[  1288.042] (II) Using input driver 'evdev' for 'SYNAPTICS Synaptics Large Touch Screen'
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: always reports core events
[  1288.042] (**) evdev: SYNAPTICS Synaptics Large Touch Screen: Device: "/dev/input/event8"
[  1288.042] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: Using mtdev for this device
[  1288.042] (--) evdev: SYNAPTICS Synaptics Large Touch Screen: Vendor 0x6cb Product 0xaf8
[  1288.042] (--) evdev: SYNAPTICS Synaptics Large Touch Screen: Found absolute axes
[  1288.042] (--) evdev: SYNAPTICS Synaptics Large Touch Screen: Found absolute multitouch axes
[  1288.042] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: No buttons found, faking one.
[  1288.042] (--) evdev: SYNAPTICS Synaptics Large Touch Screen: Found x and y absolute axes
[  1288.042] (--) evdev: SYNAPTICS Synaptics Large Touch Screen: Found absolute touchscreen
[  1288.042] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: Configuring as touchscreen
[  1288.042] (**) evdev: SYNAPTICS Synaptics Large Touch Screen: YAxisMapping: buttons 4 and 5
[  1288.042] (**) evdev: SYNAPTICS Synaptics Large Touch Screen:  EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1288.042] (II) XINPUT: Adding extended input device "SYNAPTICS Synaptics Large Touch Screen" (type: TOUCHSCREEN, id 9)
[  1288.042] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: initialized for absolute axes.
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: (accel) keeping acceleration scheme 1
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: (accel) acceleration profile 0
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: (accel) acceleration factor: 2.000
[  1288.042] (**) SYNAPTICS Synaptics Large Touch Screen: (accel) acceleration threshold: 4
[  1288.042] (II) config/udev: Adding input device SYNAPTICS Synaptics Large Touch Screen (/dev/input/mouse0)
[  1288.043] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[  1288.043] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1288.043] (II) LoadModule: "synaptics"
[  1288.043] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1288.044] (II) Module synaptics: vendor="X.Org Foundation"
[  1288.044] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1288.044] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1288.064] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5676 (res 45)
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4722 (res 60)
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1288.064] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1288.076] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[  1288.076] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1288.076] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  1288.076] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[  1288.076] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1288.076] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1288.076] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1288.076] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1288.076] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1288.076] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  1483.620] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: Using mtdev for this device
[  1483.621] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1545.052] (II) evdev: SYNAPTICS Synaptics Large Touch Screen: Using mtdev for this device
[  1545.053] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
root@silver:~#
```

```
root@silver:~# grep "TouchPad: buttons:" /var/log/Xorg.0.log
[  1288.064] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
root@silver:~# 
```

```
Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "SHMconfig" "1"
EndSection

```

Btw. the current (1.7.3) synclient has no -m and -h switch anymore?

Please, does anyone have an idea what might be needed to get this working? I already invested hours in this...
Thanks,

JC

---

### Post by bwana on 2014-12-26
Hi JC,

I just hit this very issue .. did you manage to get anywhere ?

---

