---
title: "Asus H87 PRO (C2) - X11 / lightdm broken by update"
date: 2014-04-01
forum: Hardware
---

### Post by hugl on 2014-04-01
Hello,

after the update earlier today, my PC restarts but Xorg is dead. I can login via ssh, lightdm was started, whoopsie is also reporting something on my screen :-(

ps faux reports:
[FONT=courier new]root      1525  0.0  0.0 188368  2796 ?        Ssl  16:46   0:00 lightdm
whoopsie  1571  0.0  0.0 185588  3812 ?        Ssl  16:46   0:00 whoopsie[/FONT]
(no X running)

Another rather surprising issue is that I get no grub menu. After the BIOS screen the screen is blank.

What did change with the last update?
How can I debug this?

This used to work nicely (since january)!

Manually starting X gives the same error - I lack the correct X driver.

About the hardware:
Asus H87-PRO C2 mainboard with Intel Xeon v1275 cpu BIOS version 1101 (current at time of writing).
Three TFT LCDs (DVI + HDMI + DisplayPort) all connected directly to mainboard - no GPU.

Full /var/log/Xorg.0.log:
[FONT=courier new][   145.383] X Protocol Version 11, Revision 0
[   145.383] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[   145.383] Current Operating System: Linux xeon 3.8.0-38-generic #56~precise1-Ubuntu SMP Thu Mar 13 16:22:48 UTC 2014 x86_64
[   145.383] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-38-generic root=UUID=1f1b56d2-0628-482a-b90e-f73068027dbe ro quiet splash vt.handoff=7
[   145.383] Build Date: 16 October 2013  04:41:23PM
[   145.383] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   145.383] Current version of pixman: 0.30.2
[   145.383]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   145.383] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   145.384] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  1 16:37:12 2014
[   145.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   145.394] (==) No Layout section.  Using the first Screen section.
[   145.394] (==) No screen section available. Using defaults.
[   145.394] (**) |-->Screen "Default Screen Section" (0)
[   145.394] (**) |   |-->Monitor "<default monitor>"
[   145.395] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   145.395] (==) Automatically adding devices
[   145.395] (==) Automatically enabling devices
[   145.396] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   145.396]     Entry deleted from font path.
[   145.396] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   145.396] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   145.396] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   145.396] (II) Loader magic: 0x7f3241761b00
[   145.396] (II) Module ABI versions:
[   145.396]     X.Org ANSI C Emulation: 0.4
[   145.396]     X.Org Video Driver: 11.0
[   145.396]     X.Org XInput driver : 16.0
[   145.396]     X.Org Server Extension : 6.0
[   145.396] (--) PCI:*(0:0:2:0) 8086:041a:1043:8534 rev 6, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[   145.396] (II) Open ACPI successful (/var/run/acpid.socket)
[   145.396] (II) LoadModule: "extmod"
[   145.401] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   145.401] (II) Module extmod: vendor="X.Org Foundation"
[   145.401]     compiled for 1.11.3, module version = 1.0.0
[   145.401]     Module class: X.Org Server Extension
[   145.401]     ABI class: X.Org Server Extension, version 6.0
[   145.401] (II) Loading extension MIT-SCREEN-SAVER
[   145.401] (II) Loading extension XFree86-VidModeExtension
[   145.401] (II) Loading extension XFree86-DGA
[   145.401] (II) Loading extension DPMS
[   145.401] (II) Loading extension XVideo
[   145.401] (II) Loading extension XVideo-MotionCompensation
[   145.401] (II) Loading extension X-Resource
[   145.401] (II) LoadModule: "dbe"
[   145.401] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   145.402] (II) Module dbe: vendor="X.Org Foundation"
[   145.402]     compiled for 1.11.3, module version = 1.0.0
[   145.402]     Module class: X.Org Server Extension
[   145.402]     ABI class: X.Org Server Extension, version 6.0
[   145.402] (II) Loading extension DOUBLE-BUFFER
[   145.402] (II) LoadModule: "glx"
[   145.402] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   145.403] (II) Module glx: vendor="X.Org Foundation"
[   145.403]     compiled for 1.11.3, module version = 1.0.0
[   145.403]     ABI class: X.Org Server Extension, version 6.0
[   145.403] (==) AIGLX enabled
[   145.403] (II) Loading extension GLX
[   145.403] (II) LoadModule: "record"
[   145.403] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   145.403] (II) Module record: vendor="X.Org Foundation"
[   145.403]     compiled for 1.11.3, module version = 1.13.0
[   145.403]     Module class: X.Org Server Extension
[   145.403]     ABI class: X.Org Server Extension, version 6.0
[   145.403] (II) Loading extension RECORD
[   145.403] (II) LoadModule: "dri"
[   145.403] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   145.404] (II) Module dri: vendor="X.Org Foundation"
[   145.404]     compiled for 1.11.3, module version = 1.0.0
[   145.404]     ABI class: X.Org Server Extension, version 6.0
[   145.404] (II) Loading extension XFree86-DRI
[   145.404] (II) LoadModule: "dri2"
[   145.404] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   145.404] (II) Module dri2: vendor="X.Org Foundation"
[   145.404]     compiled for 1.11.3, module version = 1.2.0
[   145.404]     ABI class: X.Org Server Extension, version 6.0
[   145.404] (II) Loading extension DRI2
[   145.404] (==) Matched intel as autoconfigured driver 0
[   145.404] (==) Matched vesa as autoconfigured driver 1
[   145.404] (==) Matched fbdev as autoconfigured driver 2
[   145.404] (==) Assigned the driver to the xf86ConfigLayout
[   145.404] (II) LoadModule: "intel"
[   145.409] (WW) Warning, couldn't open module intel
[   145.409] (II) UnloadModule: "intel"
[   145.409] (II) Unloading intel
[   145.409] (EE) Failed to load module "intel" (module does not exist, 0)
[   145.409] (II) LoadModule: "vesa"
[   145.409] (WW) Warning, couldn't open module vesa
[   145.409] (II) UnloadModule: "vesa"
[   145.409] (II) Unloading vesa
[   145.409] (EE) Failed to load module "vesa" (module does not exist, 0)
[   145.409] (II) LoadModule: "fbdev"
[   145.409] (WW) Warning, couldn't open module fbdev
[   145.409] (II) UnloadModule: "fbdev"
[   145.409] (II) Unloading fbdev
[   145.409] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   145.409] (==) Matched intel as autoconfigured driver 0
[   145.409] (==) Matched vesa as autoconfigured driver 1
[   145.409] (==) Matched fbdev as autoconfigured driver 2
[   145.409] (==) Assigned the driver to the xf86ConfigLayout
[   145.409] (II) LoadModule: "intel"
[   145.409] (WW) Warning, couldn't open module intel
[   145.409] (II) UnloadModule: "intel"
[   145.410] (II) Unloading intel
[   145.410] (EE) Failed to load module "intel" (module does not exist, 0)
[   145.410] (II) LoadModule: "vesa"
[   145.410] (WW) Warning, couldn't open module vesa
[   145.410] (II) UnloadModule: "vesa"
[   145.410] (II) Unloading vesa
[   145.410] (EE) Failed to load module "vesa" (module does not exist, 0)
[   145.410] (II) LoadModule: "fbdev"
[   145.410] (WW) Warning, couldn't open module fbdev
[   145.410] (II) UnloadModule: "fbdev"
[   145.410] (II) Unloading fbdev
[   145.410] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   145.410] (EE) No drivers available.
[   145.410] 
Fatal server error:
[   145.410] no screens found[/FONT]

---

### Post by hugl on 2014-04-01
A "sudo apt-get install xserver-xorg-video-intel" fixed the missing Xorg driver issue, but no gdm greeter comes up.
Also any GRUB console output is missing.

I removed all monitors except the one on DVI, but no grub menu?!

---

