---
title: "Xorg frequent crashes"
date: 2011-08-12
forum: Hardware
---

### Post by wishingstar on 2011-08-12
Xorg has been frequently crashing on my kubuntu laptop. It happens at random instances when I start or stop services. Mostly it's been happening when I would unplug my drawing tablet (Aiptek) but recently it's starting to happen when I start/run other services too! The last time it crashed I was starting a configuration script that uses Zenity. The crash causes a black terminal-like screen (sorry for the non-technical description) and my session simply resets, no warnings and with a loss of any work that is being done when the crash happens. It used to not bother me so much when it would happen from time to time, but lately it's been happening a lot and it's really starting to impede my work.

Here's a copy of the last section of /var/log/Xorg.0.log.old:

```
[ 82113.172] (II) config/udev: Adding input device Aiptek (/dev/input/mouse2)
[ 82113.198] (II) No input driver/identifier specified (ignoring)
[ 82113.201] (II) config/udev: Adding input device Aiptek (/dev/input/event8)
[ 82113.201] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[ 82113.201] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[ 82113.201] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[ 82113.201] (**) Aiptek: Applying InputClass "Aiptek class"
[ 82113.231] (II) LoadModule: "aiptek"
[ 82113.279] (II) Loading /usr/lib/xorg/modules/input/aiptek_drv.so
[ 82113.302] (II) Module aiptek: vendor="X.Org Foundation"
[ 82113.302]     compiled for 1.9.99.902, module version = 1.3.99
[ 82113.302]     Module class: X.Org XInput Driver
[ 82113.302]     ABI class: X.Org XInput driver, version 12.3
[ 82113.323] (II) Using input driver 'aiptek' for 'Aiptek'
[ 82113.323] (II) Loading /usr/lib/xorg/modules/input/aiptek_drv.so
[ 82113.323] (**) Aiptek: always reports core events
[ 82113.324] (II) xf86AiptekInit(): begins
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and Video Bus
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and AT Translated Set 2 keyboard
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and SynPS/2 Synaptics TouchPad
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and  USB OPTICAL MOUSE
[ 82113.324] (**) xf86AiptekConfig: device not shared btw Aiptek and Aiptek
[ 82113.324] (**) Aiptek: always reports core events
[ 82113.324] (**) Option "Device" "/dev/input/event8"
[ 82113.328] (--) HID Device name: "Aiptek"
[ 82113.328] (--) HID Driver Version: 1.0.1
[ 82113.328] (--) HID Driver knows it has 1 devices configured
[ 82113.328] (--) HID Driver is using 69 as the fd
[ 82113.328] (EE) From ioctl() xCapacity=11999
[ 82113.328] (EE) From ioctl() yCapacity=8999
[ 82113.329] (**) Aiptek device is /dev/input/event8
[ 82113.329] (**) Aiptek is in absolute mode
[ 82113.329] (**) Option "USB" "on"
[ 82113.329] (**) Aiptek: reading USB link
[ 82113.329] (**) Option "ZMax" "1023"
[ 82113.329] (**) Aiptek: ZMax/MaxZ = 1023
[ 82113.329] (**) Option "ZMin" "0"
[ 82113.329] (**) Aiptek: ZMin/MinZ = 0
[ 82113.329] (**) Option "BaudRate" "9600"
[ 82113.329] (**) Aiptek: BaudRate 9600
[ 82113.329] (**) Aiptek: xf86AiptekInit() finished
[ 82113.329] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input10/event8"
[ 82113.329] (II) XINPUT: Adding extended input device "Aiptek" (type: Stylus)
[ 82113.329] (**) xTop invalid; adjusted to 0
[ 82113.330] (**) yTop invalid; adjusted to 0
[ 82113.330] (**) xBottom invalid; adjusted to 11999
[ 82113.330] (**) yBottom invalid; adjusted to 8999
[ 82113.330] (**) ScreenNo invalid; adjusted to 0
[ 82113.330] (**) Aiptek: (accel) keeping acceleration scheme 1
[ 82113.330] (**) Aiptek: (accel) acceleration profile 0
[ 82113.330] (**) Aiptek: (accel) acceleration factor: 2.000
[ 82113.330] (**) Aiptek: (accel) acceleration threshold: 4
[ 82113.330] (--) HID Device name: "Aiptek"
[ 82113.331] (--) HID Driver Version: 1.0.1
[ 82113.331] (--) HID Driver knows it has 1 devices configured
[ 82113.331] (--) HID Driver is using 69 as the fd
[ 82113.331] (EE) From ioctl() xCapacity=11999
[ 82113.331] (EE) From ioctl() yCapacity=8999
[ 82113.331] (EE) Able to open aiptek device
[ 82465.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-65852DDC4CDF5A76BE99136643F13565B65F262B.xkm
[ 91256.297] (II) config/udev: removing device  USB OPTICAL MOUSE
[ 91256.298] (II)  USB OPTICAL MOUSE: Close
[ 91256.298] (II) UnloadModule: "evdev"
[ 91256.299] (II) Unloading evdev
[ 91265.320] (EE) Error reading Aiptek tablet: No such device
[ 91265.343] (II) config/udev: removing device Aiptek
[ 91265.353] (II) UnloadModule: "aiptek"
[ 91265.353] (II) Unloading aiptek
[ 91316.088] (II) XKB: reuse xkmfile /var/lib/xkb/server-65852DDC4CDF5A76BE99136643F13565B65F262B.xkm
[103924.932] 
Backtrace:
[103924.962] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab8b]
[103924.962] 1: /usr/bin/X (0x8048000+0x5fb38) [0x80a7b38]
[103924.962] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb771240c]
[103924.962] 3: /usr/bin/X (LookupClientResourceComplex+0x8b) [0x80916eb]
[103924.963] 4: /usr/bin/X (0x8048000+0xa8e3a) [0x80f0e3a]
[103924.963] 5: /usr/bin/X (0x8048000+0xaa40c) [0x80f240c]
[103924.963] 6: /usr/bin/X (0x8048000+0xad3ad) [0x80f53ad]
[103924.963] 7: /usr/bin/X (0x8048000+0x28167) [0x8070167]
[103924.963] 8: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[103924.963] 9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb7421e37]
[103924.963] 10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[103924.963] Segmentation fault at address 0x33
[103924.963] 
Caught signal 11 (Segmentation fault). Server aborting
[103924.993] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[103924.993] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[103925.001] 
[103925.024] (II) Power Button: Close
[103925.025] (II) UnloadModule: "evdev"
[103925.025] (II) Unloading evdev
[103925.025] (II) Video Bus: Close
[103925.026] (II) UnloadModule: "evdev"
[103925.026] (II) Unloading evdev
[103925.026] (II) Power Button: Close
[103925.027] (II) UnloadModule: "evdev"
[103925.027] (II) Unloading evdev
[103925.027] (II) AT Translated Set 2 keyboard: Close
[103925.028] (II) UnloadModule: "evdev"
[103925.028] (II) Unloading evdev
[103925.064] (II) UnloadModule: "synaptics"
[103925.064] (II) Unloading synaptics
[103925.092] (II) AIGLX: Suspending AIGLX clients for VT switch
[103925.176]  ddxSigGiveUp: Closing log

```

I cannot find a backtrace of any kind in the new Xorg log though.

Any help is appreciated.

---

