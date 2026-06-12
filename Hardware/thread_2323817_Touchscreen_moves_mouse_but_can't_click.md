---
title: "Touchscreen moves mouse but can't click"
date: 2016-05-08
forum: Hardware
---

### Post by phoen1x on 2016-05-08
After installing Ubuntu 16.04 on my Lenovo IdeaCentre C560 I'm able to move the mouse cursor on my touchscreen, but the left mouse button doesn't click on anything. The Xorg.0.log shows "TouchScreen: No buttons found, faking one."

I even tried installing Ubuntu 14.04. with X11 1.16.0 which is supported by the manufacturer driver [http://www.irtouchusa.com/download.htm](http://www.irtouchusa.com/download.htm) but without success.

Has somebody an idea on how to solve this?

```

# cat /var/log/Xorg.0.log
...
[    18.653] (II) Using input driver 'evdev' for 'Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen'
[    18.708] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Vendor 0x6615 Product 0x8702
...
[    29.136] (II) config/udev: Adding input device Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen (/dev/input/event14)
[    29.136] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Applying InputClass "evdev touchscreen catchall"
[    29.136] (II) Using input driver 'evdev' for 'Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen'
[    29.136] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: always reports core events
[    29.136] (**) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Device: "/dev/input/event14"
[    29.192] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Vendor 0x6615 Product 0x8702
[    29.192] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Found absolute axes
[    29.192] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Found absolute multitouch axes
[    29.192] (II) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: No buttons found, faking one.
[    29.192] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Found x and y absolute axes
[    29.192] (--) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Found absolute touchscreen
[    29.192] (II) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: Configuring as touchscreen
[    29.192] (**) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: YAxisMapping: buttons 4 and 5
[    29.192] (**) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.192] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:6615:8702.0005/input/input14/event14"
[    29.192] (II) XINPUT: Adding extended input device "Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen" (type: TOUCHSCREEN, id 15)
[    29.192] (II) evdev: Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: initialized for absolute axes.
[    29.192] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: (accel) keeping acceleration scheme 1
[    29.192] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: (accel) acceleration profile 0
[    29.192] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: (accel) acceleration factor: 2.000
[    29.192] (**) Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen: (accel) acceleration threshold: 4
[    29.192] (II) config/udev: Adding input device Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen (/dev/input/mouse1)
[    29.192] (II) No input driver specified, ignoring this device.
[    29.192] (II) This device may have been added with another device file.

```

```
# evtest
/dev/input/event14:    Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen
Select the device event number [0-15]: 14
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x6615 product 0x8702 version 0x110
Input device name: "Beijing IRTOUCHSYSTEMS Co.,LtD USB TouchScreen"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 330 (BTN_TOUCH)
  Event type 3 (EV_ABS)
    Event code 0 (ABS_X)
      Value  17206
      Min        0
      Max    32767
      Resolution      64
    Event code 1 (ABS_Y)
      Value  17489
      Min        0
      Max    32767
      Resolution     115
    Event code 47 (ABS_MT_SLOT)
      Value      0
      Min        0
      Max        4
    Event code 48 (ABS_MT_TOUCH_MAJOR)
      Value      0
      Min        0
      Max    32767
      Resolution     115
    Event code 49 (ABS_MT_TOUCH_MINOR)
      Value      0
      Min        0
      Max    32767
      Resolution     115
    Event code 52 (ABS_MT_ORIENTATION)
      Value      0
      Min        0
      Max        1
    Event code 53 (ABS_MT_POSITION_X)
      Value      0
      Min        0
      Max    32767
      Resolution      64
    Event code 54 (ABS_MT_POSITION_Y)
      Value      0
      Min        0
      Max    32767
      Resolution     115
    Event code 57 (ABS_MT_TRACKING_ID)
      Value      0
      Min        0
      Max    65535
Properties:
  Property type 1 (INPUT_PROP_DIRECT)
Testing ... (interrupt to exit)

```

---

