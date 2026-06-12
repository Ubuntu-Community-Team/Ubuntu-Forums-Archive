---
title: "ASUS N43J installed nvidia driver and X don't work"
date: 2011-03-03
forum: Hardware
---

### Post by opengis on 2011-03-03
After installed Ubuntu 10.10(64-bits), updated nvidia driver. The updating commands:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings 

Then reboot, can't start X windows.

Xorg.0.log&#65306;
[   454.311] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   454.312] X Protocol Version 11, Revision 0
[   454.312] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   454.313] Current Operating System: Linux lee-N43JF 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    454.313] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic  root=UUID=6146931c-d59b-46b9-b361-2374b315a6cb ro quiet splash
[   454.314] Build Date: 16 September 2010  06:18:41PM
[   454.314] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   454.315] Current version of pixman: 0.18.4
[   454.316]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[   454.317] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   454.320] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  2 15:32:39 2011
[   454.321] (==) Using config file: "/etc/X11/xorg.conf"
[   454.322] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   454.323] (==) ServerLayout "Layout0"
[   454.323] (**) |-->Screen "Screen0" (0)
[   454.323] (**) |   |-->Monitor "Monitor0"
[   454.323] (**) |   |-->Device "Device0"
[   454.323] (**) |-->Input Device "Keyboard0"
[   454.323] (**) |-->Input Device "Mouse0"
[   454.323] (==) Automatically adding devices
[   454.323] (==) Automatically enabling devices
[   454.323] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   454.323]     Entry deleted from font path.
[   454.323] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   454.323] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   454.323] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   454.323] (WW) Disabling Keyboard0
[   454.323] (WW) Disabling Mouse0
[   454.323] (II) Loader magic: 0x7d0200
[   454.323] (II) Module ABI versions:
[   454.323]     X.Org ANSI C Emulation: 0.4
[   454.323]     X.Org Video Driver: 8.0
[   454.323]     X.Org XInput driver : 11.0
[   454.323]     X.Org Server Extension : 4.0
[   454.324] (--) PCI:*(0:0:2:0) 8086:0046:1043:1482 rev 24, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
[    454.324] (--) PCI: (0:1:0:0) 10de:0df0:1043:1482 rev 161, Mem @  0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @  0x0000d000/128, BIOS @ 0x????????/524288
[   454.324] (II) Open ACPI successful (/var/run/acpid.socket)
[   454.324] (II) LoadModule: "extmod"
[   454.324] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   454.324] (II) Module extmod: vendor="X.Org Foundation"
[   454.324]     compiled for 1.9.0, module version = 1.0.0
[   454.324]     Module class: X.Org Server Extension
[   454.324]     ABI class: X.Org Server Extension, version 4.0
[   454.324] (II) Loading extension MIT-SCREEN-SAVER
[   454.324] (II) Loading extension XFree86-VidModeExtension
[   454.324] (II) Loading extension XFree86-DGA
[   454.324] (II) Loading extension DPMS
[   454.324] (II) Loading extension XVideo
[   454.324] (II) Loading extension XVideo-MotionCompensation
[   454.324] (II) Loading extension X-Resource
[   454.324] (II) LoadModule: "dbe"
[   454.324] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   454.324] (II) Module dbe: vendor="X.Org Foundation"
[   454.324]     compiled for 1.9.0, module version = 1.0.0
[   454.324]     Module class: X.Org Server Extension
[   454.324]     ABI class: X.Org Server Extension, version 4.0
[   454.324] (II) Loading extension DOUBLE-BUFFER
[   454.324] (II) LoadModule: "glx"
[   454.325] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   454.331] (II) Module glx: vendor="NVIDIA Corporation"
[   454.331]     compiled for 4.0.2, module version = 1.0.0
[   454.331]     Module class: X.Org Server Extension
[   454.331] (II) NVIDIA GLX Module  260.19.36  Tue Jan 18 17:12:12 PST 2011
[   454.331] (II) Loading extension GLX
[   454.331] (II) LoadModule: "record"
[   454.331] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   454.332] (II) Module record: vendor="X.Org Foundation"
[   454.332]     compiled for 1.9.0, module version = 1.13.0
[   454.332]     Module class: X.Org Server Extension
[   454.332]     ABI class: X.Org Server Extension, version 4.0
[   454.332] (II) Loading extension RECORD
[   454.332] (II) LoadModule: "dri"
[   454.332] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   454.332] (II) Module dri: vendor="X.Org Foundation"
[   454.332]     compiled for 1.9.0, module version = 1.0.0
[   454.332]     ABI class: X.Org Server Extension, version 4.0
[   454.332] (II) Loading extension XFree86-DRI
[   454.332] (II) LoadModule: "dri2"
[   454.332] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   454.332] (II) Module dri2: vendor="X.Org Foundation"
[   454.332]     compiled for 1.9.0, module version = 1.2.0
[   454.332]     ABI class: X.Org Server Extension, version 4.0
[   454.332] (II) Loading extension DRI2
[   454.332] (II) LoadModule: "nvidia"
[   454.332] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   454.333] (II) Module nvidia: vendor="NVIDIA Corporation"
[   454.333]     compiled for 4.0.2, module version = 1.0.0
[   454.333]     Module class: X.Org Video Driver
[   454.669] (II) NVIDIA dlloader X Driver  260.19.36  Tue Jan 18 16:57:32 PST 2011
[   454.669] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   454.669] (--) using VT number 8

[   454.672] (EE) No devices detected.
[   454.672] 
Fatal server error:
[   454.672] no screens found
[   454.672] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
[   454.672] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   454.672] 


What to do?

---

