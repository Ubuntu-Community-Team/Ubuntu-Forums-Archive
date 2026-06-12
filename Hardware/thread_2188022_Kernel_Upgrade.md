---
title: "Kernel Upgrade"
date: 2013-11-15
forum: Hardware
---

### Post by yusufelkilani on 2013-11-15
Hello,

Using 12.04 here with AMD hybrid graphics. Updated from 3.2 kernel to 3.12 and things went downhill. If I boot into the new kernel, it will boot into a X-less console and I can't start X there. Here is the X log.
```
[    42.355] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    42.355] X Protocol Version 11, Revision 0
[    42.355] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    42.355] Current Operating System: Linux Monster 3.12.0-031200-generic #201311071835 SMP Thu Nov 7 23:36:07 UTC 2013 x86_64
[    42.355] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.0-031200-generic root=UUID=e2100f45-30b3-4185-9607-766097571681 ro quiet splash vt.handoff=7
[    42.355] Build Date: 16 October 2013  04:41:23PM
[    42.355] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    42.355] Current version of pixman: 0.24.4
[    42.355]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    42.355] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    42.355] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 15 10:32:08 2013
[    42.355] (==) Using config file: "/etc/X11/xorg.conf"
[    42.355] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    42.355] (==) ServerLayout "aticonfig Layout"
[    42.355] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    42.355] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    42.356] (**) |   |-->Device "aticonfig-Device[0]-0"
[    42.356] (==) Automatically adding devices
[    42.356] (==) Automatically enabling devices
[    42.356] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    42.356]     Entry deleted from font path.
[    42.356] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    42.356]     Entry deleted from font path.
[    42.356] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    42.356]     Entry deleted from font path.
[    42.356] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    42.356]     Entry deleted from font path.
[    42.356] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    42.356]     Entry deleted from font path.
[    42.494] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    42.495]     Entry deleted from font path.
[    42.495]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    42.495] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    42.495] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    42.495] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    42.495] (II) Loader magic: 0x7fcb7c537b00
[    42.495] (II) Module ABI versions:
[    42.495]     X.Org ANSI C Emulation: 0.4
[    42.495]     X.Org Video Driver: 11.0
[    42.495]     X.Org XInput driver : 16.0
[    42.495]     X.Org Server Extension : 6.0
[    42.495] (--) PCI:*(0:0:2:0) 8086:0116:103c:1670 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005000/64
[    42.495] (--) PCI: (0:1:0:0) 1002:6760:103c:1670 rev 0, Mem @ 0xa0000000/268435456, 0xc2600000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    42.495] (II) Open ACPI successful (/var/run/acpid.socket)
[    42.495] (II) "extmod" will be loaded by default.
[    42.495] (II) "dbe" will be loaded by default.
[    42.495] (II) "glx" will be loaded by default.
[    42.495] (II) "record" will be loaded by default.
[    42.495] (II) "dri" will be loaded by default.
[    42.495] (II) "dri2" will be loaded by default.
[    42.495] (II) LoadModule: "extmod"
[    42.702] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    42.702] (II) Module extmod: vendor="X.Org Foundation"
[    42.702]     compiled for 1.11.3, module version = 1.0.0
[    42.702]     Module class: X.Org Server Extension
[    42.702]     ABI class: X.Org Server Extension, version 6.0
[    42.702] (II) Loading extension MIT-SCREEN-SAVER
[    42.702] (II) Loading extension XFree86-VidModeExtension
[    42.702] (II) Loading extension XFree86-DGA
[    42.702] (II) Loading extension DPMS
[    42.702] (II) Loading extension XVideo
[    42.702] (II) Loading extension XVideo-MotionCompensation
[    42.702] (II) Loading extension X-Resource
[    42.702] (II) LoadModule: "dbe"
[    42.702] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    42.702] (II) Module dbe: vendor="X.Org Foundation"
[    42.703]     compiled for 1.11.3, module version = 1.0.0
[    42.703]     Module class: X.Org Server Extension
[    42.703]     ABI class: X.Org Server Extension, version 6.0
[    42.703] (II) Loading extension DOUBLE-BUFFER
[    42.703] (II) LoadModule: "glx"
[    42.703] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    42.703] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    42.703]     compiled for 6.9.0, module version = 1.0.0
[    42.703] (II) Loading extension GLX
[    42.703] (II) LoadModule: "record"
[    42.704] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    42.704] (II) Module record: vendor="X.Org Foundation"
[    42.704]     compiled for 1.11.3, module version = 1.13.0
[    42.704]     Module class: X.Org Server Extension
[    42.704]     ABI class: X.Org Server Extension, version 6.0
[    42.704] (II) Loading extension RECORD
[    42.704] (II) LoadModule: "dri"
[    42.704] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    42.704] (II) Module dri: vendor="X.Org Foundation"
[    42.704]     compiled for 1.11.3, module version = 1.0.0
[    42.704]     ABI class: X.Org Server Extension, version 6.0
[    42.704] (II) Loading extension XFree86-DRI
[    42.704] (II) LoadModule: "dri2"
[    42.705] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    42.705] (II) Module dri2: vendor="X.Org Foundation"
[    42.705]     compiled for 1.11.3, module version = 1.2.0
[    42.705]     ABI class: X.Org Server Extension, version 6.0
[    42.705] (II) Loading extension DRI2
[    42.705] (II) LoadModule: "fglrx"
[    42.705] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    42.718] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    42.718]     compiled for 1.4.99.906, module version = 9.1.11
[    42.718]     Module class: X.Org Video Driver
[    42.718] (II) Loading sub module "fglrxdrm"
[    42.718] (II) LoadModule: "fglrxdrm"
[    42.718] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    42.718] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    42.718]     compiled for 1.4.99.906, module version = 9.1.11
[    42.718] (II) AMD Proprietary Linux Driver Version Identifier:9.01.11
[    42.718] (II) AMD Proprietary Linux Driver Release Identifier: 9.012                                
[    42.718] (II) AMD Proprietary Linux Driver Build Date: Dec 19 2012 14:41:10
[    42.718] (++) using VT number 7

[    42.719] (WW) Falling back to old probe method for fglrx
[    42.722] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    42.724] ukiDynamicMajor: failed to open /proc/ati/major
[    42.724] ukiDynamicMajor: failed to open /proc/ati/major
[    42.725] (--) Chipset Supported AMD Graphics Processor (0x6760) found
[    42.725] (II) fglrx: intel VGA device detected, load intel driver.
[    42.725] (II) LoadModule: "intel"
[    42.725] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    42.725] (II) Module intel: vendor="X.Org Foundation"
[    42.725]     compiled for 1.11.3, module version = 2.17.0
[    42.725]     Module class: X.Org Video Driver
[    42.725]     ABI class: X.Org Video Driver, version 11.0
[    42.725] (WW) PowerXpress feature is not supported
[    42.725] (EE) this is a Muxless PX A+I platform, we doesn't supported it
[    42.725] (EE) No devices detected.
[    42.725] (==) Matched intel as autoconfigured driver 0
[    42.725] (==) Matched vesa as autoconfigured driver 1
[    42.725] (==) Matched fbdev as autoconfigured driver 2
[    42.725] (==) Assigned the driver to the xf86ConfigLayout
[    42.725] (II) LoadModule: "intel"
[    42.726] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    42.726] (II) Module intel: vendor="X.Org Foundation"
[    42.726]     compiled for 1.11.3, module version = 2.17.0
[    42.726]     Module class: X.Org Video Driver
[    42.726]     ABI class: X.Org Video Driver, version 11.0
[    42.726] (II) UnloadModule: "intel"
[    42.726] (II) Unloading intel
[    42.726] (II) Failed to load module "intel" (already loaded, 32715)
[    42.726] (II) LoadModule: "vesa"
[    42.726] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    42.944] (II) Module vesa: vendor="X.Org Foundation"
[    42.944]     compiled for 1.11.3, module version = 2.3.0
[    42.944]     Module class: X.Org Video Driver
[    42.944]     ABI class: X.Org Video Driver, version 11.0
[    42.944] (II) LoadModule: "fbdev"
[    42.945] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    42.951] (II) Module fbdev: vendor="X.Org Foundation"
[    42.951]     compiled for 1.11.3, module version = 0.4.2
[    42.951]     ABI class: X.Org Video Driver, version 11.0
[    42.951] (II) AMD Proprietary Linux Driver Version Identifier:9.01.11
[    42.951] (II) AMD Proprietary Linux Driver Release Identifier: 9.012                                
[    42.951] (II) AMD Proprietary Linux Driver Build Date: Dec 19 2012 14:41:10
[    42.951] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[    42.952] (II) VESA: driver for VESA chipsets: vesa
[    42.952] (II) FBDEV: driver for framebuffer: fbdev
[    42.952] (++) using VT number 7

[    42.952] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    42.952] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    42.952] (WW) Falling back to old probe method for fglrx
[    42.952] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    42.952] (WW) Falling back to old probe method for vesa
[    42.952] (WW) Falling back to old probe method for fbdev
[    42.952] (EE) No devices detected.
[    42.952] 
Fatal server error:
[    42.952] no screens found
[    42.952] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    42.952] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    42.952] 


```

I've tried to generate a new x config file, but that didn't help either. 3.2 is running fine at the moment, it's just the latest kernel. Any ideas?

---

### Post by yusufelkilani on 2013-11-16
Bump

---

