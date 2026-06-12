---
title: "weird elantech touchpad issues on 16.04/4.4.0 kernel"
date: 2016-06-08
forum: Hardware
---

### Post by mattecapu on 2016-06-08
Hi folks,
I'm getting some weird issues after a minor system update (that I don't actually know how affected the system).
On kernel 4.4.0-21, my Elantech Touchpad has stopped functioning after login. I can enable with
```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```
With this I can move the cursor, tap and use the two physical buttons, but two fingers tap/scroll or any other multitouch gesture is gone.
This is from Xorg.0.log
```

 4.079] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[     4.079] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     4.079] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[     4.079] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     4.079] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[     4.079] (II) LoadModule: "synaptics"
[     4.079] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     4.079] (II) Module synaptics: vendor="X.Org Foundation"
[     4.079]     compiled for 1.18.1, module version = 1.8.2
[     4.079]     Module class: X.Org XInput Driver
[     4.079]     ABI class: X.Org XInput driver, version 22.1
[     4.079] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     4.079] (**) ETPS/2 Elantech Touchpad: always reports core events
[     4.079] (**) Option "Device" "/dev/input/event6"
[     4.152] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3249 (res 33)
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2223 (res 33)
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[     4.152] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     4.152] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     4.152] (**) ETPS/2 Elantech Touchpad: always reports core events
[     4.184] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input13/event6"
[     4.184] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[     4.184] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     4.184] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[     4.184] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.051
[     4.184] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     4.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     4.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     4.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     4.184] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     4.184] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[     4.184] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"

```
As you can see, the drivers are loaded correctly but if I run "xinput list-props 13", the device is listed as disabled. Doing "xinput enable 13" does nothing
After I realod psmouse with modprobe, this is appended to Xorg.0.log
```

[   296.329] (II) config/udev: removing device ETPS/2 Elantech Touchpad
[   296.330] (II) UnloadModule: "synaptics"
[   303.517] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[   303.517] (II) No input driver specified, ignoring this device.
[   303.517] (II) This device may have been added with another device file.
[   303.557] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event6)
[   303.557] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[   303.557] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[   303.557] (**) PS/2 Generic Mouse: always reports core events
[   303.557] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event6"
[   303.557] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[   303.557] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[   303.557] (--) evdev: PS/2 Generic Mouse: Found relative axes
[   303.557] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[   303.557] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[   303.557] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[   303.557] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   303.557] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input34/event6"
[   303.557] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 13)
[   303.557] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[   303.557] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[   303.557] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[   303.557] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[   303.557] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4

```
Apparently, the drivers loaded by the command are totally dfferent and recognize my touchpad as a "generic mouse" (this explains the absence of multitouch feature, even in Settings>Mouse&touchpad menu).
Also all the properties listed by "xinput list-props 13" change, but now Device Enabled is set to 1 (and infact I can move the cursor and tap and click).
Doing "sudo modprobe synaptics" doesn't work at all (error: "modprobe: FATAL: Module synaptics not found in directory /lib/modules/4.4.0-21-generic")

Even more strange (or not?), if I boot from a USB installation (same Ubuntu 16.04 and 4.4.0-21 kernel), it all works nicely and multitouch features are enabled too.

Initially the problem showed up on kernel 4.4.0-22, where the touchpad is loaded as "PS/2 Generic Mouse" from the start. Switching to *-21, at least the touchpad is correctly recognized as such

I'm relatively new to Ubuntu and I don't know how to investigate further on the issue... If someone has suggestions, I'd be very grateful

Thank you anticipatedly

EDIT: I have an ASUS F550 laptop

---

### Post by filippoaceto on 2016-08-30
i have the same problem with my f556uj laptop.

---

