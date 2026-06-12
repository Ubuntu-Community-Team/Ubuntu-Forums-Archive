---
title: "Touchpad recognized as mouse"
date: 2012-07-29
forum: Hardware
---

### Post by mathiaho on 2012-07-29
Hi

I have Ubuntu 12.04 installed on my Toshiba Satellite L650D-15G.
On earlier installs, my touchpad has worked perfectly, and sometimes it does so even now.

It seems as if ubuntu thinks my touchpad is a normal mouse. This affects me in two ways:
-Scrolling whith the right edge of touchpad doesn't work
-Pressing both physical mouse-buttons should produce middle-click, but doesn't

typing "synclient" in terminal gives me:
> Couldn't find synaptics properties. No synaptics driver loaded?

This is from /var/log/Xorg.0.log

> [    35.510] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/event8)
[    35.510] (**) PS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
[    35.510] (II) Using input driver 'evdev' for 'PS/2 Synaptics TouchPad'
[    35.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.510] (**) PS/2 Synaptics TouchPad: always reports core events
[    35.510] (**) evdev: PS/2 Synaptics TouchPad: Device: "/dev/input/event8"
[    35.511] (--) evdev: PS/2 Synaptics TouchPad: Vendor 0x2 Product 0x1
[    35.511] (--) evdev: PS/2 Synaptics TouchPad: Found 3 mouse buttons
[    35.511] (--) evdev: PS/2 Synaptics TouchPad: Found relative axes
[    35.511] (--) evdev: PS/2 Synaptics TouchPad: Found x and y relative axes
[    35.511] (II) evdev: PS/2 Synaptics TouchPad: Configuring as mouse
[    35.511] (**) evdev: PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    35.511] (**) evdev: PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.511] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    35.511] (II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE, id 11)
[    35.511] (II) evdev: PS/2 Synaptics TouchPad: initialized for relative axes.
[    35.511] (**) PS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    35.511] (**) PS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    35.511] (**) PS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    35.511] (**) PS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    35.511] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/mouse0)
[    35.511] (II) No input driver specified, ignoring this device.
[    35.511] (II) This device may have been added with another device file.

Please help :confused:

---

### Post by mathiaho on 2012-07-29
Update!

as I said:
> On earlier installs, my touchpad has worked perfectly, and sometimes it does so even now.

That "sometimes" is when I boot the lowlatency kernel, which is 3.2.0-23. I guess a kernel update has broken something...

What should I do? File a bug report?

---

