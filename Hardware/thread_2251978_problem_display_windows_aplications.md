---
title: "problem display windows aplications"
date: 2014-11-08
forum: Hardware
---

### Post by vincentmichaud on 2014-11-08
hello,
 I despair of finding a proper display. I used Accelerated Open Source driver for nVidia cards. A black frame replaces application menus and display settings are not retained at startup.You could see the problem [here]("https://www.dropbox.com/s/q2rcldyu5lmgov3/pb%20affichage2.png?dl=0").   I think it is a problem compiz, X11 xorg, but at my level, I am unable to solve. I tried several times to reinstall compiz after deleting configuration files, but also the new driver in which I work and the proprietary drivers, or those current version of xorg-edgers PPA. I have a nvidia graphics card gtx 560 ti. I also tried booting with the kernel running on Thrusty unsuccessfully because I now turn to the core 3.17.2. I made several reset or replace as ```
dconf reset -f /org/compiz/ && setsid unity

```
Thank you for your help, here is the /var/log/Xorg.0.log file, not against file /etc/X11/xorg.conf
 I did not put the end on the screen resolutions because it would run on multiple pages
```
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.363] X Protocol Version 11, Revision 0
[    29.363] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.363] Current Operating System: Linux vince 3.17.2-031702-generic #201410301416 SMP Thu Oct 30 18:18:02 UTC 2014 x86_64
[    29.363] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.17.2-031702-generic root=UUID=e216b65f-b16b-4e11-a6cf-5731ba1df3d1 ro quiet splash vt.handoff=7
[    29.363] Build Date: 30 July 2014  12:21:54AM
[    29.363] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.363] Current version of pixman: 0.30.2
[    29.363]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.363] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.363] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  8 09:23:01 2014
[    29.390] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.440] (==) No Layout section.  Using the first Screen section.
[    29.440] (==) No screen section available. Using defaults.
[    29.440] (**) |-->Screen "Default Screen Section" (0)
[    29.440] (**) |   |-->Monitor "<default monitor>"
[    29.440] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.440] (==) Automatically adding devices
[    29.440] (==) Automatically enabling devices
[    29.440] (==) Automatically adding GPU devices
[    29.449] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.449]     Entry deleted from font path.
[    29.449] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.449]     Entry deleted from font path.
[    29.449] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.449]     Entry deleted from font path.
[    29.450] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.450]     Entry deleted from font path.
[    29.450] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.450]     Entry deleted from font path.
[    29.450] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.450] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.450] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.450] (II) Loader magic: 0x7f7eaa726d40
[    29.450] (II) Module ABI versions:
[    29.450]     X.Org ANSI C Emulation: 0.4
[    29.450]     X.Org Video Driver: 15.0
[    29.450]     X.Org XInput driver : 20.0
[    29.450]     X.Org Server Extension : 8.0
[    29.450] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.451] (--) PCI:*(0:1:0:0) 10de:1200:1462:2382 rev 161, Mem @ 0xf8000000/33554432, 0xd0000000/134217728, 0xd8000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    29.452] Initializing built-in extension Generic Event Extension
[    29.452] Initializing built-in extension SHAPE
[    29.452] Initializing built-in extension MIT-SHM
[    29.452] Initializing built-in extension XInputExtension
[    29.452] Initializing built-in extension XTEST
[    29.452] Initializing built-in extension BIG-REQUESTS
[    29.452] Initializing built-in extension SYNC
[    29.452] Initializing built-in extension XKEYBOARD
[    29.452] Initializing built-in extension XC-MISC
[    29.452] Initializing built-in extension SECURITY
[    29.452] Initializing built-in extension XINERAMA
[    29.452] Initializing built-in extension XFIXES
[    29.452] Initializing built-in extension RENDER
[    29.452] Initializing built-in extension RANDR
[    29.452] Initializing built-in extension COMPOSITE
[    29.452] Initializing built-in extension DAMAGE
[    29.452] Initializing built-in extension MIT-SCREEN-SAVER
[    29.452] Initializing built-in extension DOUBLE-BUFFER
[    29.452] Initializing built-in extension RECORD
[    29.452] Initializing built-in extension DPMS
[    29.452] Initializing built-in extension Present
[    29.452] Initializing built-in extension DRI3
[    29.452] Initializing built-in extension X-Resource
[    29.452] Initializing built-in extension XVideo
[    29.452] Initializing built-in extension XVideo-MotionCompensation
[    29.452] Initializing built-in extension SELinux
[    29.452] Initializing built-in extension XFree86-VidModeExtension
[    29.452] Initializing built-in extension XFree86-DGA
[    29.452] Initializing built-in extension XFree86-DRI
[    29.452] Initializing built-in extension DRI2
[    29.452] (II) LoadModule: "glx"
[    29.474] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.608] (II) Module glx: vendor="X.Org Foundation"
[    29.608]     compiled for 1.15.1, module version = 1.0.0
[    29.608]     ABI class: X.Org Server Extension, version 8.0
[    29.608] (==) AIGLX enabled
[    29.608] Loading extension GLX
[    29.608] (==) Matched nvidia as autoconfigured driver 0
[    29.608] (==) Matched nouveau as autoconfigured driver 1
[    29.608] (==) Matched nvidia as autoconfigured driver 2
[    29.608] (==) Matched nouveau as autoconfigured driver 3
[    29.608] (==) Matched modesetting as autoconfigured driver 4
[    29.608] (==) Matched fbdev as autoconfigured driver 5
[    29.608] (==) Matched vesa as autoconfigured driver 6
[    29.608] (==) Assigned the driver to the xf86ConfigLayout
[    29.608] (II) LoadModule: "nvidia"
[    29.608] (WW) Warning, couldn't open module nvidia
[    29.608] (II) UnloadModule: "nvidia"
[    29.608] (II) Unloading nvidia
[    29.608] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    29.608] (II) LoadModule: "nouveau"
[    29.608] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.637] (II) Module nouveau: vendor="X.Org Foundation"
[    29.637]     compiled for 1.15.1, module version = 1.0.11
[    29.637]     Module class: X.Org Video Driver
[    29.637]     ABI class: X.Org Video Driver, version 15.0
[    29.637] (II) LoadModule: "modesetting"
[    29.637] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.644] (II) Module modesetting: vendor="X.Org Foundation"
[    29.644]     compiled for 1.15.0, module version = 0.8.1
[    29.644]     Module class: X.Org Video Driver
[    29.644]     ABI class: X.Org Video Driver, version 15.0
[    29.644] (II) LoadModule: "fbdev"
[    29.644] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.645] (II) Module fbdev: vendor="X.Org Foundation"
[    29.645]     compiled for 1.15.0, module version = 0.4.4
[    29.645]     Module class: X.Org Video Driver
[    29.645]     ABI class: X.Org Video Driver, version 15.0
[    29.645] (II) LoadModule: "vesa"
[    29.645] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.646] (II) Module vesa: vendor="X.Org Foundation"
[    29.646]     compiled for 1.15.0, module version = 2.3.3
[    29.646]     Module class: X.Org Video Driver
[    29.646]     ABI class: X.Org Video Driver, version 15.0
[    29.646] (==) Matched nvidia as autoconfigured driver 0
[    29.646] (==) Matched nouveau as autoconfigured driver 1
[    29.646] (==) Matched nvidia as autoconfigured driver 2
[    29.646] (==) Matched nouveau as autoconfigured driver 3
[    29.646] (==) Matched modesetting as autoconfigured driver 4
[    29.646] (==) Matched fbdev as autoconfigured driver 5
[    29.646] (==) Matched vesa as autoconfigured driver 6
[    29.646] (==) Assigned the driver to the xf86ConfigLayout
[    29.646] (II) LoadModule: "nvidia"
[    29.646] (WW) Warning, couldn't open module nvidia
[    29.646] (II) UnloadModule: "nvidia"
[    29.646] (II) Unloading nvidia
[    29.646] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    29.646] (II) LoadModule: "nouveau"
[    29.646] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.646] (II) Module nouveau: vendor="X.Org Foundation"
[    29.646]     compiled for 1.15.1, module version = 1.0.11
[    29.646]     Module class: X.Org Video Driver
[    29.646]     ABI class: X.Org Video Driver, version 15.0
[    29.646] (II) UnloadModule: "nouveau"
[    29.646] (II) Unloading nouveau
[    29.646] (II) Failed to load module "nouveau" (already loaded, 0)
[    29.646] (II) LoadModule: "modesetting"
[    29.646] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.646] (II) Module modesetting: vendor="X.Org Foundation"
[    29.646]     compiled for 1.15.0, module version = 0.8.1
[    29.646]     Module class: X.Org Video Driver
[    29.646]     ABI class: X.Org Video Driver, version 15.0
[    29.646] (II) UnloadModule: "modesetting"
[    29.646] (II) Unloading modesetting
[    29.646] (II) Failed to load module "modesetting" (already loaded, 0)
[    29.646] (II) LoadModule: "fbdev"
[    29.647] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.647] (II) Module fbdev: vendor="X.Org Foundation"
[    29.647]     compiled for 1.15.0, module version = 0.4.4
[    29.647]     Module class: X.Org Video Driver
[    29.647]     ABI class: X.Org Video Driver, version 15.0
[    29.647] (II) UnloadModule: "fbdev"
[    29.647] (II) Unloading fbdev
[    29.647] (II) Failed to load module "fbdev" (already loaded, 0)
[    29.647] (II) LoadModule: "vesa"
[    29.647] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.647] (II) Module vesa: vendor="X.Org Foundation"
[    29.647]     compiled for 1.15.0, module version = 2.3.3
[    29.647]     Module class: X.Org Video Driver
[    29.647]     ABI class: X.Org Video Driver, version 15.0
[    29.647] (II) UnloadModule: "vesa"
[    29.647] (II) Unloading vesa
[    29.647] (II) Failed to load module "vesa" (already loaded, 0)
[    29.647] (II) NOUVEAU driver 
[    29.647] (II) NOUVEAU driver for NVIDIA chipset families :
```

---

### Post by vincentmichaud on 2014-11-12
hi guys, nobody could answer ?

---

### Post by vincentmichaud on 2014-11-12
Problem solved after switching to ubuntu 14.10. The syslinux-themes-debian package problematic. Purge and reinstall settled the case.

---

