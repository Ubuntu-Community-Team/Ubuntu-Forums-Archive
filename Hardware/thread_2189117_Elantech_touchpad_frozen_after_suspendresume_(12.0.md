---
title: "Elantech touchpad frozen after suspend/resume (12.04.3 LTS)"
date: 2013-11-20
forum: Hardware
---

### Post by martinr on 2013-11-20
The Elantech touchpad on my laptop gets to be frozen/unusable and interferes with typing after a suspend/resume.

It occurs with a freshly installed XUbuntu 12.04.3 LTS (precise) + updates, with kernel 3.2.0-56-generic (32bit).
I happens on an Acer Aspire 5502ZWXMi (Aspire 5500Z series) laptop. (The same laptop ran Ubuntu 6.04, 8.04 and 10.04 LTS without this problem).

I found the following in the Xorg logging.

Before suspend I noticed:
```

[    29.631] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.631] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.631] (II) LoadModule: "evdev"
[    29.632] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.632] (II) Module evdev: vendor="X.Org Foundation"
[    29.632]    compiled for 1.11.3, module version = 2.7.0
[    29.632]    Module class: X.Org XInput Driver
[    29.632]    ABI class: X.Org XInput driver, version 16.0
[    29.632] (II) Using input driver 'evdev' for 'Power Button'
[    29.632] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.632] (**) Power Button: always reports core events
[    29.632] (**) evdev: Power Button: Device: "/dev/input/event3"
...
[    29.648] (II) Using input driver 'evdev' for 'ImPS/2 Elantech Touchpad'
[    29.648] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.649] (**) ImPS/2 Elantech Touchpad: always reports core events
[    29.649] (**) evdev: ImPS/2 Elantech Touchpad: Device: "/dev/input/event6"
[    29.649] (--) evdev: ImPS/2 Elantech Touchpad: Vendor 0x2 Product 0x5

```

After resume I noticed:
```

< [   444.776] (II) config/udev: removing device ImPS/2 Elantech Touchpad
< [   444.777] (II) evdev: ImPS/2 Elantech Touchpad: Close
< [   444.777] (II) UnloadModule: "evdev"
< [   444.777] (II) Unloading evdev
< [   444.886] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
< [   444.886] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
< [   444.886] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
< [   444.886] (II) LoadModule: "synaptics"
< [   444.886] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
< [   444.898] (II) Module synaptics: vendor="X.Org Foundation"
< [   444.898]  compiled for 1.11.3, module version = 1.6.2
< [   444.898]  Module class: X.Org XInput Driver
< [   444.898]  ABI class: X.Org XInput driver, version 16.0
< [   444.898] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
< [   444.898] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
< [   444.898] (**) ETPS/2 Elantech Touchpad: always reports core events
< [   444.898] (**) Option "Device" "/dev/input/event6"
...
< [   444.898] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
< [   444.898] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.332
< [   444.899] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
< [   444.899] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
< [   444.899] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
< [   444.899] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
< [   444.899] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
< [   444.899] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"

```

Could it be that a different driver is loaded or even double loaded for the touch-pad?

Does anybody recognize or have a solution for this problem?

---

### Post by Toz on 2013-11-20
Does unload and reloading the psmouse module after resume make the touchpad work again?
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

If so, it can be automated.

---

### Post by martinr on 2013-11-21
> **Toz said:**
> 
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```


Jikes! That summons my touchpad back to life. Thanks, that's great!
How could one automate that workaround? 
And what would be the right place/moment to do it?

I saw the following appear in dmesg before and upto suspend:
```

[ 7661.764038] PM: Entering mem sleep
...
[ 7662.344543] PM: late suspend of devices complete after 16.662 msecs
[ 7662.345060] ACPI: Preparing to enter system sleep state S3
[ 7662.346879] PM: Saving platform NVS memory
[ 7662.346884] Disabling non-boot CPUs ...

```

I saw the following appear in dmesg after the resume:
```

[ 7662.346884] ACPI: Low-level resume complete
[ 7662.346884] PM: Restoring platform NVS memory
[ 7662.346884] Force enabled HPET at resume
[ 7662.347116] ACPI: Waking up from system sleep state S3
...
[ 7663.417515] PM: resume of drv:snd_intel8x0 dev:0000:00:1e.2 complete after 1027.461 msecs
[ 7663.569777] psmouse serio4: hgpk: ID: 10 00 64
[ 7663.770060] psmouse serio4: hgpk: ID: 10 00 64
[ 7663.868881] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[ 7663.896902] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[ 7664.100461] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
...
[ 7665.432078] PM: resume of devices complete after 3078.328 msecs
[ 7665.432151] PM: resume devices took 3.080 seconds
[ 7665.432194] PM: Finishing wakeup.

```

I saw this happen when I did the modprobe that fixes the touchpad:
```

[ 7805.306530] psmouse serio4: hgpk: ID: 10 00 64
[ 7805.380322] psmouse serio4: elantech: assuming hardware version 1 (with firmware version 0x020000)
[ 7805.408733] psmouse serio4: elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[ 7805.599690] psmouse serio4: elantech: touchpad refuses to switch to absolute mode.
[ 7805.599703] psmouse serio4: elantech: failed to initialise registers.
[ 7805.599713] psmouse serio4: elantech: failed to put touchpad into absolute mode.
[ 7806.090532] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input8

```

Any idea what went wrong?

---

### Post by Toz on 2013-11-21
Not sure why thats happening, its just that on some laptops, the touchpad doesn't work after resume unless the psmouse module is unloaded and reloaded. To make this automatic, create the file **/etc/pm/sleep.d/65fixtouchpad**:
```
sudo leafpad /etc/pm/sleep.d/65fixtouchpad
```
...enter your password when prompted and copy/paste this content:
```
#!/bin/sh
#
# 65fixtouchpad: unload/reload psmouse module

case "$1" in
   hibernate|suspend)
      modprobe -r psmouse
   ;;
   thaw|resume)
      modprobe psmouse
   ;;
   *) exit $NA
   ;;
esac
```
...save the file and make it executable:
```
sudo chmod +x /etc/pm/sleep.d/65fixtouchpad
```
...and try it again to see if it works.

---

### Post by martinr on 2013-11-21
The workaround with the /etc/pm/sleep.d/65fixtouchpad script works like a charm.
Thank you very much for your quick and effective response!
This turns my XUbuntu setup into a usable rig. =D>

Is the /etc/pm/sleep.d/65fixtouchpad also triggered during resume from hibernate (that's the next thing I would like to get working)?

Regarding what went wrong in the first place, this is what is set up on resume (taken from dmesg):
```
[ 7664.100461] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
```

And this is what removal and again adding of the psmouse kernel module results in (taken from dmesg):
```
[ 7806.090532] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input8
```

In Xorg.log I find:
```

< [   444.776] (II) config/udev: removing device ImPS/2 Elantech Touchpad
< [   444.777] (II) evdev: ImPS/2 Elantech Touchpad: Close
< [   444.777] (II) UnloadModule: "evdev"
< [   444.777] (II) Unloading evdev
< [   444.886] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
< [   444.886] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
< [   444.886] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
< [   444.886] (II) LoadModule: "synaptics"
< [   444.886] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
< [   444.898] (II) Module synaptics: vendor="X.Org Foundation"
< [   444.898]  compiled for 1.11.3, module version = 1.6.2
< [   444.898]  Module class: X.Org XInput Driver
< [   444.898]  ABI class: X.Org XInput driver, version 16.0
< [   444.898] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
< [   444.898] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
< [   444.898] (**) ETPS/2 Elantech Touchpad: always reports core events
< [   444.898] (**) Option "Device" "/dev/input/event6"
...
[  3072.238] (II) config/udev: Adding input device ImPS/2 Elantech Touchpad (/dev/input/mouse0)
[  3072.238] (II) No input driver specified, ignoring this device.
[  3072.238] (II) This device may have been added with another device file.

```

It seems that hardware detection initially goes wrong during resume. I've got a hunch that it's got something to do with the migration from System V like init to upstart and results in a race condition on drm, the bridge between Upstart and udev?

Is there a known bug that I stumbled upon, or should I report a new one?

---

### Post by Toz on 2013-11-21
> Is there a known bug that I stumbled upon, or should I report a new one? 
Nothing wrong with creating a bug report. If there's an existing one out there, the bug reporting process may help to identify it. Keep in mind that you are also using an older kernel (3.2x) and there is a chance that this has already been fixed on later kernels.

---

### Post by martinr on 2013-11-23
My hypothesis is that something holds DRM master, which results in a race condition with upstart events.
How could I test this hypothysis? Is there a way to slow down the resume/restart of xorg?

---

### Post by arthur-aida on 2014-10-25
The new kernel ubuntu 3.18 multitouch enabled my ETPS/2 Elantech Touchpad with zoom photos, vertical and horizontal scrolling with two fingers like in windows 8. Tested on ubuntu 14.10 with all updates.

---

