---
title: "Display driver error Via EPIA Ubuntu 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by EEUYY on 2011-05-02
Hi all,

I have just upgraded Ubuntu from 10.10 to 11.04 on mu mini-itx desktop and now I can't play any video's in either VLC or any other media player without the driver crashes (I think).

I'm using a VIA EPIA-CN10000EG with a EDEN V4/1000Mhz processor.

When I open a video clip (any video clip) the player starts to play the clip but as soon as I do anything with the window, such as resize or move or set full screen, X crashes and restarts.
When I look in the log file for X it seems that the driver have failed some how:
```
[270150.147] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[270150.147] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input5/event5"
[270150.147] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[270150.147] (II) Logitech Optical USB Mouse: initialized for relative axes.
[270150.148] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[270150.148] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[270150.148] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[270150.148] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[270150.149] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[270150.150] (II) No input driver/identifier specified (ignoring)
[270351.099] Freed 0 (pool 0)
[270351.100] Fulfilled via DRI at 16717184
[270351.102] Freed 0 (pool 0)
[270351.102] Fulfilled via DRI at 16970624
[270351.557]
Backtrace:
[270351.558] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[270351.559] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[270351.559] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x71b40c]
[270351.560] 3: /usr/lib/xorg/modules/drivers/openchrome_drv.so (0x33a000+0x26798) [0x360798]
[270351.560] 4: /usr/bin/X (0x8048000+0x140c26) [0x8188c26]
[270351.561] 5: /usr/bin/X (0x8048000+0x141682) [0x8189682]
[270351.561] 6: /usr/bin/X (miHandleValidateExposures+0x83) [0x81bc133]
[270351.561] 7: /usr/bin/X (miMoveWindow+0x20c) [0x81bc3ac]
[270351.562] 8: /usr/bin/X (0x8048000+0xa7f0b) [0x80eff0b]
[270351.562] 9: /usr/bin/X (ConfigureWindow+0x49d) [0x809a3cd]
[270351.564] 10: /usr/bin/X (0x8048000+0x22239) [0x806a239]
[270351.565] 11: /usr/bin/X (0x8048000+0x28167) [0x8070167]
[270351.567] 12: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[270351.568] 13: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x126e37]
[270351.570] 14: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[270351.571] Segmentation fault at address 0x202
[270351.573]
Caught signal 11 (Segmentation fault). Server aborting
[270351.573]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[270351.574] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[270351.575]
[270351.582] (II) Power Button: Close
[270351.586] (II) UnloadModule: "evdev"
[270351.586] (II) Unloading evdev
[270351.589] (II) Power Button: Close
[270351.598] (II) UnloadModule: "evdev"
[270351.599] (II) Unloading evdev
[270351.602] (II) Sleep Button: Close
[270351.605] (II) UnloadModule: "evdev"
[270351.608] (II) Unloading evdev
[270351.613] (II)   USB Keyboard: Close
[270351.616] (II) UnloadModule: "evdev"
[270351.620] (II) Unloading evdev
[270351.621] (II)   USB Keyboard: Close
[270351.625] (II) UnloadModule: "evdev"
[270351.627] (II) Unloading evdev
[270351.631] (II) Logitech Optical USB Mouse: Close
[270351.632] (II) UnloadModule: "evdev"
[270351.634] (II) Unloading evdev
[270351.637] (II) AIGLX: Suspending AIGLX clients for VT switch
[270351.638] Freed 16717184 (pool 2)
[270351.639] Freed 16970624 (pool 2)
[270351.640] (II) CHROME(0): VIALeaveVT
[270351.641] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[270352.486] (II) CHROME(0): ViaCursorStore
[270352.486] (II) CHROME(0): VIARestore
[270352.486] (II) CHROME(0): VT162xRestore
[270352.611] (II) CHROME(0): ViaDisablePrimaryFIFO
[270352.633]  ddxSigGiveUp: Closing log

```

Does anyone have some clues as to where I could continue trouble shoot?

Also I the system won't let me run the unity interface as my desktop doesn't have the power to run it, so I'm running GNOME 2

```
Processor               : VIA Esther processor 1000MHz
Memory          : 960MB (340MB used)
Operating System                : Ubuntu 11.04
User Name               : media (Media)
Date/Time               : Mon 02 May 2011 11:44:46 PM CEST
-Display-
Resolution              : 1360x768 pixels
OpenGL Renderer         : Mesa DRI UniChrome 20060710 x86/MMX/SSE2
X11 Vendor              : The X.Org Foundation
-Multimedia-
Audio Adapter           : VIA8237 - VIA 8237
-SCSI Disks-
ATA WDC WD5000AAKS-6

```

---

### Post by raxhonp on 2011-06-15
See [http://ubuntuforums.org/showpost.php?p=10941121&postcount=12](http://ubuntuforums.org/showpost.php?p=10941121&postcount=12), that should help solve your problem.

---

### Post by EEUYY on 2011-06-15
Thanks for the help, it work perfectly!

---

