---
title: "LightDM-(EE) no screens found: No GUI after Update from 12.04.5 LTS to 14.04.1"
date: 2014-10-09
forum: Hardware
---

### Post by AstroPhysik on 2014-10-09
Hello,

On 27.09.14 i did an update from ubuntu 12.04.5 LTS   (64 Bit Kernel 3.11.26-generic #45)    to 14.04.1    (Kernel 3.13.0-36 generic x86_64).
(Before the distupgrade,  i tested the laptop with a live dvd and installed all the 12.04 updates..)

After aprox 6 hours and a restart i cannot login into the GUI anymore. I ccan login into a terminal and after **startx**:

> 
Initialializing...
Initialializing...
Initialializing...
Initialializing built in extension DRI2
Loading Extension GLX
(EE)
Fatal Server Error:
(EE) no screens found(EE)
(EE)
Please consult the X.Org Foundation Support
(EE) please check the log in file "/var/log/Xorg.0.log"....
(EE)
(EE) Server terminated with error (1). Closing Log File
xinit: giving up
xinit: unable to connect to x server: Connectino refused
xinit: server error


**lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2  **
> 01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470] [1002:95c4]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Kernel driver in use: radeon

**xrandr --prop** says: **cannot open Display**

I foud out that on 14.04 my AMD/ATI RV620/M82 **Mobility Radeon HD 3450/3470** is not supported anymore:

> Ubuntu 14.04
    AMD FireStream: 9350, 9270, 9250, 9170
    **AMD Mobility Radeon HD**: 8xxxM, 7xxxM, 6xxxM, 5xxx
    AMD Radeon HD: Rx 2xx, 8xxx, 7xxx, 6xxx, 5xxx

Ubuntu 12.04, 12.04.1 (Catalyst 12.4 - 8.960)
    AMD FireStream: 9350, 9270, 9250, 9170
    **AMD Mobility Radeon HD**: 6xxxM, 6xxx, 6xxxG, 5xxx, 4xxx, **3xxx**, 2xxx sowie AMD PowerXpress
    AMD Radeon HD: 7xxx, 7xxxD, 6xxx, 6xxxD, 5xxx, 4xxx, 3xxx, 2xxx
    AMD Radeon: 3000, 3100, 3200



How can i fix this?


The log file says some fonts does not exist..

>    102.424] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   102.424] X Protocol Version 11, Revision 0
[   102.424] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[   102.425] Current Operating System: Linux user-HP-Pavilion-dv5-Notebook-PC 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64
[   102.425] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=25fe1b8a-50c6-4045-b9bd-a5048e4657e7 ro splash
[   102.425] Build Date: 30 July 2014  12:21:54AM
[   102.425] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   102.425] Current version of pixman: 0.30.2
[   102.425]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   102.425] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   102.426] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 28 05:48:06 2014
[   102.426] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   102.426] (==) No Layout section.  Using the first Screen section.
[   102.426] (==) No screen section available. Using defaults.
[   102.426] (**) |-->Screen "Default Screen Section" (0)
[   102.426] (**) |   |-->Monitor "<default monitor>"
[   102.427] **(==) No monitor specified for screen "Default Screen Section".**
    Using a default monitor configuration.
[   102.427] (==) Automatically adding devices
[   102.427] (==) Automatically enabling devices
[   102.427] (==) Automatically adding GPU devices
[   102.427] [B](WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   102.427]     Entry deleted from font path.
[   102.427] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   102.427]     Entry deleted from font path.
[   102.427] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   102.427]     Entry deleted from font path.
[   102.427] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   102.427]     Entry deleted from font path.
[   102.427] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   102.427]     Entry deleted from font path.[/B]
[   102.427] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   102.427] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   102.427] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   102.427] (II) Loader magic: 0x7f14196f8d40
[   102.427] (II) Module ABI versions:
[   102.427]     X.Org ANSI C Emulation: 0.4
[   102.427]     X.Org Video Driver: 15.0
[   102.427]     X.Org XInput driver : 20.0
[   102.427]     X.Org Server Extension : 8.0
[   102.427] (II) xfree86: Adding drm device (/dev/dri/card0)
[   102.430] (--) PCI:*(0:1:0:0) 1002:95c4:103c:3600 rev 0, Mem @ 0xc0000000/268435456, 0xd2300000/65536, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[   102.430] Initializing built-in extension Generic Event Extension
[   102.430] Initializing built-in extension SHAPE
[   102.430] Initializing built-in extension MIT-SHM
[   102.430] Initializing built-in extension XInputExtension
[   102.430] Initializing built-in extension XTEST
[   102.430] Initializing built-in extension BIG-REQUESTS
[   102.430] Initializing built-in extension SYNC
[   102.430] Initializing built-in extension XKEYBOARD
[   102.431] Initializing built-in extension XC-MISC
[   102.431] Initializing built-in extension SECURITY
[   102.431] Initializing built-in extension XINERAMA
[   102.431] Initializing built-in extension XFIXES
[   102.431] Initializing built-in extension RENDER
[   102.431] Initializing built-in extension RANDR
[   102.431] Initializing built-in extension COMPOSITE
[   102.431] Initializing built-in extension DAMAGE
[   102.431] Initializing built-in extension MIT-SCREEN-SAVER
[   102.431] Initializing built-in extension DOUBLE-BUFFER
[   102.431] Initializing built-in extension RECORD
[   102.431] Initializing built-in extension DPMS
[   102.433] Initializing built-in extension Present
[   102.434] Initializing built-in extension DRI3
[   102.435] Initializing built-in extension X-Resource
[   102.437] Initializing built-in extension XVideo
[   102.438] Initializing built-in extension XVideo-MotionCompensation
[   102.439] Initializing built-in extension SELinux
[   102.441] Initializing built-in extension XFree86-VidModeExtension
[   102.442] Initializing built-in extension XFree86-DGA
[   102.443] Initializing built-in extension XFree86-DRI
[   102.444] Initializing built-in extension DRI2
[   102.445] (II) LoadModule: "glx"
[   102.445] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   102.447] (II) Module glx: vendor="X.Org Foundation"
[   102.447]     compiled for 1.15.1, module version = 1.0.0
[   102.447]     ABI class: X.Org Server Extension, version 8.0
[   102.447] (==) AIGLX enabled
[   102.448] Loading extension GLX
[   102.448] (==) Matched fglrx as autoconfigured driver 0
[   102.448] (==) Matched ati as autoconfigured driver 1
[   102.448] (==) Matched fglrx as autoconfigured driver 2
[   102.448] (==) Matched ati as autoconfigured driver 3
[   102.448] (==) Matched modesetting as autoconfigured driver 4
[   102.448] (==) Matched fbdev as autoconfigured driver 5
[   102.448] (==) Matched vesa as autoconfigured driver 6
[   102.448] (==) Assigned the driver to the xf86ConfigLayout
[   102.448] (II) LoadModule: "fglrx"
[   102.449] [B](WW) Warning, couldn't open module fglrx
[   102.449] (II) UnloadModule: "fglrx"
[   102.449] (II) Unloading fglrx
[   102.449] (EE) Failed to load module "fglrx" (module does not exist, 0)[/B]
[   102.449] (II) LoadModule: "ati"
[   102.449] **(WW) Warning, couldn't open module ati**
[   102.449] (II) UnloadModule: "ati"
[   102.449] (II) Unloading ati
[   102.449] **(EE) Failed to load module "ati" (module does not exist, 0)**
[   102.449] (II) LoadModule: "modesetting"
[   102.450] **(WW) Warning, couldn't open module modesetting**
[   102.450] (II) UnloadModule: "modesetting"
[   102.450] (II) Unloading modesetting
[   102.450] **(EE) Failed to load module "modesetting" (module does not exist, 0)**
[   102.450] (II) LoadModule: "fbdev"
[   102.450] (WW) Warning, couldn't open module fbdev
[   102.450] (II) UnloadModule: "fbdev"
[   102.450] (II) Unloading fbdev
[   102.450]** (EE) Failed to load module "fbdev" (module does not exist, 0)**
[   102.450] (II) LoadModule: "vesa"
[   102.451] (WW) Warning, couldn't open module vesa
[   102.451] (II) UnloadModule: "vesa"
[   102.451] (II) Unloading vesa
[   102.451] **(EE) Failed to load module "vesa" (module does not exist, 0)**
[   102.451] (==) Matched fglrx as autoconfigured driver 0
[   102.451] (==) Matched ati as autoconfigured driver 1
[   102.451] (==) Matched fglrx as autoconfigured driver 2
[   102.451] (==) Matched ati as autoconfigured driver 3
[   102.451] (==) Matched modesetting as autoconfigured driver 4
[   102.451] (==) Matched fbdev as autoconfigured driver 5
[   102.451] (==) Matched vesa as autoconfigured driver 6
[   102.451] (==) Assigned the driver to the xf86ConfigLayout
[   102.451] (II) LoadModule: "fglrx"
[   102.451] (WW) Warning, couldn't open module fglrx
[   102.451] (II) UnloadModule: "fglrx"
[   102.451] (II) Unloading fglrx
[   102.451] **(EE) Failed to load module "fglrx" (module does not exist, 0)**
[   102.451] (II) LoadModule: "ati"
[   102.452] (WW) Warning, couldn't open module ati
[   102.452] (II) UnloadModule: "ati"
[   102.452] (II) Unloading ati
[   102.452] **(EE) Failed to load module "ati" (module does not exist, 0)**
[   102.452] (II) LoadModule: "modesetting"
[   102.452] (WW) Warning, couldn't open module modesetting
[   102.452] (II) UnloadModule: "modesetting"
[   102.452] (II) Unloading modesetting
[   102.452] **(EE) Failed to load module "modesetting" (module does not exist, 0)**
[   102.452] (II) LoadModule: "fbdev"
[   102.453] (WW) Warning, couldn't open module fbdev
[   102.453] (II) UnloadModule: "fbdev"
[   102.453] (II) Unloading fbdev
[   102.453] **(EE) Failed to load module "fbdev" (module does not exist, 0)**
[   102.453] (II) LoadModule: "vesa"
[   102.453] (WW) Warning, couldn't open module vesa
[   102.453] (II) UnloadModule: "vesa"
[   102.453] (II) Unloading vesa
[   102.453] [B](EE) Failed to load module "vesa" (module does not exist, 0)
[   102.453] (EE) No drivers available.[/B]
[   102.453] (EE) 
**Fatal server error:**
[   102.455] [B](EE) no screens found(EE) 
[   102.457] (EE) [/B]
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   102.461] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   102.462] (EE)




regards AP.

---

