---
title: "Since last week updates, Xorg hangs on start on Maverick"
date: 2010-10-11
forum: Hardware
---

### Post by teo_rossi on 2010-10-11
Hey guys,
I'm running Maverick from its beta release and it worked fine until last week updates. After a reboot Ubuntu gets stuck on a purple screen after the loading splash screen has gone. I have to manually restart my laptop (Vaio VPCCW2C5E) as the keyboard is not responding.

If I run Ubuntu with xorg in failsafe mode the system starts normally, so I guess the problem is with xorg and maybe with nvidia driver (260.19.06). Infact,the log is truncated:

```
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.254] X Protocol Version 11, Revision 0
[    18.254] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    18.254] Current Operating System: Linux matteo-vaio 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64
[    18.254] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=fe1a051b-27ef-43bd-88c8-fbfd8f3d4e7f ro quiet splash
[    18.255] Build Date: 16 September 2010  06:18:41PM
[    18.255] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    18.255] Current version of pixman: 0.18.4
[    18.255] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.255] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.255] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 14:43:25 2010
[    18.377] (==) Using config file: "/etc/X11/xorg.conf"
[    18.377] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.713] (==) ServerLayout "Default Layout"
[    18.713] (**) |-->Screen "Default Screen" (0)
[    18.713] (**) |   |-->Monitor "Monitor0"
[    18.728] (**) |   |-->Device "Device0"
[    18.728] (==) Automatically adding devices
[    18.728] (==) Automatically enabling devices
[    18.910] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.910] 	Entry deleted from font path.
[    19.091] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.091] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.091] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.092] (II) Loader magic: 0x7d0200
[    19.092] (II) Module ABI versions:
[    19.092] 	X.Org ANSI C Emulation: 0.4
[    19.092] 	X.Org Video Driver: 8.0
[    19.092] 	X.Org XInput driver : 11.0
[    19.092] 	X.Org Server Extension : 4.0
[    19.093] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9072 rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    19.093] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.093] (II) LoadModule: "extmod"
[    19.184] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.283] (II) Module extmod: vendor="X.Org Foundation"
[    19.283] 	compiled for 1.9.0, module version = 1.0.0
[    19.283] 	Module class: X.Org Server Extension
[    19.283] 	ABI class: X.Org Server Extension, version 4.0
[    19.283] (II) Loading extension MIT-SCREEN-SAVER
[    19.283] (II) Loading extension XFree86-VidModeExtension
[    19.283] (II) Loading extension XFree86-DGA
[    19.283] (II) Loading extension DPMS
[    19.283] (II) Loading extension XVideo
[    19.283] (II) Loading extension XVideo-MotionCompensation
[    19.283] (II) Loading extension X-Resource
[    19.283] (II) LoadModule: "dbe"
[    19.283] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.299] (II) Module dbe: vendor="X.Org Foundation"
[    19.299] 	compiled for 1.9.0, module version = 1.0.0
[    19.299] 	Module class: X.Org Server Extension
[    19.299] 	ABI class: X.Org Server Extension, version 4.0
[    19.299] (II) Loading extension DOUBLE-BUFFER
[    19.299] (II) LoadModule: "glx"
[    19.299] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    20.834] (II) Module glx: vendor="NVIDIA Corporation"
[    20.853] 	compiled for 4.0.2, module version = 1.0.0
[    20.853] 	Module class: X.Org Server Extension
[    20.853] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    20.853] (II) Loading extension GLX
[    20.853] (II) LoadModule: "record"
[    20.853] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.864] (II) Module record: vendor="X.Org Foundation"
[    20.864] 	compiled for 1.9.0, module version = 1.13.0
[    20.864] 	Module class: X.Org Server Extension
[    20.864] 	ABI class: X.Org Server Extension, version 4.0
[    20.864] (II) Loading extension RECORD
[    20.864] (II) LoadModule: "dri"
[    20.864] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.877] (II) Module dri: vendor="X.Org Foundation"
[    20.877] 	compiled for 1.9.0, module version = 1.0.0
[    20.877] 	ABI class: X.Org Server Extension, version 4.0
[    20.877] (II) Loading extension XFree86-DRI
[    20.877] (II) LoadModule: "dri2"
[    20.877] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.890] (II) Module dri2: vendor="X.Org Foundation"
[    20.890] 	compiled for 1.9.0, module version = 1.2.0
[    20.890] 	ABI class: X.Org Server Extension, version 4.0
[    20.890] (II) Loading extension DRI2
[    20.890] (II) LoadModule: "nvidia"
[    20.890] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.047] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.047] 	compiled for 4.0.2, module version = 1.0.0
[    21.047] 	Module class: X.Org Video Driver
[    21.060] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    21.060] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.060] (++) using VT number 7

[    21.062] (II) Loading sub module "fb"
[    21.062] (II) LoadModule: "fb"
[    21.062] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.084] (II) Module fb: vendor="X.Org Foundation"
[    21.095] 	compiled for 1.9.0, module version = 1.0.0
[    21.095] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.095] (II) Loading sub module "wfb"
[    21.095] (II) LoadModule: "wfb"
[    21.223] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.313] (II) Module wfb: vendor="X.Org Foundation"
[    21.313] 	compiled for 1.9.0, module version = 1.0.0
[    21.313] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.313] (II) Loading sub module "ramdac"
[    21.313] (II) LoadModule: "ramdac"
[    21.313] (II) Module "ramdac" already built-in
[    21.314] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    21.314] (==) NVIDIA(0): RGB weight 888
[    21.314] (==) NVIDIA(0): Default visual is TrueColor
[    21.314] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.447] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.447] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.447] (II) NVIDIA(0):     enabled.

```

I couldn't see any error messages in dmesg or syslog, but if you need any other info I will provide it.

---

### Post by johnsto on 2010-10-22
> **teo_rossi said:**
> If I run Ubuntu with xorg in failsafe mode the system starts normally, so I guess the problem is with xorg and maybe with nvidia driver (260.19.06). Infact,the log is truncated:

I had the same issue. Switching to the 256.53 drivers fixed it for me. You can get them from nVidia's site here:
[http://www.nvidia.co.uk/object/linux-display-amd64-256.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-256.53-driver-uk.html)

---

### Post by teo_rossi on 2010-10-22
Yes I fixed the problem the same way. I filed a bug on launchpad but nobody read it.

---

### Post by PaulW21781 on 2010-10-23
Having exactly the same issue with my new laptop too, running the 260.19 driver set in Maverick (fresh install I might add), it hangs booting into X, but failsafe works fine.  My log is also the same as above:

```
[    15.735] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.735] X Protocol Version 11, Revision 0
[    15.735] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    15.735] Current Operating System: Linux paulw-VPCF12M0E 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[    15.735] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=f43545c6-d07d-4c8c-a076-8eb5fa474567 ro i8042.nopnp nouveau.modeset=0 quiet splash
[    15.735] Build Date: 16 September 2010  06:18:41PM
[    15.735] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    15.735] Current version of pixman: 0.18.4
[    15.735]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.735] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.735] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 23 15:27:12 2010
[    15.736] (==) Using config file: "/etc/X11/xorg.conf"
[    15.736] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.768] (==) No Layout section.  Using the first Screen section.
[    15.771] (**) |-->Screen "Default Screen" (0)
[    15.771] (**) |   |-->Monitor "<default monitor>"
[    15.772] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    15.772] (**) |   |-->Device "Default Device"
[    15.772] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    15.772] (==) Automatically adding devices
[    15.772] (==) Automatically enabling devices
[    15.772] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.772]     Entry deleted from font path.
[    15.772] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.772] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.772] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.772] (II) Loader magic: 0x7d0200
[    15.772] (II) Module ABI versions:
[    15.772]     X.Org ANSI C Emulation: 0.4
[    15.772]     X.Org Video Driver: 8.0
[    15.772]     X.Org XInput driver : 11.0
[    15.772]     X.Org Server Extension : 4.0
[    15.773] (--) PCI:*(0:1:0:0) 10de:0a29:104d:9067 rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    15.773] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.773] (II) "extmod" will be loaded by default.
[    15.773] (II) "dbe" will be loaded by default.
[    15.773] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    15.773] (II) "record" will be loaded by default.
[    15.773] (II) "dri" will be loaded by default.
[    15.773] (II) "dri2" will be loaded by default.
[    15.773] (II) LoadModule: "glx"
[    15.804] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    16.441] (II) Module glx: vendor="NVIDIA Corporation"
[    16.450]     compiled for 4.0.2, module version = 1.0.0
[    16.450]     Module class: X.Org Server Extension
[    16.450] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    16.450] (II) Loading extension GLX
[    16.450] (II) LoadModule: "extmod"
[    16.459] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.459] (II) Module extmod: vendor="X.Org Foundation"
[    16.459]     compiled for 1.9.0, module version = 1.0.0
[    16.459]     Module class: X.Org Server Extension
[    16.459]     ABI class: X.Org Server Extension, version 4.0
[    16.459] (II) Loading extension MIT-SCREEN-SAVER
[    16.459] (II) Loading extension XFree86-VidModeExtension
[    16.459] (II) Loading extension XFree86-DGA
[    16.459] (II) Loading extension DPMS
[    16.459] (II) Loading extension XVideo
[    16.459] (II) Loading extension XVideo-MotionCompensation
[    16.459] (II) Loading extension X-Resource
[    16.459] (II) LoadModule: "dbe"
[    16.459] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.460] (II) Module dbe: vendor="X.Org Foundation"
[    16.460]     compiled for 1.9.0, module version = 1.0.0
[    16.460]     Module class: X.Org Server Extension
[    16.460]     ABI class: X.Org Server Extension, version 4.0
[    16.460] (II) Loading extension DOUBLE-BUFFER
[    16.460] (II) LoadModule: "record"
[    16.460] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.460] (II) Module record: vendor="X.Org Foundation"
[    16.460]     compiled for 1.9.0, module version = 1.13.0
[    16.460]     Module class: X.Org Server Extension
[    16.460]     ABI class: X.Org Server Extension, version 4.0
[    16.460] (II) Loading extension RECORD
[    16.460] (II) LoadModule: "dri"
[    16.460] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.460] (II) Module dri: vendor="X.Org Foundation"
[    16.460]     compiled for 1.9.0, module version = 1.0.0
[    16.460]     ABI class: X.Org Server Extension, version 4.0
[    16.460] (II) Loading extension XFree86-DRI
[    16.460] (II) LoadModule: "dri2"
[    16.461] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.461] (II) Module dri2: vendor="X.Org Foundation"
[    16.461]     compiled for 1.9.0, module version = 1.2.0
[    16.461]     ABI class: X.Org Server Extension, version 4.0
[    16.461] (II) Loading extension DRI2
[    16.461] (II) LoadModule: "nvidia"
[    16.461] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.556] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.558]     compiled for 4.0.2, module version = 1.0.0
[    16.558]     Module class: X.Org Video Driver
[    16.595] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    16.595] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.595] (++) using VT number 7

[    16.597] (II) Loading sub module "fb"
[    16.597] (II) LoadModule: "fb"
[    16.598] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.598] (II) Module fb: vendor="X.Org Foundation"
[    16.598]     compiled for 1.9.0, module version = 1.0.0
[    16.598]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.598] (II) Loading sub module "wfb"
[    16.598] (II) LoadModule: "wfb"
[    16.598] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.598] (II) Module wfb: vendor="X.Org Foundation"
[    16.598]     compiled for 1.9.0, module version = 1.0.0
[    16.598]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.598] (II) Loading sub module "ramdac"
[    16.598] (II) LoadModule: "ramdac"
[    16.598] (II) Module "ramdac" already built-in
[    16.604] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    16.604] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    16.604] (==) NVIDIA(0): RGB weight 888
[    16.604] (==) NVIDIA(0): Default visual is TrueColor
[    16.604] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.604] (**) NVIDIA(0): Option "NoLogo" "True"
[    16.604] (**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0"
[    16.604] (**) NVIDIA(0): Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
[    16.605] (**) NVIDIA(0): Enabling RENDER acceleration
[    16.605] (**) NVIDIA(0): ConnectedMonitor string: "DFP-0"
[    16.605] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    16.605] (II) NVIDIA(0):     enabled.
```Appears to hang after saying about GLX, yada yada yada...

Going to remove nvidia-current and switch to the 256.53 set as suggested...

Laptop is a Sony Vaio VPCF12M0E for reference, 330M GT Nvidia.

*edit*

I can confirm, downloading and installing 256.53 drivers from Nvidia's website worked for me :)

---

