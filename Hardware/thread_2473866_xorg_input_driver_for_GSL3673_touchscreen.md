---
title: "xorg input driver for GSL3673 touchscreen ?"
date: 2022-04-16
forum: Hardware
---

### Post by dieselnutjob on 2022-04-16
Hi
I am trying to get the touchscreen to work on a prototype tablet that I have.
The tablet has a GSL3673 touch panel, and currently uses a Rockchip BSP kernel, with the eventual aim of going mainline.
I can run either Android or standard Linux on the tablet using basically the same kernel with different configs.
I have tried evdev, libinput and multitouch drivers for xorg, and basically they all have the same result.
I can see that they initialise the panel and load the firmware, but then they don't respond to touch input.
More specifically if I do cat /dev/input/event1 in Android and touch the screen then characters appear on the console, however, in Linux with xorg nothing appears on the console.
Here is the output from multitouch:-
```

[    64.414] (II) config/udev: Adding input device gsl3673_800x1280 (/dev/input/event1)
[    64.414] (**) gsl3673_800x1280: Applying InputClass "evdev touchscreen catchall"
[    64.414] (**) gsl3673_800x1280: Applying InputClass "libinput touchscreen catchall"
[    64.414] (**) gsl3673_800x1280: Applying InputClass "touchscreen"
[    64.414] (II) LoadModule: "multitouch"
[    64.415] (II) Loading /usr/lib/xorg/modules/input/multitouch_drv.so
[    64.419] (II) Module multitouch: vendor="X.Org Foundation"
[    64.419]     compiled for 1.21.1.3, module version = 0.1.0
[    64.419]     Module class: X.Org XInput Driver
[    64.419]     ABI class: X.Org XInput driver, version 24.4
[    64.419] (II) Using input driver 'multitouch' for 'gsl3673_800x1280'
[    64.419] (**) gsl3673_800x1280: always reports core events
[    64.420] (**) Option "config_info" "udev:/sys/devices/platform/fe5a0000.i2c/i2c-1/1-0040/input/input1/event1"
[    64.420] (II) XINPUT: Adding extended input device "gsl3673_800x1280" (type: TOUCHPAD, id 8)
[    64.420] (II) device control: init
[    64.420] (**) Option "Device" "/dev/input/event1"
[    64.420] (II) multitouch: devname: gsl3673_800x1280
[    64.420] (II) multitouch: devid: 0 0 0
[    64.420] (II) multitouch: caps: mtdata
[    64.420] (II) multitouch: 0: min: 0 max: 255
[    64.420] (II) multitouch: 2: min: 0 max: 200
[    64.420] (II) multitouch: 5: min: 0 max: 800
[    64.420] (II) multitouch: 6: min: 0 max: 1280
[    64.420] (II) multitouch: 9: min: 0 max: 65535
[    64.473] (II) pointer_control
[    64.473] (**) gsl3673_800x1280: (accel) keeping acceleration scheme 1
[    64.473] (II) pointer_property
[    64.473] (II) pointer_property
[    64.473] (**) gsl3673_800x1280: (accel) acceleration profile 0
[    64.473] (II) pointer_property
[    64.473] (II) pointer_property
[    64.473] (**) gsl3673_800x1280: (accel) acceleration factor: 2.000
[    64.473] (**) gsl3673_800x1280: (accel) acceleration threshold: 4
[    64.473] (II) device control: on
[    64.474] (II) pointer_property
[    64.474] (II) pointer_property

```

I have already modified the kernel driver a bit just to dump out more messages and I get this:-
```

[   62.813279] GSL3673: shutdown_low completed
[   64.595213] GSL3673: shutdown_high completed
[   64.616326] GSL3673: reset_chip completed
[   64.621467] GSL3673: startup_chip completed
[   64.631966] GSL3673: shutdown_low completed
[   64.657213] GSL3673: shutdown_high completed
[   64.704102] GSL3673: init_chip completed
[   64.704160] GSL3673: gsl_resume_work completed
[   64.799326] GSL3673: reset_chip completed
[   65.337770] GSL3673: gsl_load_fw completed
[   65.342926] GSL3673: startup_chip completed
[   65.358413] GSL3673: reset_chip completed
[   65.363563] GSL3673: startup_chip completed
[   65.363568] GSL3673: gsl_download_fw_work completed

```

Here are my questions:-
Which xorg touchscreen driver is most actively being developed?
Which supports the most touchscreens?
Which is easiest to modify to add something new?
What's the best way to contact developers to get some help to make this touchscreen work?

thanks

---

### Post by dieselnutjob on 2022-04-16
and another question:-
Maybe instead of modifying the xorg driver I should be looking at modifying the kernel driver instead?
Is there a similar touchpanel that is known to work well with xorg ?  which xorg driver?
Maybe I can look at the kernel driver for a "good" panel and see what's missing in the gsl3673_800x1280 one, and fix it.

---

