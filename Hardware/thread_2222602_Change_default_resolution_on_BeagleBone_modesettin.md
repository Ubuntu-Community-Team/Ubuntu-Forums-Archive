---
title: "Change default resolution on BeagleBone modesetting vs fbdev"
date: 2014-05-07
forum: Hardware
---

### Post by digiteltlc on 2014-05-07
Hi
I'm running a BeagleBone with a 5,7" LCD Touchscreen with a native resolution of 640x480
However, the system recognizes monitor as a LCD7 Cape with 800x480 resolution and after LXDE boot desktop is only partially displayed

On the old 12.04 FBDEV was used and I fixed problem adding the /usr/share/X11/xorg.conf.d/10-monitor.conf this way :

[SIZE=2][COLOR=#008080]Section "Monitor"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Identifier "Configured Monitor"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]EndSection[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]
[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]Section "Screen"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Identifier "Default Screen"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Device "Configured Video Device"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Monitor "Configured Monitor"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    #Limited by SGX?[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    DefaultDepth 16[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    SubSection "Display"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]        Modes "640x480"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]EndSubsection[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]EndSection[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]
[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]Section "Device"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Identifier "Configured Video Device"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Driver "omapfb"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]    Option "fb" "/dev/fb0"[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]EndSection
[/COLOR]
With new kernel on 13.10 or 14.04 it seems FBDEV is no more used but modesetting is, instead.
So the old 10-monitor.conf is useless.


[/SIZE]/var/log/Xorg.0.log from 12.04 is :
[SIZE=2]



[/SIZE][SIZE=1][COLOR=#ff0000][    25.574] (II) LoadModule: "glx"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.590] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.621] (II) Module glx: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.621]    compiled for 1.13.0, module version = 1.0.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.621]    ABI class: X.Org Server Extension, version 7.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.621] (==) AIGLX enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.622] Loading extension GLX[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.622] (II) LoadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.624] (WW) Warning, couldn't open module omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.624] (II) UnloadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.624] (II) Unloading omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (EE) Failed to load module "omapfb" (module does not exist, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (==) Matched omapfb as autoconfigured driver 0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (==) Matched modesetting as autoconfigured driver 1[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (==) Matched fbdev as autoconfigured driver 2[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (==) Assigned the driver to the xf86ConfigLayout[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.625] (II) LoadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.627] (WW) Warning, couldn't open module omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.627] (II) UnloadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.628] (II) Unloading omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.628] (EE) Failed to load module "omapfb" (module does not exist, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.628] (II) LoadModule: "modesetting"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.629] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.643] (II) Module modesetting: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.644]    compiled for 1.13.0, module version = 0.5.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.644]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.644]    ABI class: X.Org Video Driver, version 13.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.644] (II) LoadModule: "fbdev"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.645] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.649] (II) Module fbdev: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.649]    compiled for 1.12.99.902, module version = 0.4.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.649]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.649]    ABI class: X.Org Video Driver, version 13.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.649] (II) modesetting: Driver for Modesetting Kernel Drivers: kms[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.650] (II) FBDEV: driver for framebuffer: fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.650] (++) using VT number 7[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000]
[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.656] (WW) Falling back to old probe method for modesetting[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.656] (EE) open /dev/dri/card0: No such file or directory[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.656] (WW) Falling back to old probe method for fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.656] (II) Loading sub module "fbdevhw"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.656] (II) LoadModule: "fbdevhw"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.658] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.661] (II) Module fbdevhw: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.662]    compiled for 1.13.0, module version = 0.0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.662]    ABI class: X.Org Video Driver, version 13.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.662] (II) FBDEV(0): using default device[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.662] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (**) FBDEV(0): Depth 16, (--) framebuffer bpp 16[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (==) FBDEV(0): RGB weight 565[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (==) FBDEV(0): Default visual is TrueColor[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (II) FBDEV(0): hardware: DA8xx FB Drv (video memory: 1600kB)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (II) FBDEV(0): checking modes against framebuffer device...[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (II) FBDEV(0):     mode "640x480" ok[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.663] (II) FBDEV(0): checking modes against monitor...[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (**) FBDEV(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (II) FBDEV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (==) FBDEV(0): DPI set to (96, 96)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (II) Loading sub module "fb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.664] (II) LoadModule: "fb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.666] (II) Loading /usr/lib/xorg/modules/libfb.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.679] (II) Module fb: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.679]    compiled for 1.13.0, module version = 1.0.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.679]    ABI class: X.Org ANSI C Emulation, version 0.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.683] (**) FBDEV(0): using shadow framebuffer[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.683] (II) Loading sub module "shadow"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.683] (II) LoadModule: "shadow"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.684] (II) Loading /usr/lib/xorg/modules/libshadow.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.692] (II) Module shadow: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.692]    compiled for 1.13.0, module version = 1.1.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.692]    ABI class: X.Org ANSI C Emulation, version 0.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.692] (II) UnloadModule: "modesetting"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.692] (II) Unloading modesetting[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.693] (EE) FBDEV(0): FBIOBLANK: Invalid argument[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.701] (==) FBDEV(0): Backing store disabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.702] (==) FBDEV(0): DPMS enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.703] (==) RandR enabled[/COLOR][/SIZE]
[SIZE=2]
The 13.10 one is :

[/SIZE][SIZE=1][COLOR=#ff0000][    24.549] (II) LoadModule: "glx"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.603] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.805] (II) Module glx: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.806]    compiled for 1.15.1, module version = 1.0.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.806]    ABI class: X.Org Server Extension, version 8.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.806] (==) AIGLX enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.806] Loading extension GLX[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.816] (==) Matched omapfb as autoconfigured driver 0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.820] (==) Matched modesetting as autoconfigured driver 1[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.823] (==) Matched fbdev as autoconfigured driver 2[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.823] (==) Assigned the driver to the xf86ConfigLayout[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.823] (II) LoadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.833] (WW) Warning, couldn't open module omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.842] (II) UnloadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.842] (II) Unloading omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.842] (EE) Failed to load module "omapfb" (module does not exist, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.842] (II) LoadModule: "modesetting"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.852] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.866] (II) Module modesetting: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.866]    compiled for 1.15.0, module version = 0.8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.866]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.866]    ABI class: X.Org Video Driver, version 15.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.867] (II) LoadModule: "fbdev"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.868] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.884] (II) Module fbdev: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.888]    compiled for 1.15.0, module version = 0.4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.888]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.888]    ABI class: X.Org Video Driver, version 15.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.894] (==) Matched omapfb as autoconfigured driver 0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.894] (==) Matched modesetting as autoconfigured driver 1[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.894] (==) Matched fbdev as autoconfigured driver 2[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.894] (==) Assigned the driver to the xf86ConfigLayout[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.899] (II) LoadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.916] (WW) Warning, couldn't open module omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.916] (II) UnloadModule: "omapfb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.916] (II) Unloading omapfb[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.916] (EE) Failed to load module "omapfb" (module does not exist, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.916] (II) LoadModule: "modesetting"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.926] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.926] (II) Module modesetting: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.926]    compiled for 1.15.0, module version = 0.8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.926]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.927]    ABI class: X.Org Video Driver, version 15.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.927] (II) UnloadModule: "modesetting"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.927] (II) Unloading modesetting[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.927] (II) Failed to load module "modesetting" (already loaded, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.927] (II) LoadModule: "fbdev"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.939] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.944] (II) Module fbdev: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.944]    compiled for 1.15.0, module version = 0.4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.944]    Module class: X.Org Video Driver[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.945]    ABI class: X.Org Video Driver, version 15.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.945] (II) UnloadModule: "fbdev"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.945] (II) Unloading fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.949] (II) Failed to load module "fbdev" (already loaded, 0)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.949] (II) modesetting: Driver for Modesetting Kernel Drivers: kms[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.949] (II) FBDEV: driver for framebuffer: fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.950] (++) using VT number 7[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000]
[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.955] (II) modesetting(0): using drv /dev/dri/card0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.956] (WW) Falling back to old probe method for fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.956] (II) Loading sub module "fbdevhw"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.956] (II) LoadModule: "fbdevhw"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.957] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.960] (II) Module fbdevhw: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.960]    compiled for 1.15.1, module version = 0.0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.967]    ABI class: X.Org Video Driver, version 15.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.967] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.968] (II) modesetting(0): Creating default Display subsection in Screen section[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000]        "Default Screen Section" for depth/fbbpp 24/32[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.968] (==) modesetting(0): Depth 24, (==) framebuffer bpp 32[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.973] (==) modesetting(0): RGB weight 888[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.974] (==) modesetting(0): Default visual is TrueColor[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.974] (II) modesetting(0): ShadowFB: preferred NO, enabled NO[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.974] (II) modesetting(0): Output LVDS-0 has no monitor section[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): EDID for output LVDS-0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): Printing probed modes for output LVDS-0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): Modeline "800x480"x61.5   30.00  800 840 888 928  480 493 496 526 -hsync -vsync (32.3 kHz eP)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): Output LVDS-0 connected[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): Using exact sizes for initial modes[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.975] (II) modesetting(0): Output LVDS-0 using initial mode 800x480[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.976] (II) modesetting(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.976] (==) modesetting(0): DPI set to (96, 96)[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.976] (II) Loading sub module "fb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.976] (II) LoadModule: "fb"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    24.992] (II) Loading /usr/lib/xorg/modules/libfb.so[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.004] (II) Module fb: vendor="X.Org Foundation"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.005]    compiled for 1.15.1, module version = 1.0.0[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.005]    ABI class: X.Org ANSI C Emulation, version 0.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.005] (II) UnloadModule: "fbdev"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.005] (II) Unloading fbdev[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.005] (II) UnloadSubModule: "fbdevhw"[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.011] (II) Unloading fbdevhw[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.015] (==) Depth 24 pixmap format is 32 bpp[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.049] (==) modesetting(0): Backing store enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.049] (==) modesetting(0): Silken mouse enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.054] (II) modesetting(0): RandR 1.2 enabled, ignore the following RandR disabled message.[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.057] (==) modesetting(0): DPMS enabled[/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][    25.139] (--) RandR disabled[/COLOR][/SIZE]
[SIZE=2]
How I can fix resolution in 13.10 ??
Can I still use 10-monitor.conf ? which settings ??

Thank you very much.


[/SIZE]

---

### Post by digiteltlc on 2014-05-08
I just kept the new modeset driver, no omapfb or fbset

Just instruct which modeline to use in 10-monitor.conf this way :

Start lXterminal in lxde environment and issue the command

cvt 640 480 60   (horizontal - vertical - rate)

its output will be something like:

# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
[COLOR=#ff0000]Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync[/COLOR] 

[COLOR=#000000]create a new /usr/share/X11/xorg.conf.d/10-monitor.conf inserting the copied RED line in Monitor section this way :

[/COLOR]**[SIZE=1]Section "Monitor"[/SIZE]**
**[SIZE=1]    Identifier             "Monitor0"[/SIZE]**
**[SIZE=1][COLOR=#ff0000]    Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync[/COLOR][/SIZE]**
**[SIZE=1]EndSection[/SIZE]**
[B][SIZE=1]
[/SIZE][/B]
**[SIZE=1]Section "Device"[/SIZE]**
**[SIZE=1]    Identifier             "Device0"[/SIZE]**
**[SIZE=1]EndSection[/SIZE]**
[B][SIZE=1]
[/SIZE][/B]
**[SIZE=1]Section "Screen"[/SIZE]**
**[SIZE=1]    Identifier             "Screen0"  [/SIZE]**
**[SIZE=1]    Device                 "Device0"[/SIZE]**
**[SIZE=1]    Monitor                "Monitor0"[/SIZE]**
**[SIZE=1]    DefaultDepth           16 #Choose the depth (16||24)[/SIZE]**
**[SIZE=1]    SubSection             "Display"[/SIZE]**
**[SIZE=1]        Depth              16[/SIZE]**
**[SIZE=1]        [COLOR=#008000]Modes              "640x480_60.00"[/COLOR] #Choose the resolution, match the Modeline[/SIZE]**
**[SIZE=1]    EndSubSection[/SIZE]**
**[SIZE=1]EndSection[/SIZE]**

Save and reboot, 
it worked for me, hope it helps someone with this problem.

---

