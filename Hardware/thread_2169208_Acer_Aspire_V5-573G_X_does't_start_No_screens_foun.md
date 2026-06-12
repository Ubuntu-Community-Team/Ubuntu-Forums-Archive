---
title: "Acer Aspire V5-573G: X does't start: No screens found"
date: 2013-08-21
forum: Hardware
---

### Post by highwaychile on 2013-08-21
Hi,

I just bought an Acer Aspire V5-573G with core i5-4200U and NVidia GeForce GT 750M and I'm trying to get ubuntu running. I already solved one problem: When starting the liveusb system  I got "fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver". This could be solved by setting "nomodeset". This way I managed to install Ubuntu.

When starting from the hard drive (also using nomodeset) the graphical interface doesn't work, the last message I see is "init hw failure, initialization failed", but at least I can login at the terminal. When trying to execute startx manually, I get "no screens found":


```

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux Ben 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=59c8b0dd-7cd1-4f40-878d-4df968a795f5 ro nomodeset vt.handoff=7
Build Date: 17 April 2013  10:43:13PM
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 21 08:05:26 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX


Fatal server error:
no screens found
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```


This is my Xorg.0.log:
```

[   455.387] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[   455.387] X Protocol Version 11, Revision 0
[   455.387] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   455.387] Current Operating System: Linux Ben 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64
[   455.387] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=59c8b0dd-7cd1-4f40-878d-4df968a795f5 ro nomodeset vt.handoff=7
[   455.387] Build Date: 17 April 2013  10:43:13PM
[   455.387] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[   455.387] Current version of pixman: 0.28.2
[   455.387]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   455.387] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   455.387] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 21 08:05:26 2013
[   455.388] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   455.388] (==) No Layout section.  Using the first Screen section.
[   455.388] (==) No screen section available. Using defaults.
[   455.388] (**) |-->Screen "Default Screen Section" (0)
[   455.388] (**) |   |-->Monitor "<default monitor>"
[   455.388] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   455.389] (==) Automatically adding devices
[   455.389] (==) Automatically enabling devices
[   455.389] (==) Automatically adding GPU devices
[   455.389] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   455.389]     Entry deleted from font path.
[   455.389] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   455.389] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   455.389] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   455.389] (II) Loader magic: 0x7fa061278d20
[   455.389] (II) Module ABI versions:
[   455.389]     X.Org ANSI C Emulation: 0.4
[   455.389]     X.Org Video Driver: 13.1
[   455.389]     X.Org XInput driver : 18.0
[   455.389]     X.Org Server Extension : 7.0
[   455.391] (--) PCI:*(0:0:2:0) 8086:0a16:1025:079b rev 9, Mem @ 0xb3000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[   455.391] (--) PCI: (0:1:0:0) 10de:0fe4:1025:079b rev 161, Mem @ 0xb2000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128
[   455.391] (II) Open ACPI successful (/var/run/acpid.socket)
[   455.391] Initializing built-in extension Generic Event Extension
[   455.391] Initializing built-in extension SHAPE
[   455.391] Initializing built-in extension MIT-SHM
[   455.391] Initializing built-in extension XInputExtension
[   455.391] Initializing built-in extension XTEST
[   455.391] Initializing built-in extension BIG-REQUESTS
[   455.392] Initializing built-in extension SYNC
[   455.392] Initializing built-in extension XKEYBOARD
[   455.392] Initializing built-in extension XC-MISC
[   455.392] Initializing built-in extension SECURITY
[   455.392] Initializing built-in extension XINERAMA
[   455.392] Initializing built-in extension XFIXES
[   455.392] Initializing built-in extension RENDER
[   455.392] Initializing built-in extension RANDR
[   455.392] Initializing built-in extension COMPOSITE
[   455.392] Initializing built-in extension DAMAGE
[   455.392] Initializing built-in extension MIT-SCREEN-SAVER
[   455.392] Initializing built-in extension DOUBLE-BUFFER
[   455.392] Initializing built-in extension RECORD
[   455.392] Initializing built-in extension DPMS
[   455.392] Initializing built-in extension X-Resource
[   455.392] Initializing built-in extension XVideo
[   455.392] Initializing built-in extension XVideo-MotionCompensation
[   455.392] Initializing built-in extension SELinux
[   455.392] Initializing built-in extension XFree86-VidModeExtension
[   455.392] Initializing built-in extension XFree86-DGA
[   455.392] Initializing built-in extension XFree86-DRI
[   455.392] Initializing built-in extension DRI2
[   455.392] (II) LoadModule: "glx"
[   455.393] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   455.393] (II) Module glx: vendor="X.Org Foundation"
[   455.393]     compiled for 1.13.3, module version = 1.0.0
[   455.393]     ABI class: X.Org Server Extension, version 7.0
[   455.393] (==) AIGLX enabled
[   455.393] Loading extension GLX
[   455.393] (==) Matched intel as autoconfigured driver 0
[   455.393] (==) Matched vesa as autoconfigured driver 1
[   455.393] (==) Matched modesetting as autoconfigured driver 2
[   455.393] (==) Matched fbdev as autoconfigured driver 3
[   455.393] (==) Assigned the driver to the xf86ConfigLayout
[   455.393] (II) LoadModule: "intel"
[   455.393] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   455.394] (II) Module intel: vendor="X.Org Foundation"
[   455.394]     compiled for 1.13.3, module version = 2.21.6
[   455.394]     Module class: X.Org Video Driver
[   455.394]     ABI class: X.Org Video Driver, version 13.1
[   455.394] (II) LoadModule: "vesa"
[   455.394] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   455.394] (II) Module vesa: vendor="X.Org Foundation"
[   455.394]     compiled for 1.12.99.902, module version = 2.3.2
[   455.394]     Module class: X.Org Video Driver
[   455.394]     ABI class: X.Org Video Driver, version 13.0
[   455.394] (II) LoadModule: "modesetting"
[   455.395] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   455.395] (II) Module modesetting: vendor="X.Org Foundation"
[   455.395]     compiled for 1.13.3, module version = 0.7.0
[   455.395]     Module class: X.Org Video Driver
[   455.395]     ABI class: X.Org Video Driver, version 13.1
[   455.395] (II) LoadModule: "fbdev"
[   455.395] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   455.395] (II) Module fbdev: vendor="X.Org Foundation"
[   455.395]     compiled for 1.12.99.902, module version = 0.4.3
[   455.395]     Module class: X.Org Video Driver
[   455.395]     ABI class: X.Org Video Driver, version 13.0
[   455.395] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[   455.396] (II) VESA: driver for VESA chipsets: vesa
[   455.396] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   455.396] (II) FBDEV: driver for framebuffer: fbdev
[   455.396] (--) using VT number 7


[   455.402] (WW) Falling back to old probe method for modesetting
[   455.402] (EE) open /dev/dri/card0: No such file or directory
[   455.402] (WW) Falling back to old probe method for fbdev
[   455.402] (II) Loading sub module "fbdevhw"
[   455.402] (II) LoadModule: "fbdevhw"
[   455.402] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   455.402] (II) Module fbdevhw: vendor="X.Org Foundation"
[   455.402]     compiled for 1.13.3, module version = 0.0.2
[   455.402]     ABI class: X.Org Video Driver, version 13.1
[   455.402] (II) Loading sub module "vbe"
[   455.402] (II) LoadModule: "vbe"
[   455.402] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   455.402] (II) Module vbe: vendor="X.Org Foundation"
[   455.402]     compiled for 1.13.3, module version = 1.1.0
[   455.402]     ABI class: X.Org Video Driver, version 13.1
[   455.402] (II) Loading sub module "int10"
[   455.402] (II) LoadModule: "int10"
[   455.402] (II) Loading /usr/lib/xorg/modules/libint10.so
[   455.402] (II) Module int10: vendor="X.Org Foundation"
[   455.402]     compiled for 1.13.3, module version = 1.0.0
[   455.402]     ABI class: X.Org Video Driver, version 13.1
[   455.402] (II) VESA(0): initializing int10
[   455.402] (EE) VESA(0): V_BIOS address 0x0 out of range
[   455.403] (II) UnloadModule: "vesa"
[   455.403] (II) UnloadSubModule: "int10"
[   455.403] (II) Unloading int10
[   455.403] (II) UnloadSubModule: "vbe"
[   455.403] (II) Unloading vbe
[   455.403] (EE) Screen(s) found, but none have a usable configuration.
[   455.403] 
Fatal server error:
[   455.403] no screens found
[   455.403] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   455.403] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   455.403] (EE) 
[   455.410] Server terminated with error (1). Closing log file.

```


This is what `lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'` prints out:
```

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])

```

So ubuntu only recognizes the intel graphics but not the nvidia one (therefore I didn't try to use bumblebee yet). This isn't a problem for me, as I don't need the NVidia card on linux, intel hd graphics is enough.

Could you help me getting the intel graphics to work? The installer somehow managed to use it, so it has to be possible somehow, but after a lot of time trying it out by myself I've no idea how to proceed :(


Thank you in advance,


highwaychile

---

### Post by Yellow Pasque on 2013-08-21
```
(EE) VESA(0): V_BIOS address 0x0 out of range
```
The VESA driver doesn't seem to like your GPU. Anyway, you would be far better off using Ubuntu 13.10 for such a new system.

---

### Post by highwaychile on 2013-08-26
Hi,

I just tried out 13.10 and it works great (NVidia isn't recognised, but for me this isn't important as the Intel graphics is fast enough)! Just one small thing: After booting the screen is always totally black, so I always have to brighten it up using the keyboard. Is there a way to do this automatically?

Xorg.0.log:
```
[     4.722] X.Org X Server 1.14.2.901 (1.14.3 RC 1)
Release Date: 2013-07-25
[     4.722] X Protocol Version 11, Revision 0
[     4.722] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     4.722] Current Operating System: Linux Ben 3.11.0-3-generic #8-Ubuntu SMP Fri Aug 23 16:49:15 UTC 2013 x86_64
[     4.722] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-3-generic root=UUID=59c7dbcd-9b36-4454-9b14-ceb1a8acc898 ro quiet splash vt.handoff=7
[     4.722] Build Date: 22 August 2013  05:40:13AM
[     4.722] xorg-server 2:1.14.2.901-2ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[     4.723] Current version of pixman: 0.30.2
[     4.723]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.723] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.723] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 26 08:15:12 2013
[     4.724] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.725] (==) No Layout section.  Using the first Screen section.
[     4.725] (==) No screen section available. Using defaults.
[     4.725] (**) |-->Screen "Default Screen Section" (0)
[     4.725] (**) |   |-->Monitor "<default monitor>"
[     4.726] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.726] (==) Automatically adding devices
[     4.726] (==) Automatically enabling devices
[     4.726] (==) Automatically adding GPU devices
[     4.726] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     4.726]     Entry deleted from font path.
[     4.726] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.726] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.726] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.726] (II) Loader magic: 0x7fb973508d20
[     4.726] (II) Module ABI versions:
[     4.726]     X.Org ANSI C Emulation: 0.4
[     4.726]     X.Org Video Driver: 14.1
[     4.726]     X.Org XInput driver : 19.1
[     4.726]     X.Org Server Extension : 7.0
[     4.727] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.728] (--) PCI:*(0:0:2:0) 8086:0a16:1025:079b rev 9, Mem @ 0xb3000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[     4.728] (--) PCI: (0:1:0:0) 10de:0fe4:1025:079b rev 161, Mem @ 0xb2000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128
[     4.728] (II) Open ACPI successful (/var/run/acpid.socket)
[     4.728] Initializing built-in extension Generic Event Extension
[     4.728] Initializing built-in extension SHAPE
[     4.728] Initializing built-in extension MIT-SHM
[     4.728] Initializing built-in extension XInputExtension
[     4.728] Initializing built-in extension XTEST
[     4.728] Initializing built-in extension BIG-REQUESTS
[     4.728] Initializing built-in extension SYNC
[     4.728] Initializing built-in extension XKEYBOARD
[     4.728] Initializing built-in extension XC-MISC
[     4.728] Initializing built-in extension SECURITY
[     4.728] Initializing built-in extension XINERAMA
[     4.728] Initializing built-in extension XFIXES
[     4.728] Initializing built-in extension RENDER
[     4.728] Initializing built-in extension RANDR
[     4.728] Initializing built-in extension COMPOSITE
[     4.728] Initializing built-in extension DAMAGE
[     4.728] Initializing built-in extension MIT-SCREEN-SAVER
[     4.728] Initializing built-in extension DOUBLE-BUFFER
[     4.728] Initializing built-in extension RECORD
[     4.728] Initializing built-in extension DPMS
[     4.728] Initializing built-in extension X-Resource
[     4.728] Initializing built-in extension XVideo
[     4.728] Initializing built-in extension XVideo-MotionCompensation
[     4.728] Initializing built-in extension SELinux
[     4.728] Initializing built-in extension XFree86-VidModeExtension
[     4.728] Initializing built-in extension XFree86-DGA
[     4.728] Initializing built-in extension XFree86-DRI
[     4.728] Initializing built-in extension DRI2
[     4.728] (II) LoadModule: "glx"
[     4.730] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.732] (II) Module glx: vendor="X.Org Foundation"
[     4.732]     compiled for 1.14.2.901, module version = 1.0.0
[     4.732]     ABI class: X.Org Server Extension, version 7.0
[     4.732] (==) AIGLX enabled
[     4.732] Loading extension GLX
[     4.732] (==) Matched intel as autoconfigured driver 0
[     4.732] (==) Matched intel as autoconfigured driver 1
[     4.732] (==) Matched vesa as autoconfigured driver 2
[     4.732] (==) Matched modesetting as autoconfigured driver 3
[     4.732] (==) Matched fbdev as autoconfigured driver 4
[     4.732] (==) Assigned the driver to the xf86ConfigLayout
[     4.732] (II) LoadModule: "intel"
[     4.732] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.735] (II) Module intel: vendor="X.Org Foundation"
[     4.735]     compiled for 1.14.2.901, module version = 2.21.14
[     4.735]     Module class: X.Org Video Driver
[     4.735]     ABI class: X.Org Video Driver, version 14.1
[     4.735] (II) LoadModule: "vesa"
[     4.735] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.736] (II) Module vesa: vendor="X.Org Foundation"
[     4.736]     compiled for 1.14.1, module version = 2.3.2
[     4.736]     Module class: X.Org Video Driver
[     4.736]     ABI class: X.Org Video Driver, version 14.1
[     4.736] (II) LoadModule: "modesetting"
[     4.736] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.736] (II) Module modesetting: vendor="X.Org Foundation"
[     4.736]     compiled for 1.14.1, module version = 0.8.0
[     4.736]     Module class: X.Org Video Driver
[     4.736]     ABI class: X.Org Video Driver, version 14.1
[     4.736] (II) LoadModule: "fbdev"
[     4.737] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.737] (II) Module fbdev: vendor="X.Org Foundation"
[     4.737]     compiled for 1.14.1, module version = 0.4.3
[     4.737]     Module class: X.Org Video Driver
[     4.737]     ABI class: X.Org Video Driver, version 14.1
[     4.737] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[     4.738] (II) VESA: driver for VESA chipsets: vesa
[     4.738] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.738] (II) FBDEV: driver for framebuffer: fbdev
[     4.738] (++) using VT number 7


[     4.739] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.14-4ubuntu2 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[     4.739] (WW) Falling back to old probe method for vesa
[     4.739] (WW) Falling back to old probe method for modesetting
[     4.739] (WW) Falling back to old probe method for fbdev
[     4.739] (II) Loading sub module "fbdevhw"
[     4.739] (II) LoadModule: "fbdevhw"
[     4.740] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.740] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.740]     compiled for 1.14.2.901, module version = 0.0.2
[     4.740]     ABI class: X.Org Video Driver, version 14.1
[     4.741] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     4.741] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     4.741] (==) intel(0): RGB weight 888
[     4.741] (==) intel(0): Default visual is TrueColor
[     4.741] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[     4.741] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     4.741] (**) intel(0): Framebuffer tiled
[     4.741] (**) intel(0): Pixmaps tiled
[     4.741] (**) intel(0): "Tear free" disabled
[     4.741] (**) intel(0): Forcing per-crtc-pixmaps? no
[     4.741] (II) intel(0): Output eDP1 has no monitor section
[     4.741] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[     4.741] (II) intel(0): Output DP1 has no monitor section
[     4.741] (II) intel(0): Output HDMI1 has no monitor section
[     4.741] (II) intel(0): Output DP2 has no monitor section
[     4.741] (II) intel(0): Output HDMI2 has no monitor section
[     4.741] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[     4.741] (==) intel(0): DPI set to (96, 96)
[     4.741] (II) Loading sub module "dri2"
[     4.741] (II) LoadModule: "dri2"
[     4.741] (II) Module "dri2" already built-in
[     4.741] (II) UnloadModule: "vesa"
[     4.741] (II) Unloading vesa
[     4.741] (II) UnloadModule: "modesetting"
[     4.741] (II) Unloading modesetting
[     4.742] (II) UnloadModule: "fbdev"
[     4.742] (II) Unloading fbdev
[     4.742] (II) UnloadSubModule: "fbdevhw"
[     4.742] (II) Unloading fbdevhw
[     4.742] (==) Depth 24 pixmap format is 32 bpp
[     4.743] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[     4.743] (==) intel(0): Backing store disabled
[     4.743] (==) intel(0): Silken mouse enabled
[     4.743] (II) intel(0): HW Cursor enabled
[     4.743] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.744] (==) intel(0): DPMS enabled
[     4.745] (II) intel(0): [DRI2] Setup complete
[     4.745] (II) intel(0): [DRI2]   DRI driver: i965
[     4.745] (II) intel(0): direct rendering: DRI2 Enabled
[     4.745] (==) intel(0): hotplug detection: "enabled"
[     4.745] (--) RandR disabled
[     4.750] (II) SELinux: Disabled on system
[     4.762] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.762] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.762] (II) AIGLX: enabled GLX_ARB_create_context
[     4.762] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     4.762] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     4.762] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.762] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.762] (II) AIGLX: Loaded and initialized i965
[     4.762] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.765] (II) intel(0): switch to mode 1920x1080@60.2 on pipe 0 using eDP1, position (0, 0), rotation normal
[     4.796] (II) intel(0): Setting screen physical size to 508 x 285
[     4.805] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.807] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     4.807] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.807] (II) LoadModule: "evdev"
[     4.808] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.809] (II) Module evdev: vendor="X.Org Foundation"
[     4.809]     compiled for 1.14.1, module version = 2.7.3
[     4.809]     Module class: X.Org XInput Driver
[     4.809]     ABI class: X.Org XInput driver, version 19.1
[     4.809] (II) Using input driver 'evdev' for 'Power Button'
[     4.809] (**) Power Button: always reports core events
[     4.809] (**) evdev: Power Button: Device: "/dev/input/event3"
[     4.809] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.809] (--) evdev: Power Button: Found keys
[     4.809] (II) evdev: Power Button: Configuring as keyboard
[     4.809] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     4.809] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.809] (**) Option "xkb_rules" "evdev"
[     4.809] (**) Option "xkb_model" "pc105"
[     4.809] (**) Option "xkb_layout" "de"
[     4.811] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[     4.812] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[     4.812] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.812] (II) Using input driver 'evdev' for 'Video Bus'
[     4.812] (**) Video Bus: always reports core events
[     4.812] (**) evdev: Video Bus: Device: "/dev/input/event11"
[     4.812] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.812] (--) evdev: Video Bus: Found keys
[     4.812] (II) evdev: Video Bus: Configuring as keyboard
[     4.812] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input11/event11"
[     4.812] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     4.812] (**) Option "xkb_rules" "evdev"
[     4.812] (**) Option "xkb_model" "pc105"
[     4.812] (**) Option "xkb_layout" "de"
[     4.812] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[     4.812] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.812] (II) Using input driver 'evdev' for 'Video Bus'
[     4.812] (**) Video Bus: always reports core events
[     4.812] (**) evdev: Video Bus: Device: "/dev/input/event10"
[     4.812] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.812] (--) evdev: Video Bus: Found keys
[     4.812] (II) evdev: Video Bus: Configuring as keyboard
[     4.812] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/LNXVIDEO:00/input/input10/event10"
[     4.812] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[     4.812] (**) Option "xkb_rules" "evdev"
[     4.812] (**) Option "xkb_model" "pc105"
[     4.813] (**) Option "xkb_layout" "de"
[     4.813] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.813] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.813] (II) Using input driver 'evdev' for 'Power Button'
[     4.813] (**) Power Button: always reports core events
[     4.813] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.813] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.813] (--) evdev: Power Button: Found keys
[     4.813] (II) evdev: Power Button: Configuring as keyboard
[     4.813] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     4.813] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[     4.813] (**) Option "xkb_rules" "evdev"
[     4.813] (**) Option "xkb_model" "pc105"
[     4.813] (**) Option "xkb_layout" "de"
[     4.813] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     4.813] (II) No input driver specified, ignoring this device.
[     4.813] (II) This device may have been added with another device file.
[     4.813] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     4.813] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     4.813] (II) Using input driver 'evdev' for 'Sleep Button'
[     4.813] (**) Sleep Button: always reports core events
[     4.813] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     4.813] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     4.813] (--) evdev: Sleep Button: Found keys
[     4.813] (II) evdev: Sleep Button: Configuring as keyboard
[     4.813] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[     4.813] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[     4.813] (**) Option "xkb_rules" "evdev"
[     4.813] (**) Option "xkb_model" "pc105"
[     4.813] (**) Option "xkb_layout" "de"
[     4.814] (II) config/udev: Adding drm device (/dev/dri/card0)
[     4.814] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     4.814] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=8 (/dev/input/event12)
[     4.814] (II) No input driver specified, ignoring this device.
[     4.814] (II) This device may have been added with another device file.
[     4.814] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event13)
[     4.814] (II) No input driver specified, ignoring this device.
[     4.814] (II) This device may have been added with another device file.
[     4.814] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event14)
[     4.814] (II) No input driver specified, ignoring this device.
[     4.814] (II) This device may have been added with another device file.
[     4.814] (II) config/udev: Adding input device HD WebCam (/dev/input/event5)
[     4.814] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[     4.814] (II) Using input driver 'evdev' for 'HD WebCam'
[     4.814] (**) HD WebCam: always reports core events
[     4.814] (**) evdev: HD WebCam: Device: "/dev/input/event5"
[     4.814] (--) evdev: HD WebCam: Vendor 0x64e Product 0xe330
[     4.814] (--) evdev: HD WebCam: Found keys
[     4.814] (II) evdev: HD WebCam: Configuring as keyboard
[     4.814] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input5/event5"
[     4.814] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 11)
[     4.814] (**) Option "xkb_rules" "evdev"
[     4.814] (**) Option "xkb_model" "pc105"
[     4.815] (**) Option "xkb_layout" "de"
[     4.815] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event8)
[     4.815] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[     4.815] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[     4.815] (**) Logitech USB Optical Mouse: always reports core events
[     4.815] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event8"
[     4.815] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc018
[     4.815] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[     4.815] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[     4.815] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[     4.815] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[     4.815] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[     4.815] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[     4.815] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[     4.815] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.815] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input8/event8"
[     4.815] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 12)
[     4.815] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[     4.815] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[     4.815] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[     4.815] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[     4.815] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[     4.815] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[     4.815] (II) No input driver specified, ignoring this device.
[     4.815] (II) This device may have been added with another device file.
[     4.815] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[     4.815] (II) No input driver specified, ignoring this device.
[     4.815] (II) This device may have been added with another device file.
[     4.816] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     4.816] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.816] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     4.816] (**) AT Translated Set 2 keyboard: always reports core events
[     4.816] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     4.816] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     4.816] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     4.816] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     4.816] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     4.816] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[     4.816] (**) Option "xkb_rules" "evdev"
[     4.816] (**) Option "xkb_model" "pc105"
[     4.816] (**) Option "xkb_layout" "de"
[     4.816] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[     4.816] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     4.816] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     4.816] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     4.816] (II) LoadModule: "synaptics"
[     4.816] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     4.817] (II) Module synaptics: vendor="X.Org Foundation"
[     4.817]     compiled for 1.14.2, module version = 1.7.1
[     4.817]     Module class: X.Org XInput Driver
[     4.817]     ABI class: X.Org XInput driver, version 19.1
[     4.817] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     4.817] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.817] (**) Option "Device" "/dev/input/event9"
[     4.840] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5662 (res 42)
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4656 (res 46)
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     4.840] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     4.840] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.840] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.856] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[     4.856] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[     4.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     4.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     4.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[     4.856] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     4.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     4.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     4.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     4.856] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.856] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[     4.856] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     4.858] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[     4.858] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     4.858] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[     4.858] (**) Acer WMI hotkeys: always reports core events
[     4.858] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[     4.858] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[     4.858] (--) evdev: Acer WMI hotkeys: Found keys
[     4.858] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[     4.858] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[     4.858] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 15)
[     4.858] (**) Option "xkb_rules" "evdev"
[     4.858] (**) Option "xkb_model" "pc105"
[     4.858] (**) Option "xkb_layout" "de"
[     4.858] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event7)
[     4.858] (II) No input driver specified, ignoring this device.
[     4.858] (II) This device may have been added with another device file.
[     4.858] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[     4.858] (II) No input driver specified, ignoring this device.
[     4.858] (II) This device may have been added with another device file.
[     5.311] (II) intel(0): EDID vendor "AUO", prod id 4845
[     5.311] (II) intel(0): Printing DDC gathered Modelines:
[     5.311] (II) intel(0): Modeline "1920x1080"x0.0  141.40  1920 1968 2068 2112  1080 1088 1102 1112 -hsync -vsync (67.0 kHz eP)
[     6.833] (II) XKB: reuse xkmfile /var/lib/xkb/server-81907AB388B478D711E6423DD8B0048239BE0CB6.xkm
[    10.957] (II) XKB: reuse xkmfile /var/lib/xkb/server-CD2F7BBA0F9DFC3D8E49D1C6E62F6093973B5D74.xkm
```

```
ben@Ben:~$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Kernel driver in use: i915
```

---

### Post by vladimir2 on 2013-09-01
hi, this script help you
just set LEVEL_AC and LEVEL_BAT whit your best value
save this script in to /etc/pm/power.d/ 

#!/bin/sh
# /etc/pm/power.d/backlight 
# set backlight brightness depending on power source
LEVEL_AC=70
LEVEL_BAT=40 
BRIGHT=/sys/class/backlight/acpi_video0/brightness
case "$1" in     
    true)  level=$LEVEL_BAT ;;      
    false) level=$LEVEL_AC ;;
    *) exit 0 # invalid argument
esac
[ "$(cat $BRIGHT)" != "$level" ] && echo -n $level > $BRIGHT
exit 0

---

### Post by frekja on 2013-09-12
I also have an Aspire V5-573G 54208g50aii and thought I'd share what I've found: running Saucy 13.10 beta, everything works except the Nvidia 750m, bluetooth, and screen brightness on startup. I've tried using bumblebee, which doesn't recognise the Nvidia card, but if I've understood the thread at [https://bugzilla.kernel.org/show_bug.cgi?id=60829](https://bugzilla.kernel.org/show_bug.cgi?id=60829) correctly, there will be a fix in kernel 3.12. The bluetooth problem relates to a known bug ([https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033)) for which there is a partial workaround. I haven't yet tried the script in post #4 (thanks vladimir2!) but will do so - at the moment, I'm just pressing fn-right on startup. Does anyone know why the brightness control might not be working by default?

---

