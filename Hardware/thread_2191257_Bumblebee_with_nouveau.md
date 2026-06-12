---
title: "Bumblebee with nouveau"
date: 2013-12-01
forum: Hardware
---

### Post by lucidlytwisted on 2013-12-01
Kubuntu 13.10 running on a Lenovo T430 with Intel HD 4000 and discrete Nvidia NVS 5400M, kernel 3.11, fully updated at time of posting.

I've previously had this running with Bumblebee and the proprietary nvidia driviers without issue (version 304 and 331). I have removed those and now want to test with nouveau (which should support this card as far as I can tell). When I attempt to invoke the discrete GPU I get an exception that seems to relate to libdrm (or possibly libgl).```
user@computer:~$ optirun -vvv glxgears
[ 2782.234048] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2782.234846] [INFO]Configured driver: nouveau
[ 2782.235216] [DEBUG]optirun version 3.2.1 starting...
[ 2782.235286] [DEBUG]Active configuration:
[ 2782.235324] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 2782.235356] [DEBUG] X display: :8
[ 2782.235384] [DEBUG] LD_LIBRARY_PATH: 
[ 2782.235414] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 2782.235444] [DEBUG] Accel/display bridge: auto
[ 2782.235474] [DEBUG] VGL Compression: proxy
[ 2782.235502] [DEBUG] VGLrun extra options: 
[ 2782.235531] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 2782.272215] [DEBUG]Using auto-detected bridge virtualgl
[ 2783.421853] [INFO]Response: No - error: [XORG] (EE) NOUVEAU(0): [drm] failed to set drm interface version.

[ 2783.421888] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NOUVEAU(0): [drm] failed to set drm interface version.

[ 2783.421898] [DEBUG]Socket closed.
[ 2783.421921] [ERROR]Aborting because fallback start is disabled.
[ 2783.421929] [DEBUG]Killing all remaining processes.
```

And when I check the relevant XOrg log, I see this:```
[  2783.254] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[  2783.254] X Protocol Version 11, Revision 0
[  2783.254] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  2783.254] Current Operating System: Linux kanzi 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64
[  2783.254] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=c3aac455-acbc-47db-a89b-55bd1732c596 ro quiet splash vt.handoff=7
[  2783.254] Build Date: 15 October 2013  09:23:37AM
[  2783.254] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[  2783.254] Current version of pixman: 0.30.2
[  2783.254]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  2783.254] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2783.254] (==) Log file: "/var/log/Xorg.8.log", Time: Sun Dec  1 22:14:41 2013
[  2783.267] (++) Using config file: "/etc/bumblebee/xorg.conf.nouveau"
[  2783.268] (++) Using config directory: "/etc/bumblebee/xorg.conf.d"
[  2783.268] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2783.274] (==) ServerLayout "Layout0"
[  2783.274] (==) No screen section available. Using defaults.
[  2783.274] (**) |-->Screen "Default Screen Section" (0)
[  2783.274] (**) |   |-->Monitor "<default monitor>"
[  2783.274] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[  2783.274] (**) |   |-->Device "DiscreteNvidia"
[  2783.274] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  2783.274] (**) Option "AutoAddDevices" "false"
[  2783.274] (**) Option "AutoAddGPU" "false"
[  2783.274] (**) Not automatically adding devices
[  2783.274] (==) Automatically enabling devices
[  2783.274] (**) Not automatically adding GPU devices
[  2783.274] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2783.274]     Entry deleted from font path.
[  2783.274] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2783.274]     Entry deleted from font path.
[  2783.274] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2783.274]     Entry deleted from font path.
[  2783.274] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2783.274]     Entry deleted from font path.
[  2783.274] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2783.274]     Entry deleted from font path.
[  2783.274] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  2783.274] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2783.274] (==) |-->Input Device "<default pointer>"
[  2783.274] (==) |-->Input Device "<default keyboard>"
[  2783.274] (==) The core pointer device wasn't specified explicitly in the layout.
    Using the default mouse configuration.
[  2783.274] (==) The core keyboard device wasn't specified explicitly in the layout.
    Using the default keyboard configuration.
[  2783.274] (II) Loader magic: 0x7f0a7ffe0d20
[  2783.274] (II) Module ABI versions:
[  2783.274]     X.Org ANSI C Emulation: 0.4
[  2783.274]     X.Org Video Driver: 14.1
[  2783.274]     X.Org XInput driver : 19.1
[  2783.274]     X.Org Server Extension : 7.0
[  2783.275] (II) xfree86: Adding drm device (/dev/dri/card1)
[  2783.275] setversion 1.4 failed
[  2783.275] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[  2783.275] (II) xfree86: Adding drm device (/dev/dri/card0)
[  2783.275] setversion 1.4 failed
[  2783.275] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  2783.278] (--) PCI:*(0:1:0:0) 10de:0def:17aa:21f4 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[  2783.278] (II) Open ACPI successful (/var/run/acpid.socket)
[  2783.278] Initializing built-in extension Generic Event Extension
[  2783.278] Initializing built-in extension SHAPE
[  2783.278] Initializing built-in extension MIT-SHM
[  2783.278] Initializing built-in extension XInputExtension
[  2783.278] Initializing built-in extension XTEST
[  2783.278] Initializing built-in extension BIG-REQUESTS
[  2783.278] Initializing built-in extension SYNC
[  2783.278] Initializing built-in extension XKEYBOARD
[  2783.278] Initializing built-in extension XC-MISC
[  2783.278] Initializing built-in extension SECURITY
[  2783.278] Initializing built-in extension XINERAMA
[  2783.278] Initializing built-in extension XFIXES
[  2783.278] Initializing built-in extension RENDER
[  2783.278] Initializing built-in extension RANDR
[  2783.278] Initializing built-in extension COMPOSITE
[  2783.278] Initializing built-in extension DAMAGE
[  2783.279] Initializing built-in extension MIT-SCREEN-SAVER
[  2783.279] Initializing built-in extension DOUBLE-BUFFER
[  2783.279] Initializing built-in extension RECORD
[  2783.279] Initializing built-in extension DPMS
[  2783.279] Initializing built-in extension X-Resource
[  2783.279] Initializing built-in extension XVideo
[  2783.279] Initializing built-in extension XVideo-MotionCompensation
[  2783.279] Initializing built-in extension SELinux
[  2783.279] Initializing built-in extension XFree86-VidModeExtension
[  2783.279] Initializing built-in extension XFree86-DGA
[  2783.279] Initializing built-in extension XFree86-DRI
[  2783.279] Initializing built-in extension DRI2
[  2783.279] (II) "glx" will be loaded by default.
[  2783.279] (WW) "xmir" is not to be loaded by default. Skipping.
[  2783.279] (II) LoadModule: "dri2"
[  2783.279] (II) Module "dri2" already built-in
[  2783.279] (II) LoadModule: "glamoregl"
[  2783.279] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  2783.280] (II) Module glamoregl: vendor="X.Org Foundation"
[  2783.280]     compiled for 1.14.3, module version = 0.5.1
[  2783.280]     ABI class: X.Org ANSI C Emulation, version 0.4
[  2783.280] (II) LoadModule: "glx"
[  2783.280] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2783.280] (II) Module glx: vendor="X.Org Foundation"
[  2783.280]     compiled for 1.14.3, module version = 1.0.0
[  2783.280]     ABI class: X.Org Server Extension, version 7.0
[  2783.280] (==) AIGLX enabled
[  2783.280] Loading extension GLX
[  2783.280] (II) LoadModule: "nouveau"
[  2783.281] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  2783.301] (II) Module nouveau: vendor="X.Org Foundation"
[  2783.301]     compiled for 1.14.2.901, module version = 1.0.9
[  2783.301]     Module class: X.Org Video Driver
[  2783.301]     ABI class: X.Org Video Driver, version 14.1
[  2783.301] (II) LoadModule: "mouse"
[  2783.301] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[  2783.311] (II) Module mouse: vendor="X.Org Foundation"
[  2783.311]     compiled for 1.14.1, module version = 1.7.2
[  2783.311]     Module class: X.Org XInput Driver
[  2783.311]     ABI class: X.Org XInput driver, version 19.1
[  2783.311] (II) LoadModule: "kbd"
[  2783.312] (WW) Warning, couldn't open module kbd
[  2783.312] (II) UnloadModule: "kbd"
[  2783.312] (II) Unloading kbd
[  2783.312] (EE) Failed to load module "kbd" (module does not exist, 0)
[  2783.312] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[  2783.312] (II) NOUVEAU driver for NVIDIA chipset families :
[  2783.312]     RIVA TNT        (NV04)
[  2783.312]     RIVA TNT2       (NV05)
[  2783.312]     GeForce 256     (NV10)
[  2783.312]     GeForce 2       (NV11, NV15)
[  2783.312]     GeForce 4MX     (NV17, NV18)
[  2783.312]     GeForce 3       (NV20)
[  2783.312]     GeForce 4Ti     (NV25, NV28)
[  2783.312]     GeForce FX      (NV3x)
[  2783.312]     GeForce 6       (NV4x)
[  2783.312]     GeForce 7       (G7x)
[  2783.312]     GeForce 8       (G8x)
[  2783.312]     GeForce GTX 200 (NVA0)
[  2783.312]     GeForce GTX 400 (NVC0)
[  2783.312] (--) using VT number 7

[  2783.365] (II) [drm] nouveau interface version: 1.1.1
[  2783.365] (II) Loading sub module "dri2"
[  2783.365] (II) LoadModule: "dri2"
[  2783.365] (II) Module "dri2" already built-in
[  2783.420] (EE) NOUVEAU(0): [drm] failed to set drm interface version.
[  2783.420] (EE) NOUVEAU(0): [drm] error opening the drm
[  2783.420] (EE) NOUVEAU(0): 944: 
[  2783.420] (II) UnloadModule: "nouveau"
[  2783.420] (EE) Screen(s) found, but none have a usable configuration.
[  2783.420] (EE) 
Fatal server error:
[  2783.420] (EE) no screens found(EE) 
```

I've looked unsuccessfully for a solution to this problem and all I can find is that my nouveau drivers might be out of whack with libdrm; I don't see how that can be as I have installed everything from the repos:
[TABLE="width: 500"]
[TR]
[TD][B]Package
[/B][/TD]
[TD][B]Version
[/B][/TD]
[/TR]
[TR]
[TD]libdrm-nouveau
[/TD]
[TD]2.4.46-1ubuntu1
[/TD]
[/TR]
[TR]
[TD]xserver-xorg-video-nouveau
[/TD]
[TD]1:1.0.9-2ubuntu1
[/TD]
[/TR]
[TR]
[TD]bumblebee
[/TD]
[TD]3.2.1.3
[/TD]
[/TR]
[/TABLE]
 
Can anyone offer advice on how to resolve this? Thanks.

---

