---
title: "Only 1/4 of screen is used by Xubuntu"
date: 2013-05-04
forum: Hardware
---

### Post by Methos2 on 2013-05-04
Hi,

I have installed XUbuntu 13.04 on my old Dell Inspiron 1100 with the aim of making it usable again for basic tasks. Unfortunately most of the screen doesn't seem to be used at all by XUbuntu. I have attached a screenshot. How do I sort it out so it looks normal? There are no properietry drivers to install, which was my first thought. Any help would be very welcome!

Here is a photo of the screen: 

[IMG]https://mail.google.com/mail/?ui=2&ik=c5bf86112c&view=att&th=13e726d32119bcdb&attid=0.1&disp=thd&realattid=1434157638854115328-1&zw[/IMG]

---

### Post by Yellow Pasque on 2013-05-05
Your screenshot didn't post (and screenshots usually aren't real helpful anyway). Instead,post your /var/log/Xorg.0.log

---

### Post by Methos2 on 2013-05-05
Sorry I dont know what that means. The photo was taken just showed the screen divided into four parts with only the top left being used by Xubuntu. The other parts are grey ish colours. Its like the OS cant detect screen size or the drivers to run the graphics chip. It ran Xubuntu 10.10 ok.

---

### Post by Yellow Pasque on 2013-05-05
You have a file: /var/log/Xorg.0.log 
Post its contents here (or use pastebin).

---

### Post by Methos2 on 2013-05-05
Here is the file contents:
```

[    27.355] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    27.355] X Protocol Version 11, Revision 0
[    27.355] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    27.355] Current Operating System: Linux mum-laptop 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686
[    27.363] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=a5a7ad7f-ad77-4ff6-a09b-b18632dd49f1 ro quiet splash vt.handoff=7
[    27.363] Build Date: 17 April 2013  10:42:56PM
[    27.363] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    27.363] Current version of pixman: 0.28.2
[    27.363]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    27.363] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.364] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  5 19:14:34 2013
[    27.417] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.418] (==) No Layout section.  Using the first Screen section.
[    27.418] (==) No screen section available. Using defaults.
[    27.418] (**) |-->Screen "Default Screen Section" (0)
[    27.418] (**) |   |-->Monitor "<default monitor>"
[    27.419] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.419] (==) Automatically adding devices
[    27.419] (==) Automatically enabling devices
[    27.419] (==) Automatically adding GPU devices
[    27.419] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.419]     Entry deleted from font path.
[    27.419] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.419]     Entry deleted from font path.
[    27.420] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.420]     Entry deleted from font path.
[    27.420] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.420]     Entry deleted from font path.
[    27.420] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.420]     Entry deleted from font path.
[    27.421] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    27.421]     Entry deleted from font path.
[    27.421] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.421] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.421] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.421] (II) Loader magic: 0xb779a6a0
[    27.421] (II) Module ABI versions:
[    27.421]     X.Org ANSI C Emulation: 0.4
[    27.421]     X.Org Video Driver: 13.1
[    27.421]     X.Org XInput driver : 18.0
[    27.421]     X.Org Server Extension : 7.0
[    27.422] (II) config/udev: Adding drm device (/dev/dri/card0)
[    27.447] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    27.447] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.453] Initializing built-in extension Generic Event Extension
[    27.453] Initializing built-in extension SHAPE
[    27.453] Initializing built-in extension MIT-SHM
[    27.453] Initializing built-in extension XInputExtension
[    27.453] Initializing built-in extension XTEST
[    27.453] Initializing built-in extension BIG-REQUESTS
[    27.453] Initializing built-in extension SYNC
[    27.453] Initializing built-in extension XKEYBOARD
[    27.453] Initializing built-in extension XC-MISC
[    27.453] Initializing built-in extension SECURITY
[    27.453] Initializing built-in extension XINERAMA
[    27.454] Initializing built-in extension XFIXES
[    27.454] Initializing built-in extension RENDER
[    27.454] Initializing built-in extension RANDR
[    27.454] Initializing built-in extension COMPOSITE
[    27.454] Initializing built-in extension DAMAGE
[    27.454] Initializing built-in extension MIT-SCREEN-SAVER
[    27.454] Initializing built-in extension DOUBLE-BUFFER
[    27.454] Initializing built-in extension RECORD
[    27.454] Initializing built-in extension DPMS
[    27.454] Initializing built-in extension X-Resource
[    27.454] Initializing built-in extension XVideo
[    27.454] Initializing built-in extension XVideo-MotionCompensation
[    27.454] Initializing built-in extension SELinux
[    27.454] Initializing built-in extension XFree86-VidModeExtension
[    27.454] Initializing built-in extension XFree86-DGA
[    27.454] Initializing built-in extension XFree86-DRI
[    27.454] Initializing built-in extension DRI2
[    27.455] (II) LoadModule: "glx"
[    27.630] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.631] (II) Module glx: vendor="X.Org Foundation"
[    27.631]     compiled for 1.13.3, module version = 1.0.0
[    27.631]     ABI class: X.Org Server Extension, version 7.0
[    27.631] (==) AIGLX enabled
[    27.631] Loading extension GLX
[    27.631] (==) Matched intel as autoconfigured driver 0
[    27.631] (==) Matched intel as autoconfigured driver 1
[    27.631] (==) Matched vesa as autoconfigured driver 2
[    27.631] (==) Matched modesetting as autoconfigured driver 3
[    27.631] (==) Matched fbdev as autoconfigured driver 4
[    27.631] (==) Assigned the driver to the xf86ConfigLayout
[    27.631] (II) LoadModule: "intel"
[    27.632] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.812] (II) Module intel: vendor="X.Org Foundation"
[    27.901]     compiled for 1.13.3, module version = 2.21.6
[    27.901]     Module class: X.Org Video Driver
[    27.901]     ABI class: X.Org Video Driver, version 13.1
[    27.901] (II) LoadModule: "vesa"
[    27.902] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.902] (II) Module vesa: vendor="X.Org Foundation"
[    27.903]     compiled for 1.12.99.902, module version = 2.3.2
[    27.903]     Module class: X.Org Video Driver
[    27.903]     ABI class: X.Org Video Driver, version 13.0
[    27.903] (II) LoadModule: "modesetting"
[    27.903] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.904] (II) Module modesetting: vendor="X.Org Foundation"
[    27.904]     compiled for 1.13.3, module version = 0.7.0
[    27.904]     Module class: X.Org Video Driver
[    27.904]     ABI class: X.Org Video Driver, version 13.1
[    27.904] (II) LoadModule: "fbdev"
[    27.905] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.905] (II) Module fbdev: vendor="X.Org Foundation"
[    27.905]     compiled for 1.12.99.902, module version = 0.4.3
[    27.905]     Module class: X.Org Video Driver
[    27.905]     ABI class: X.Org Video Driver, version 13.0
[    27.906] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
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
[    27.912] (II) VESA: driver for VESA chipsets: vesa
[    27.912] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.912] (II) FBDEV: driver for framebuffer: fbdev
[    27.912] (++) using VT number 7

[    27.913] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    27.914] (WW) Falling back to old probe method for vesa
[    27.914] (WW) Falling back to old probe method for modesetting
[    27.914] (WW) Falling back to old probe method for fbdev
[    27.914] (II) Loading sub module "fbdevhw"
[    27.914] (II) LoadModule: "fbdevhw"
[    27.914] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.915] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.915]     compiled for 1.13.3, module version = 0.0.2
[    27.915]     ABI class: X.Org Video Driver, version 13.1
[    27.918] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 15/16
[    27.918] (==) intel(0): Depth 15, (--) framebuffer bpp 16
[    27.918] (==) intel(0): RGB weight 555
[    27.919] (==) intel(0): Default visual is TrueColor
[    27.919] (--) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    27.924] (--) intel(0): CPU: sse2
[    27.924] (**) intel(0): Framebuffer tiled
[    27.924] (**) intel(0): Pixmaps tiled
[    27.924] (**) intel(0): "Tear free" disabled
[    27.924] (**) intel(0): Forcing per-crtc-pixmaps? no
[    27.932] (II) intel(0): Output LVDS1 has no monitor section
[    27.937] (--) intel(0): found backlight control interface dell_backlight (type 'platform')
[    27.968] (II) intel(0): Output VGA1 has no monitor section
[    27.976] (II) intel(0): EDID for output LVDS1
[    27.977] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    27.977] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.977] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.977] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    27.977] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    27.977] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    27.977] (II) intel(0): Printing probed modes for output LVDS1
[    27.978] (II) intel(0): Modeline "640x480"x60.0   65.00  640 856 992 1344  480 627 633 806 (48.4 kHz P)
[    27.979] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    28.008] (II) intel(0): EDID for output VGA1
[    28.008] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    28.008] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    28.008] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.009] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    28.009] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    28.010] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    28.010] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.010] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    28.010] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    28.011] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    28.011] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    28.011] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.011] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    28.011] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    28.012] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.012] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.012] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    28.013] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    28.013] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    28.013] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    28.013] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    28.013] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    28.013] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    28.013] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    28.013] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    28.013] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    28.013] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.013] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    28.014] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    28.014] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    28.014] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.014] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    28.014] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.014] (II) intel(0): Printing probed modes for output VGA1
[    28.014] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    28.015] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    28.016] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    28.016] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    28.016] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    28.016] (II) intel(0): Output LVDS1 connected
[    28.016] (II) intel(0): Output VGA1 disconnected
[    28.016] (II) intel(0): Using exact sizes for initial modes
[    28.016] (II) intel(0): Output LVDS1 using initial mode 640x480
[    28.016] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.016] (==) intel(0): DPI set to (96, 96)
[    28.016] (II) Loading sub module "dri2"
[    28.016] (II) LoadModule: "dri2"
[    28.016] (II) Module "dri2" already built-in
[    28.016] (II) UnloadModule: "vesa"
[    28.017] (II) Unloading vesa
[    28.017] (II) UnloadModule: "modesetting"
[    28.017] (II) Unloading modesetting
[    28.017] (II) UnloadModule: "fbdev"
[    28.017] (II) Unloading fbdev
[    28.017] (II) UnloadSubModule: "fbdevhw"
[    28.017] (II) Unloading fbdevhw
[    28.018] (II) intel(0): SNA initialized with gen2 backend
[    28.018] (==) intel(0): Backing store disabled
[    28.018] (==) intel(0): Silken mouse enabled
[    28.018] (II) intel(0): HW Cursor enabled
[    28.018] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.205] (==) intel(0): DPMS enabled
[    28.205] (WW) intel(0): Textured video not supported on this hardware
[    28.206] (II) intel(0): [DRI2] Setup complete
[    28.206] (II) intel(0): [DRI2]   DRI driver: i915
[    28.206] (II) intel(0): direct rendering: DRI2 Enabled
[    28.206] (==) intel(0): hotplug detection: "enabled"
[    28.206] (--) RandR disabled
[    28.364] (II) SELinux: Disabled on system
[    29.529] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    29.529] (II) AIGLX: enabled GLX_INTEL_swap_event
[    29.529] (II) AIGLX: enabled GLX_ARB_create_context
[    29.529] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    29.529] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    29.529] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    29.529] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    29.530] (II) AIGLX: Loaded and initialized i915
[    29.530] (II) GLX: Initialized DRI2 GL provider for screen 0
[    29.536] (II) intel(0): switch to mode 640x480 on crtc 3 (pipe 0)
[    30.396] (II) intel(0): Setting screen physical size to 169 x 126
[    30.435] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.458] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    30.458] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.458] (II) LoadModule: "evdev"
[    30.459] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.505] (II) Module evdev: vendor="X.Org Foundation"
[    30.505]     compiled for 1.13.3, module version = 2.7.3
[    30.505]     Module class: X.Org XInput Driver
[    30.505]     ABI class: X.Org XInput driver, version 18.0
[    30.505] (II) Using input driver 'evdev' for 'Video Bus'
[    30.505] (**) Video Bus: always reports core events
[    30.505] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    30.506] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.506] (--) evdev: Video Bus: Found keys
[    30.506] (II) evdev: Video Bus: Configuring as keyboard
[    30.506] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    30.506] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    30.506] (**) Option "xkb_rules" "evdev"
[    30.506] (**) Option "xkb_model" "pc105"
[    30.506] (**) Option "xkb_layout" "gb"
[    30.520] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    30.523] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.523] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.523] (II) Using input driver 'evdev' for 'Power Button'
[    30.523] (**) Power Button: always reports core events
[    30.523] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.523] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.528] (--) evdev: Power Button: Found keys
[    30.528] (II) evdev: Power Button: Configuring as keyboard
[    30.528] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    30.528] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.528] (**) Option "xkb_rules" "evdev"
[    30.528] (**) Option "xkb_model" "pc105"
[    30.528] (**) Option "xkb_layout" "gb"
[    30.530] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    30.530] (II) No input driver specified, ignoring this device.
[    30.530] (II) This device may have been added with another device file.
[    30.536] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    30.536] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.536] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.536] (**) Sleep Button: always reports core events
[    30.536] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    30.536] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.537] (--) evdev: Sleep Button: Found keys
[    30.537] (II) evdev: Sleep Button: Configuring as keyboard
[    30.537] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    30.537] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    30.537] (**) Option "xkb_rules" "evdev"
[    30.537] (**) Option "xkb_model" "pc105"
[    30.537] (**) Option "xkb_layout" "gb"
[    30.538] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    30.538] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    30.545] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    30.545] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.545] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.545] (**) AT Translated Set 2 keyboard: always reports core events
[    30.545] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    30.545] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.545] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.545] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.546] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    30.546] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    30.546] (**) Option "xkb_rules" "evdev"
[    30.546] (**) Option "xkb_model" "pc105"
[    30.546] (**) Option "xkb_layout" "gb"
[    30.552] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    30.552] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.552] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.552] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    30.552] (II) LoadModule: "synaptics"
[    30.553] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.553] (II) Module synaptics: vendor="X.Org Foundation"
[    30.554]     compiled for 1.13.1.901, module version = 1.6.2
[    30.554]     Module class: X.Org XInput Driver
[    30.554]     ABI class: X.Org XInput driver, version 18.0
[    30.554] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.554] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.554] (**) Option "Device" "/dev/input/event5"
[    30.554] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    30.554] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    30.555] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.555] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.555] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.555] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.555] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.555] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.555] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    30.555] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    30.555] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    30.555] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    30.560] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    30.560] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.560] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    30.560] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.560] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.561] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.562] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    30.562] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
```

---

