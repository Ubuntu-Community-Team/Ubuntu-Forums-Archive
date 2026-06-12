---
title: "Proprietary driver for Nvidia gtx465 boots to a black log in screen"
date: 2014-02-15
forum: Hardware
---

### Post by ps2chiper on 2014-02-15
Hey guys, I have a weird problem. Ubuntu will boot to the log in screen. I can tell because of the sounds. But the screen is black. It doesn't have this problem with the open source driver. 


Here is the X.org log. If anyone could help me solve it, you will have my eternal gratitude. 

```
[    19.882] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    19.882] X Protocol Version 11, Revision 0
[    19.882] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.882] Current Operating System: Linux jason1-desktop 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64
[    19.882] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=7d436dcf-eb47-4e2e-8eb2-660c7141258a ro recovery nomodeset
[    19.882] Build Date: 17 December 2013  10:06:15AM
[    19.882] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.882] Current version of pixman: 0.30.2
[    19.882]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    19.882] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.882] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 15 13:40:43 2014
[    20.068] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.302] (==) No Layout section.  Using the first Screen section.
[    20.302] (==) No screen section available. Using defaults.
[    20.302] (**) |-->Screen "Default Screen Section" (0)
[    20.302] (**) |   |-->Monitor "<default monitor>"
[    20.325] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.325] (==) Automatically adding devices
[    20.325] (==) Automatically enabling devices
[    20.325] (==) Automatically adding GPU devices
[    20.495] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.495]     Entry deleted from font path.
[    20.496] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.496]     Entry deleted from font path.
[    20.496] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.496]     Entry deleted from font path.
[    20.496] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.496] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.496] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.496] (II) Loader magic: 0x7f425c58bd20
[    20.496] (II) Module ABI versions:
[    20.496]     X.Org ANSI C Emulation: 0.4
[    20.496]     X.Org Video Driver: 14.1
[    20.496]     X.Org XInput driver : 19.1
[    20.496]     X.Org Server Extension : 7.0
[    20.497] (--) PCI: (0:0:2:0) 8086:0162:1849:0162 rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    20.497] (--) PCI:*(0:1:0:0) 10de:06c4:10de:0839 rev 163, Mem @ 0xf4000000/33554432, 0xe0000000/134217728, 0xe8000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    20.497] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.525] Initializing built-in extension Generic Event Extension
[    20.525] Initializing built-in extension SHAPE
[    20.525] Initializing built-in extension MIT-SHM
[    20.525] Initializing built-in extension XInputExtension
[    20.525] Initializing built-in extension XTEST
[    20.525] Initializing built-in extension BIG-REQUESTS
[    20.525] Initializing built-in extension SYNC
[    20.525] Initializing built-in extension XKEYBOARD
[    20.525] Initializing built-in extension XC-MISC
[    20.525] Initializing built-in extension SECURITY
[    20.525] Initializing built-in extension XINERAMA
[    20.525] Initializing built-in extension XFIXES
[    20.525] Initializing built-in extension RENDER
[    20.525] Initializing built-in extension RANDR
[    20.525] Initializing built-in extension COMPOSITE
[    20.525] Initializing built-in extension DAMAGE
[    20.525] Initializing built-in extension MIT-SCREEN-SAVER
[    20.525] Initializing built-in extension DOUBLE-BUFFER
[    20.525] Initializing built-in extension RECORD
[    20.525] Initializing built-in extension DPMS
[    20.525] Initializing built-in extension X-Resource
[    20.525] Initializing built-in extension XVideo
[    20.525] Initializing built-in extension XVideo-MotionCompensation
[    20.525] Initializing built-in extension SELinux
[    20.525] Initializing built-in extension XFree86-VidModeExtension
[    20.525] Initializing built-in extension XFree86-DGA
[    20.525] Initializing built-in extension XFree86-DRI
[    20.525] Initializing built-in extension DRI2
[    20.525] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    20.525] (II) "glx" will be loaded by default.
[    20.525] (WW) "xmir" is not to be loaded by default. Skipping.
[    20.525] (II) LoadModule: "glx"
[    20.602] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.609] (II) Module glx: vendor="NVIDIA Corporation"
[    22.609]     compiled for 4.0.2, module version = 1.0.0
[    22.609]     Module class: X.Org Server Extension
[    22.609] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[    22.655] Loading extension GLX
[    22.655] (==) Matched nvidia as autoconfigured driver 0
[    22.655] (==) Matched nouveau as autoconfigured driver 1
[    22.655] (==) Matched vesa as autoconfigured driver 2
[    22.655] (==) Matched modesetting as autoconfigured driver 3
[    22.655] (==) Matched fbdev as autoconfigured driver 4
[    22.655] (==) Assigned the driver to the xf86ConfigLayout
[    22.655] (II) LoadModule: "nvidia"
[    22.655] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.103] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.103]     compiled for 4.0.2, module version = 1.0.0
[    23.103]     Module class: X.Org Video Driver
[    23.123] (II) LoadModule: "nouveau"
[    23.193] (WW) Warning, couldn't open module nouveau
[    23.193] (II) UnloadModule: "nouveau"
[    23.193] (II) Unloading nouveau
[    23.193] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    23.193] (II) LoadModule: "vesa"
[    23.193] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.241] (II) Module vesa: vendor="X.Org Foundation"
[    23.241]     compiled for 1.14.1, module version = 2.3.2
[    23.241]     Module class: X.Org Video Driver
[    23.241]     ABI class: X.Org Video Driver, version 14.1
[    23.241] (II) LoadModule: "modesetting"
[    23.241] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.252] (II) Module modesetting: vendor="X.Org Foundation"
[    23.252]     compiled for 1.14.1, module version = 0.8.0
[    23.252]     Module class: X.Org Video Driver
[    23.252]     ABI class: X.Org Video Driver, version 14.1
[    23.252] (II) LoadModule: "fbdev"
[    23.252] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.298] (II) Module fbdev: vendor="X.Org Foundation"
[    23.298]     compiled for 1.14.1, module version = 0.4.3
[    23.298]     Module class: X.Org Video Driver
[    23.298]     ABI class: X.Org Video Driver, version 14.1
[    23.298] (==) Matched nvidia as autoconfigured driver 0
[    23.298] (==) Matched nouveau as autoconfigured driver 1
[    23.298] (==) Matched vesa as autoconfigured driver 2
[    23.298] (==) Matched modesetting as autoconfigured driver 3
[    23.298] (==) Matched fbdev as autoconfigured driver 4
[    23.298] (==) Assigned the driver to the xf86ConfigLayout
[    23.298] (II) LoadModule: "nvidia"
[    23.298] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.298] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.298]     compiled for 4.0.2, module version = 1.0.0
[    23.298]     Module class: X.Org Video Driver
[    23.298] (II) UnloadModule: "nvidia"
[    23.298] (II) Unloading nvidia
[    23.298] (II) Failed to load module "nvidia" (already loaded, 32578)
[    23.298] (II) LoadModule: "nouveau"
[    23.298] (WW) Warning, couldn't open module nouveau
[    23.298] (II) UnloadModule: "nouveau"
[    23.298] (II) Unloading nouveau
[    23.298] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    23.298] (II) LoadModule: "vesa"
[    23.298] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.298] (II) Module vesa: vendor="X.Org Foundation"
[    23.298]     compiled for 1.14.1, module version = 2.3.2
[    23.298]     Module class: X.Org Video Driver
[    23.298]     ABI class: X.Org Video Driver, version 14.1
[    23.298] (II) UnloadModule: "vesa"
[    23.298] (II) Unloading vesa
[    23.298] (II) Failed to load module "vesa" (already loaded, 0)
[    23.298] (II) LoadModule: "modesetting"
[    23.298] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.298] (II) Module modesetting: vendor="X.Org Foundation"
[    23.298]     compiled for 1.14.1, module version = 0.8.0
[    23.298]     Module class: X.Org Video Driver
[    23.298]     ABI class: X.Org Video Driver, version 14.1
[    23.298] (II) UnloadModule: "modesetting"
[    23.298] (II) Unloading modesetting
[    23.298] (II) Failed to load module "modesetting" (already loaded, 0)
[    23.298] (II) LoadModule: "fbdev"
[    23.299] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.299] (II) Module fbdev: vendor="X.Org Foundation"
[    23.299]     compiled for 1.14.1, module version = 0.4.3
[    23.299]     Module class: X.Org Video Driver
[    23.299]     ABI class: X.Org Video Driver, version 14.1
[    23.299] (II) UnloadModule: "fbdev"
[    23.299] (II) Unloading fbdev
[    23.299] (II) Failed to load module "fbdev" (already loaded, 0)
[    23.299] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[    23.299] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.334] (II) VESA: driver for VESA chipsets: vesa
[    23.334] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.334] (II) FBDEV: driver for framebuffer: fbdev
[    23.334] (++) using VT number 7

[    23.374] (II) Loading sub module "fb"
[    23.374] (II) LoadModule: "fb"
[    23.374] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.405] (II) Module fb: vendor="X.Org Foundation"
[    23.405]     compiled for 1.14.5, module version = 1.0.0
[    23.405]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.405] (WW) Unresolved symbol: fbGetGCPrivateKey
[    23.405] (II) Loading sub module "wfb"
[    23.405] (II) LoadModule: "wfb"
[    23.405] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.451] (II) Module wfb: vendor="X.Org Foundation"
[    23.451]     compiled for 1.14.5, module version = 1.0.0
[    23.452]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.452] (II) Loading sub module "ramdac"
[    23.452] (II) LoadModule: "ramdac"
[    23.452] (II) Module "ramdac" already built-in
[    23.494] (WW) Falling back to old probe method for vesa
[    23.494] (WW) Falling back to old probe method for modesetting
[    23.494] (EE) open /dev/dri/card0: No such file or directory
[    23.494] (EE) open /dev/dri/card0: No such file or directory
[    23.494] (WW) Falling back to old probe method for fbdev
[    23.494] (II) Loading sub module "fbdevhw"
[    23.494] (II) LoadModule: "fbdevhw"
[    23.494] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.508] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.508]     compiled for 1.14.5, module version = 0.0.2
[    23.508]     ABI class: X.Org Video Driver, version 14.1
[    23.508] (EE) open /dev/fb0: No such file or directory
[    23.508] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.508] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    23.508] (==) NVIDIA(0): RGB weight 888
[    23.508] (==) NVIDIA(0): Default visual is TrueColor
[    23.508] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.508] (**) NVIDIA(0): Enabling 2D acceleration
[    23.527] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    23.527] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    23.527] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    23.528] (EE) NVIDIA(0):  *** Aborting ***
[    23.528] (EE) NVIDIA(0): Failing initialization of X screen 0
[    23.528] (II) UnloadModule: "nvidia"
[    23.528] (II) UnloadSubModule: "wfb"
[    23.528] (II) UnloadSubModule: "fb"
[    23.528] (EE) Screen(s) found, but none have a usable configuration.
[    23.528] (EE) 
Fatal server error:
[    23.528] (EE) no screens found(EE) 
[    23.528] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    23.528] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    23.528] (EE) 
[    23.529] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by papibe on 2014-02-15
Hi ps2chiper.

Try to set the 'nomodeset' option. Here's a similar [thread]("http://ubuntuforums.org/showthread.php?t=2161671&highlight=nomodeset").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldfred on 2014-02-15
Please use code tags for long terminal output. You can add easily with # in Advanced editor.

It also says this
 (EE) Failed to load module "nouveau" (module does not exist, 0)
Did you blacklist the nouveau driver?

How did you install nVidia. Best if from repository.
But you have to totally houseclean/purge one install of nVidia before attempting a different install.

---

### Post by Detlef_Bracker on 2014-02-16
Possible use this workarround: [http://ubuntuforums.org/showthread.php?t=2205651](http://ubuntuforums.org/showthread.php?t=2205651)

---

