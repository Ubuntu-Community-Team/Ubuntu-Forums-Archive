---
title: "Laptop display freezes and on reboot startx fails"
date: 2011-03-31
forum: Hardware
---

### Post by shredder12 on 2011-03-31
Hi, 

Since, this morning I am having some weird trouble with the display. After a while the display just freezes and I have to do a cold reboot. Not just this, once the system boots again, even the display of bios looks affected with weird lines all over the place.
 
When I try to boot anyway in these conditions, I can't even get to the recovery mode. The grub screen shows up but as soon as I click on recovery mode, after a few seconds, the screen just shuts off(although processing is still on).

After leaving the laptop for a while, things work fine for some time. I have a hunch this is due to over-heating of Nvidia card.

Here is the failure log of X.Org when I did startx. Notice the erros in the end. I had the same issue with Win7 too, so the trouble is definitely not X.

```
[    25.783] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    25.784] X Protocol Version 11, Revision 0
[    25.784] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    25.784] Current Operating System: Linux sahni-Vostro1510 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    25.784] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=c83c7204-5e93-4650-880d-ffa6f71bcb66 ro quiet splash
[    25.784] Build Date: 09 January 2011  12:14:58PM
[    25.784] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    25.785] Current version of pixman: 0.18.4
[    25.785] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    25.785] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.786] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 31 15:21:48 2011
[    25.786] (==) Using config file: "/etc/X11/xorg.conf"
[    25.787] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.787] (==) ServerLayout "Layout0"
[    25.787] (**) |-->Screen "Screen0" (0)
[    25.787] (**) |   |-->Monitor "Monitor0"
[    25.787] (**) |   |-->Device "Device0"
[    25.787] (**) |-->Input Device "Keyboard0"
[    25.787] (**) |-->Input Device "Mouse0"
[    25.787] (==) Automatically adding devices
[    25.787] (==) Automatically enabling devices
[    25.788] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.788] 	Entry deleted from font path.
[    25.788] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    25.788] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.788] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    25.788] (WW) Disabling Keyboard0
[    25.788] (WW) Disabling Mouse0
[    25.788] (II) Loader magic: 0x81f9b00
[    25.788] (II) Module ABI versions:
[    25.788] 	X.Org ANSI C Emulation: 0.4
[    25.788] 	X.Org Video Driver: 8.0
[    25.788] 	X.Org XInput driver : 11.0
[    25.788] 	X.Org Server Extension : 4.0
[    25.789] (--) PCI:*(0:1:0:0) 10de:0427:1028:0273 rev 161, Mem @ 0xca000000/16777216, 0xd0000000/268435456, 0xc8000000/33554432, I/O @ 0x00002000/128
[    25.789] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.789] (II) LoadModule: "extmod"
[    25.790] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.790] (II) Module extmod: vendor="X.Org Foundation"
[    25.790] 	compiled for 1.9.0, module version = 1.0.0
[    25.790] 	Module class: X.Org Server Extension
[    25.790] 	ABI class: X.Org Server Extension, version 4.0
[    25.790] (II) Loading extension MIT-SCREEN-SAVER
[    25.790] (II) Loading extension XFree86-VidModeExtension
[    25.790] (II) Loading extension XFree86-DGA
[    25.790] (II) Loading extension DPMS
[    25.790] (II) Loading extension XVideo
[    25.790] (II) Loading extension XVideo-MotionCompensation
[    25.790] (II) Loading extension X-Resource
[    25.790] (II) LoadModule: "dbe"
[    25.790] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.790] (II) Module dbe: vendor="X.Org Foundation"
[    25.790] 	compiled for 1.9.0, module version = 1.0.0
[    25.790] 	Module class: X.Org Server Extension
[    25.790] 	ABI class: X.Org Server Extension, version 4.0
[    25.790] (II) Loading extension DOUBLE-BUFFER
[    25.790] (II) LoadModule: "glx"
[    25.791] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.816] (II) Module glx: vendor="NVIDIA Corporation"
[    25.816] 	compiled for 4.0.2, module version = 1.0.0
[    25.816] 	Module class: X.Org Server Extension
[    25.816] (II) NVIDIA GLX Module  260.19.44  Sun Feb 27 21:47:21 PST 2011
[    25.816] (II) Loading extension GLX
[    25.816] (II) LoadModule: "record"
[    25.816] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.816] (II) Module record: vendor="X.Org Foundation"
[    25.816] 	compiled for 1.9.0, module version = 1.13.0
[    25.816] 	Module class: X.Org Server Extension
[    25.816] 	ABI class: X.Org Server Extension, version 4.0
[    25.817] (II) Loading extension RECORD
[    25.817] (II) LoadModule: "dri"
[    25.817] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.817] (II) Module dri: vendor="X.Org Foundation"
[    25.817] 	compiled for 1.9.0, module version = 1.0.0
[    25.817] 	ABI class: X.Org Server Extension, version 4.0
[    25.817] (II) Loading extension XFree86-DRI
[    25.817] (II) LoadModule: "dri2"
[    25.817] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.817] (II) Module dri2: vendor="X.Org Foundation"
[    25.817] 	compiled for 1.9.0, module version = 1.2.0
[    25.817] 	ABI class: X.Org Server Extension, version 4.0
[    25.817] (II) Loading extension DRI2
[    25.817] (II) LoadModule: "nvidia"
[    25.818] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    25.818] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.818] 	compiled for 4.0.2, module version = 1.0.0
[    25.818] 	Module class: X.Org Video Driver
[    25.818] (II) NVIDIA dlloader X Driver  260.19.44  Sun Feb 27 21:31:52 PST 2011
[    25.818] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    25.818] (--) using VT number 8

[    25.834] (II) Loading sub module "fb"
[    25.834] (II) LoadModule: "fb"
[    25.834] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.834] (II) Module fb: vendor="X.Org Foundation"
[    25.834] 	compiled for 1.9.0, module version = 1.0.0
[    25.834] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.834] (II) Loading sub module "wfb"
[    25.834] (II) LoadModule: "wfb"
[    25.835] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    25.835] (II) Module wfb: vendor="X.Org Foundation"
[    25.835] 	compiled for 1.9.0, module version = 1.0.0
[    25.835] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.835] (II) Loading sub module "ramdac"
[    25.835] (II) LoadModule: "ramdac"
[    25.835] (II) Module "ramdac" already built-in
[    25.835] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    25.835] (==) NVIDIA(0): RGB weight 888
[    25.835] (==) NVIDIA(0): Default visual is TrueColor
[    25.835] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.835] (**) NVIDIA(0): Enabling RENDER acceleration
[    25.835] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    25.835] (II) NVIDIA(0):     enabled.
[    26.004] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    26.004] (EE) NVIDIA(0):     check your system's kernel log for additional error
[    26.004] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    26.004] (EE) NVIDIA(0):     README for additional information.
[    26.004] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    26.004] (II) UnloadModule: "nvidia"
[    26.004] (II) UnloadModule: "wfb"
[    26.004] (II) UnloadModule: "fb"
[    26.004] (EE) Screen(s) found, but none have a usable configuration.
[    26.004] 
Fatal server error:
[    26.005] no screens found
[    26.005] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    26.005] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    26.005] 
[    26.019]  ddxSigGiveUp: Closing log

```

---

