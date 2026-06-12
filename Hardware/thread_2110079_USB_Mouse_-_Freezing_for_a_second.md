---
title: "USB Mouse - Freezing for a second"
date: 2013-01-29
forum: Hardware
---

### Post by clivej on 2013-01-29
For this past few weeks, all of a sudden, my mouse will randomly stop working (its like someone has unplugged it for a split second).  If I wait a couple of seconds it will start working again.  

In the last few days I have been using a USB video capture dongle to convert some VHS tapes to DVD.  In the past this has worked fine.  But same thing is happening as the mouse, it keeps disconnecting only the grabber wont come back without a physical restart and its driving me crazy.

The only clue I can see in the logs is this line

```
INFO: task khubd:23 blocked for more than 120 seconds.
```Anyone know whats going on?

I'm using Ubuntu 12.10, 64bit on a Toshiba Satellite P500

-----

XOrg Log
```
[  3920.794] (II) config/udev: removing device Genius 4D Scroll Mouse
[  3920.797] (II) evdev: Genius 4D Scroll Mouse: Close
[  3920.797] (II) UnloadModule: "evdev"
[  3921.754] (II) config/udev: Adding input device Genius 4D Scroll Mouse (/dev/input/mouse0)
[  3921.754] (II) No input driver specified, ignoring this device.
[  3921.754] (II) This device may have been added with another device file.
[  3921.755] (II) config/udev: Adding input device Genius 4D Scroll Mouse (/dev/input/event5)
[  3921.755] (**) Genius 4D Scroll Mouse: Applying InputClass "evdev pointer catchall"
[  3921.755] (**) Genius 4D Scroll Mouse: Applying InputClass "evdev keyboard catchall"
[  3921.755] (II) Using input driver 'evdev' for 'Genius 4D Scroll Mouse'
[  3921.755] (**) Genius 4D Scroll Mouse: always reports core events
[  3921.755] (**) evdev: Genius 4D Scroll Mouse: Device: "/dev/input/event5"
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Vendor 0x458 Product 0x65
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found 3 mouse buttons
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found scroll wheel(s)
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found relative axes
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found x and y relative axes
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found absolute axes
[  3921.755] (II) evdev: Genius 4D Scroll Mouse: Forcing absolute x/y axes to exist.
[  3921.755] (--) evdev: Genius 4D Scroll Mouse: Found keys
[  3921.755] (II) evdev: Genius 4D Scroll Mouse: Configuring as mouse
[  3921.755] (II) evdev: Genius 4D Scroll Mouse: Configuring as keyboard
[  3921.755] (II) evdev: Genius 4D Scroll Mouse: Adding scrollwheel support
[  3921.755] (**) evdev: Genius 4D Scroll Mouse: YAxisMapping: buttons 4 and 5
[  3921.755] (**) evdev: Genius 4D Scroll Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3921.755] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input13/event5"
[  3921.755] (II) XINPUT: Adding extended input device "Genius 4D Scroll Mouse" (type: KEYBOARD, id 9)
[  3921.755] (**) Option "xkb_rules" "evdev"
[  3921.755] (**) Option "xkb_model" "pc105"
[  3921.755] (**) Option "xkb_layout" "gb"
[  3921.756] (II) evdev: Genius 4D Scroll Mouse: initialized for relative axes.
[  3921.756] (WW) evdev: Genius 4D Scroll Mouse: ignoring absolute axes.
[  3921.756] (**) Genius 4D Scroll Mouse: (accel) keeping acceleration scheme 1
[  3921.756] (**) Genius 4D Scroll Mouse: (accel) acceleration profile 0
[  3921.756] (**) Genius 4D Scroll Mouse: (accel) acceleration factor: 2.000
[  3921.756] (**) Genius 4D Scroll Mouse: (accel) acceleration threshold: 4
```

---

