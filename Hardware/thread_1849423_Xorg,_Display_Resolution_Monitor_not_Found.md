---
title: "Xorg, Display Resolution? Monitor not Found?"
date: 2011-09-24
forum: Hardware
---

### Post by JSchultheis on 2011-09-24
My display is 640x480...
I am trying to adjust the display to 1024x768 but seems to be nothing that will work.#-o

I have an Intel card, I run Ubuntu 11.04.
Computer is Dell Inspiron 1100.

System>Preferences>Monitors   : I cannot change the options and it says monitor unknown.:confused:

```
lspci |grep VGA
```00:02.0 VGA compatible controller: [COLOR=Red]Intel[/COLOR] Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)



Now I am ready to start over. 
Where should I start?


Also:
I am very new, but a quick learner!!  :D
I am dual boot: XP/Ubuntu

---

### Post by realzippy on 2011-09-26
Ok,
what does xrandr say ?
```
xrandr -q
```

Which kernel is running ?
```
uname -a
```

---

### Post by JSchultheis on 2011-09-26
```
$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 
```



```
$ uname -a
Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by realzippy on 2011-09-26
```
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
sudo update-initramfs -u -k all
```

Run those commands to add *glasen's* patched intel drivers.
Since Canonical blacklisted i830, i845 und i855 in 11.04,also run:

```
gksudo gedit /etc/X11/xorg.conf
```

Paste in:
```
Section "Device"
Identifier "Card0"
Driver "intel"
EndSection
```

Reboot.
If no success,post again

```
xrandr -q
```

and

```
cat /var/log/Xorg.0.log
```

```
lshw -c video
```

---

### Post by JSchultheis on 2011-09-26
```
$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0*
``````
[    23.453] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    23.453] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.453] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.453] (II) Loader magic: 0x81ffde0
[    23.453] (II) Module ABI versions:
[    23.453]     X.Org ANSI C Emulation: 0.4
[    23.453]     X.Org Video Driver: 10.0
[    23.453]     X.Org XInput driver : 12.3
[    23.453]     X.Org Server Extension : 5.0
[    23.457] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    23.457] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    23.457] (II) LoadModule: "extmod"
[    23.474] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.502] (II) Module extmod: vendor="X.Org Foundation"
[    23.502]     compiled for 1.10.1, module version = 1.0.0
[    23.502]     Module class: X.Org Server Extension
[    23.502]     ABI class: X.Org Server Extension, version 5.0
[    23.502] (II) Loading extension MIT-SCREEN-SAVER
[    23.502] (II) Loading extension XFree86-VidModeExtension
[    23.503] (II) Loading extension XFree86-DGA
[    23.503] (II) Loading extension DPMS
[    23.503] (II) Loading extension XVideo
[    23.503] (II) Loading extension XVideo-MotionCompensation
[    23.503] (II) Loading extension X-Resource
[    23.503] (II) LoadModule: "dbe"
[    23.503] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.513] (II) Module dbe: vendor="X.Org Foundation"
[    23.513]     compiled for 1.10.1, module version = 1.0.0
[    23.513]     Module class: X.Org Server Extension
[    23.513]     ABI class: X.Org Server Extension, version 5.0
[    23.513] (II) Loading extension DOUBLE-BUFFER
[    23.513] (II) LoadModule: "glx"
[    23.514] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.556] (II) Module glx: vendor="X.Org Foundation"
[    23.556]     compiled for 1.10.1, module version = 1.0.0
[    23.556]     ABI class: X.Org Server Extension, version 5.0
[    23.565] (==) AIGLX enabled
[    23.565] (II) Loading extension GLX
[    23.565] (II) LoadModule: "record"
[    23.565] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.582] (II) Module record: vendor="X.Org Foundation"
[    23.583]     compiled for 1.10.1, module version = 1.13.0
[    23.583]     Module class: X.Org Server Extension
[    23.583]     ABI class: X.Org Server Extension, version 5.0
[    23.583] (II) Loading extension RECORD
[    23.583] (II) LoadModule: "dri"
[    23.583] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.587] (II) Module dri: vendor="X.Org Foundation"
[    23.587]     compiled for 1.10.1, module version = 1.0.0
[    23.587]     ABI class: X.Org Server Extension, version 5.0
[    23.587] (II) Loading extension XFree86-DRI
[    23.588] (II) LoadModule: "dri2"
[    23.588] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.590] (II) Module dri2: vendor="X.Org Foundation"
[    23.590]     compiled for 1.10.1, module version = 1.2.0
[    23.590]     ABI class: X.Org Server Extension, version 5.0
[    23.590] (II) Loading extension DRI2
[    23.590] (==) Matched vesa as autoconfigured driver 0
[    23.590] (==) Matched fbdev as autoconfigured driver 1
[    23.590] (==) Assigned the driver to the xf86ConfigLayout
[    23.590] (II) LoadModule: "vesa"
[    23.628] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.640] (II) Module vesa: vendor="X.Org Foundation"
[    23.640]     compiled for 1.10.0, module version = 2.3.0
[    23.640]     Module class: X.Org Video Driver
[    23.640]     ABI class: X.Org Video Driver, version 10.0
[    23.640] (II) LoadModule: "fbdev"
[    23.641] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.659] (II) Module fbdev: vendor="X.Org Foundation"
[    23.659]     compiled for 1.10.0, module version = 0.4.2
[    23.659]     ABI class: X.Org Video Driver, version 10.0
[    23.659] (II) VESA: driver for VESA chipsets: vesa
[    23.659] (II) FBDEV: driver for framebuffer: fbdev
[    23.659] (++) using VT number 7

[    23.660] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    23.660] (WW) Falling back to old probe method for vesa
[    23.660] (II) Loading sub module "fbdevhw"
[    23.660] (II) LoadModule: "fbdevhw"
[    23.661] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.675] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.675]     compiled for 1.10.1, module version = 0.0.2
[    23.675]     ABI class: X.Org Video Driver, version 10.0
[    23.675] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.675] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.676] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    23.676] (II) FBDEV(0): using default device
[    23.676] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.676] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    23.676] (==) FBDEV(0): RGB weight 888
[    23.676] (==) FBDEV(0): Default visual is TrueColor
[    23.676] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.677] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    23.677] (II) FBDEV(0): checking modes against framebuffer device...
[    23.677] (II) FBDEV(0): checking modes against monitor...
[    23.677] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    23.677] (**) FBDEV(0):  Built-in mode "current"
[    23.677] (==) FBDEV(0): DPI set to (96, 96)
[    23.677] (II) Loading sub module "fb"
[    23.677] (II) LoadModule: "fb"
[    23.677] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.702] (II) Module fb: vendor="X.Org Foundation"
[    23.703]     compiled for 1.10.1, module version = 1.0.0
[    23.703]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.703] (**) FBDEV(0): using shadow framebuffer
[    23.703] (II) Loading sub module "shadow"
[    23.703] (II) LoadModule: "shadow"
[    23.704] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    23.705] (II) Module shadow: vendor="X.Org Foundation"
[    23.705]     compiled for 1.10.1, module version = 1.1.0
[    23.706]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.706] (==) Depth 24 pixmap format is 32 bpp
[    23.797] (==) FBDEV(0): Backing store disabled
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.799] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.804] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.812] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.813] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.814] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.840] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.841] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.842] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.843] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.849] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    23.860] (==) FBDEV(0): DPMS enabled
[    23.860] (==) RandR enabled
[    23.860] (II) Initializing built-in extension Generic Event Extension
[    23.861] (II) Initializing built-in extension SHAPE
[    23.861] (II) Initializing built-in extension MIT-SHM
[    23.861] (II) Initializing built-in extension XInputExtension
[    23.861] (II) Initializing built-in extension XTEST
[    23.861] (II) Initializing built-in extension BIG-REQUESTS
[    23.861] (II) Initializing built-in extension SYNC
[    23.861] (II) Initializing built-in extension XKEYBOARD
[    23.861] (II) Initializing built-in extension XC-MISC
[    23.861] (II) Initializing built-in extension SECURITY
[    23.861] (II) Initializing built-in extension XINERAMA
[    23.861] (II) Initializing built-in extension XFIXES
[    23.861] (II) Initializing built-in extension RENDER
[    23.861] (II) Initializing built-in extension RANDR
[    23.861] (II) Initializing built-in extension COMPOSITE
[    23.861] (II) Initializing built-in extension DAMAGE
[    23.861] (II) Initializing built-in extension GESTURE
[    23.919] (II) AIGLX: Screen 0 is not DRI2 capable
[    23.919] (II) AIGLX: Screen 0 is not DRI capable
[    23.919] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    24.099] (II) AIGLX: Loaded and initialized swrast
[    24.099] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    24.733] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.850] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    24.850] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.850] (II) LoadModule: "evdev"
[    24.850] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.023] (II) Module evdev: vendor="X.Org Foundation"
[    25.023]     compiled for 1.10.0.902, module version = 2.6.0
[    25.024]     Module class: X.Org XInput Driver
[    25.024]     ABI class: X.Org XInput driver, version 12.3
[    25.024] (II) Using input driver 'evdev' for 'Video Bus'
[    25.024] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.024] (**) Video Bus: always reports core events
[    25.024] (**) Video Bus: Device: "/dev/input/event4"
[    25.025] (--) Video Bus: Found keys
[    25.025] (II) Video Bus: Configuring as keyboard
[    25.025] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    25.025] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.025] (**) Option "xkb_rules" "evdev"
[    25.025] (**) Option "xkb_model" "pc105"
[    25.025] (**) Option "xkb_layout" "us"
[    25.078] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.078] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.078] (II) Using input driver 'evdev' for 'Power Button'
[    25.078] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.078] (**) Power Button: always reports core events
[    25.078] (**) Power Button: Device: "/dev/input/event1"
[    25.078] (--) Power Button: Found keys
[    25.078] (II) Power Button: Configuring as keyboard
[    25.078] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.079] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.079] (**) Option "xkb_rules" "evdev"
[    25.079] (**) Option "xkb_model" "pc105"
[    25.079] (**) Option "xkb_layout" "us"
[    25.081] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.081] (II) No input driver/identifier specified (ignoring)
[    25.091] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.091] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.091] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.091] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.091] (**) Sleep Button: always reports core events
[    25.091] (**) Sleep Button: Device: "/dev/input/event2"
[    25.091] (--) Sleep Button: Found keys
[    25.096] (II) Sleep Button: Configuring as keyboard
[    25.097] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.098] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.098] (**) Option "xkb_rules" "evdev"
[    25.098] (**) Option "xkb_model" "pc105"
[    25.098] (**) Option "xkb_layout" "us"
[    25.187] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.192] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.192] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.192] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.192] (**) AT Translated Set 2 keyboard: always reports core events
[    25.192] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.192] (--) AT Translated Set 2 keyboard: Found keys
[    25.192] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.193] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.193] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.193] (**) Option "xkb_rules" "evdev"
[    25.193] (**) Option "xkb_model" "pc105"
[    25.193] (**) Option "xkb_layout" "us"
[    25.195] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.195] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.195] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.195] (II) LoadModule: "synaptics"
[    25.200] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.216] (II) Module synaptics: vendor="X.Org Foundation"
[    25.216]     compiled for 1.10.1, module version = 1.3.99
[    25.216]     Module class: X.Org XInput Driver
[    25.216]     ABI class: X.Org XInput driver, version 12.3
[    25.216] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.216] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.217] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.217] (**) Option "Device" "/dev/input/event5"
[    25.217] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.217] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.217] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.217] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.217] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.217] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.218] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.218] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    25.218] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.218] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.218] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.218] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    25.219] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.219] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.219] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.219] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.219] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    25.219] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.225] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.225] (II) No input driver/identifier specified (ignoring)

```I couldn't scroll up to capture all of the cat /var/log/Xorg.0.log is there another way to do it?

Also, this is my Xorg.conf:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "Dell 1024x768 Laptop Display Panel"
        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection

Section "Device"
Identifier "Card0"
Driver "intel"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
        EndSubsection
EndSection
```

---

### Post by realzippy on 2011-09-26
Where does all that strange content from your xorg.conf come from?
Normally you should have any xorg.conf....
Have you done anything else I should know?
EG some blacklisting,editing boot options,or similar?
Tried to install (outdated) intel graphic drivers?

So,move existing xorg.conf out of the way.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.strange
```

Then again:
```
gksudo gedit /etc/X11/xorg.conf
```
Paste in (anything else!) :
```
Section "Device"
Identifier "Card0"
Driver "intel"
EndSection
```
Close file saving changes.

Reboot.
If not better (likely),
show
```
gedit /var/log/Xorg.0.log
```
(this time with text editor "gedit"   ;-)  )

```
lshw -c video
```

---

### Post by .... on 2011-09-26
> Also, this is my Xorg.conf..:
I suspect you need to increase the range of horizsync in that example (30-82 is common). Even without the intel driver, you should still be able to get 1024x768 with the fbdev or vesa driver.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)
Example xorg.conf's are given in that link. You should also add the horizsync and vertrefresh options to the monitor section because older displays often report no/incorrect edid info and X uses conservative values.

---

### Post by realzippy on 2011-09-26
> **.... said:**
>  Even without the intel driver, you should still be able to get 1024x768 with the fbdev or vesa driver.


yep,but I prefer the intel driver...if there is no way
(waiting for log) vesa will be next shot.

---

### Post by JSchultheis on 2011-09-26
Well I am replying from a full display, realzippy! Thanks, realzippy, I think you have fixed my problem!

Only thing is, I have seen a message on startup a few times before the full screen started. I restarted until I could copy the message:

```
ureadahead main process (204) terminated with status 5
```Actually it stopped the last couple of times (?). I realize that maybe this is pertaining to another process, if so np.

----------

```
gedit /var/log/Xorg.0.log
``````
[    25.033] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    25.034] X Protocol Version 11, Revision 0
[    25.034] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    25.034] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    25.034] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    25.034] Build Date: 11 August 2011  03:47:56PM
[    25.034] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    25.035] Current version of pixman: 0.20.2
[    25.035]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    25.035] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.035] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 11:07:15 2011
[    25.065] (==) Using config file: "/etc/X11/xorg.conf"
[    25.065] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.130] (==) No Layout section.  Using the first Screen section.
[    25.131] (==) No screen section available. Using defaults.
[    25.131] (**) |-->Screen "Default Screen Section" (0)
[    25.131] (**) |   |-->Monitor "<default monitor>"
[    25.132] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    25.132] (**) |   |-->Device "Card0"
[    25.132] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    25.132] (==) Automatically adding devices
[    25.132] (==) Automatically enabling devices
[    25.145] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.145]     Entry deleted from font path.
[    25.146] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.146]     Entry deleted from font path.
[    25.146] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.146]     Entry deleted from font path.
[    25.157] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.157]     Entry deleted from font path.
[    25.157] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.158]     Entry deleted from font path.
[    25.172] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    25.172] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.172] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.172] (II) Loader magic: 0x81ffde0
[    25.172] (II) Module ABI versions:
[    25.172]     X.Org ANSI C Emulation: 0.4
[    25.172]     X.Org Video Driver: 10.0
[    25.172]     X.Org XInput driver : 12.3
[    25.172]     X.Org Server Extension : 5.0
[    25.181] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    25.181] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    25.182] (II) LoadModule: "extmod"
[    25.208] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.235] (II) Module extmod: vendor="X.Org Foundation"
[    25.235]     compiled for 1.10.1, module version = 1.0.0
[    25.236]     Module class: X.Org Server Extension
[    25.236]     ABI class: X.Org Server Extension, version 5.0
[    25.236] (II) Loading extension MIT-SCREEN-SAVER
[    25.236] (II) Loading extension XFree86-VidModeExtension
[    25.236] (II) Loading extension XFree86-DGA
[    25.236] (II) Loading extension DPMS
[    25.236] (II) Loading extension XVideo
[    25.236] (II) Loading extension XVideo-MotionCompensation
[    25.236] (II) Loading extension X-Resource
[    25.236] (II) LoadModule: "dbe"
[    25.237] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.260] (II) Module dbe: vendor="X.Org Foundation"
[    25.260]     compiled for 1.10.1, module version = 1.0.0
[    25.260]     Module class: X.Org Server Extension
[    25.261]     ABI class: X.Org Server Extension, version 5.0
[    25.261] (II) Loading extension DOUBLE-BUFFER
[    25.261] (II) LoadModule: "glx"
[    25.262] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.303] (II) Module glx: vendor="X.Org Foundation"
[    25.304]     compiled for 1.10.1, module version = 1.0.0
[    25.304]     ABI class: X.Org Server Extension, version 5.0
[    25.312] (==) AIGLX enabled
[    25.312] (II) Loading extension GLX
[    25.312] (II) LoadModule: "record"
[    25.313] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.315] (II) Module record: vendor="X.Org Foundation"
[    25.315]     compiled for 1.10.1, module version = 1.13.0
[    25.315]     Module class: X.Org Server Extension
[    25.315]     ABI class: X.Org Server Extension, version 5.0
[    25.316] (II) Loading extension RECORD
[    25.316] (II) LoadModule: "dri"
[    25.317] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.321] (II) Module dri: vendor="X.Org Foundation"
[    25.322]     compiled for 1.10.1, module version = 1.0.0
[    25.322]     ABI class: X.Org Server Extension, version 5.0
[    25.322] (II) Loading extension XFree86-DRI
[    25.322] (II) LoadModule: "dri2"
[    25.323] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.333] (II) Module dri2: vendor="X.Org Foundation"
[    25.333]     compiled for 1.10.1, module version = 1.2.0
[    25.333]     ABI class: X.Org Server Extension, version 5.0
[    25.333] (II) Loading extension DRI2
[    25.333] (II) LoadModule: "intel"
[    25.360] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.411] (II) Module intel: vendor="X.Org Foundation"
[    25.412]     compiled for 1.10.1, module version = 2.15.0
[    25.412]     Module class: X.Org Video Driver
[    25.412]     ABI class: X.Org Video Driver, version 10.0
[    25.412] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    25.425] (++) using VT number 7

[    25.448] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.449] drmOpenDevice: node name is /dev/dri/card0
[    25.449] drmOpenDevice: open result is 8, (OK)
[    25.450] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.450] drmOpenDevice: node name is /dev/dri/card0
[    25.450] drmOpenDevice: open result is 8, (OK)
[    25.450] drmOpenByBusid: drmOpenMinor returns 8
[    25.450] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.450] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.450] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.450] (==) intel(0): RGB weight 888
[    25.451] (==) intel(0): Default visual is TrueColor
[    25.451] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    25.451] (--) intel(0): Chipset: "845G"
[    25.451] (**) intel(0): Relaxed fencing disabled
[    25.451] (**) intel(0): Framebuffer tiled
[    25.451] (**) intel(0): Pixmaps tiled
[    25.457] (**) intel(0): 3D buffers tiled
[    25.457] (**) intel(0): SwapBuffers wait enabled
[    25.457] (==) intel(0): video overlay key set to 0x101fe
[    25.537] (II) intel(0): Output VGA1 has no monitor section
[    25.573] (II) intel(0): Output LVDS1 has no monitor section
[    25.648] (II) intel(0): EDID for output VGA1
[    25.649] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    25.649] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    25.649] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    25.649] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    25.650] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    25.650] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    25.650] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    25.650] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.650] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.651] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.651] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.651] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.651] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.651] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.651] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.651] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.651] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.651] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    25.651] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    25.660] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.660] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    25.660] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.660] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    25.660] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.660] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    25.660] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.660] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.661] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.661] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    25.661] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.661] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    25.661] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.661] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    25.661] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.661] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    25.661] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.661] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    25.661] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.662] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.662] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.662] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.662] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.662] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.662] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.662] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.662] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.663] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.663] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.663] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    25.663] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.663] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    25.663] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.663] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    25.663] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.663] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    25.663] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.672] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    25.672] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.672] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    25.672] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.672] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    25.672] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    25.672] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.672] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.672] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.673] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.673] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.673] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.673] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.673] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.673] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.673] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.673] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.673] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    25.673] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.674] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    25.674] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    25.674] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    25.674] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    25.674] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.674] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    25.675] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.675] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.675] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.675] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.675] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.675] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    25.675] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.675] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    25.675] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.684] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    25.684] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.684] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    25.684] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.684] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    25.684] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.684] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    25.684] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.685] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    25.685] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.685] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    25.685] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.685] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    25.685] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.685] (II) intel(0): Printing probed modes for output VGA1
[    25.685] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.685] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    25.686] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.686] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.686] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.721] (II) intel(0): EDID for output LVDS1
[    25.722] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.722] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.722] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.722] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.722] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.723] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.732] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.732] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.732] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.732] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.732] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.732] (II) intel(0): Printing probed modes for output LVDS1
[    25.732] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
[    25.733] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.733] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.733] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.733] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.733] (II) intel(0): Output VGA1 disconnected
[    25.733] (II) intel(0): Output LVDS1 connected
[    25.733] (II) intel(0): Using exact sizes for initial modes
[    25.733] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    25.734] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.734] (II) intel(0): Kernel page flipping support detected, enabling
[    25.734] (==) intel(0): DPI set to (96, 96)
[    25.734] (II) Loading sub module "fb"
[    25.734] (II) LoadModule: "fb"
[    25.735] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.764] (II) Module fb: vendor="X.Org Foundation"
[    25.764]     compiled for 1.10.1, module version = 1.0.0
[    25.764]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.764] (II) Loading sub module "dri2"
[    25.764] (II) LoadModule: "dri2"
[    25.765] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.766] (II) Module dri2: vendor="X.Org Foundation"
[    25.766]     compiled for 1.10.1, module version = 1.2.0
[    25.766]     ABI class: X.Org Server Extension, version 5.0
[    25.766] (==) Depth 24 pixmap format is 32 bpp
[    25.766] (II) intel(0): [DRI2] Setup complete
[    25.767] (II) intel(0): [DRI2]   DRI driver: i915
[    25.767] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    25.810] (II) UXA(0): Driver registered support for the following operations:
[    25.810] (II)         solid
[    25.810] (II)         copy
[    25.810] (II)         composite (RENDER acceleration)
[    25.810] (II)         put_image
[    25.810] (II)         get_image
[    25.810] (==) intel(0): Backing store disabled
[    25.810] (==) intel(0): Silken mouse enabled
[    25.816] (II) intel(0): Initializing HW Cursor
[    25.880] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.881] (==) intel(0): DPMS enabled
[    25.881] (==) intel(0): Intel XvMC decoder disabled
[    25.881] (II) intel(0): Set up overlay video
[    25.881] (II) intel(0): direct rendering: DRI2 Enabled
[    25.881] (==) intel(0): hotplug detection: "enabled"
[    25.882] (--) RandR disabled
[    25.882] (II) Initializing built-in extension Generic Event Extension
[    25.882] (II) Initializing built-in extension SHAPE
[    25.882] (II) Initializing built-in extension MIT-SHM
[    25.882] (II) Initializing built-in extension XInputExtension
[    25.883] (II) Initializing built-in extension XTEST
[    25.883] (II) Initializing built-in extension BIG-REQUESTS
[    25.883] (II) Initializing built-in extension SYNC
[    25.883] (II) Initializing built-in extension XKEYBOARD
[    25.883] (II) Initializing built-in extension XC-MISC
[    25.883] (II) Initializing built-in extension SECURITY
[    25.883] (II) Initializing built-in extension XINERAMA
[    25.883] (II) Initializing built-in extension XFIXES
[    25.883] (II) Initializing built-in extension RENDER
[    25.883] (II) Initializing built-in extension RANDR
[    25.883] (II) Initializing built-in extension COMPOSITE
[    25.883] (II) Initializing built-in extension DAMAGE
[    25.883] (II) Initializing built-in extension GESTURE
[    25.978] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    26.224] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.224] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.224] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.224] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.225] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.225] (II) AIGLX: Loaded and initialized i915
[    26.225] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.232] (II) intel(0): Setting screen physical size to 270 x 203
[    26.495] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.722] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.722] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.722] (II) LoadModule: "evdev"
[    26.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.785] (II) Module evdev: vendor="X.Org Foundation"
[    26.785]     compiled for 1.10.0.902, module version = 2.6.0
[    26.785]     Module class: X.Org XInput Driver
[    26.785]     ABI class: X.Org XInput driver, version 12.3
[    26.785] (II) Using input driver 'evdev' for 'Video Bus'
[    26.785] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.786] (**) Video Bus: always reports core events
[    26.786] (**) Video Bus: Device: "/dev/input/event4"
[    26.786] (--) Video Bus: Found keys
[    26.786] (II) Video Bus: Configuring as keyboard
[    26.787] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    26.787] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.787] (**) Option "xkb_rules" "evdev"
[    26.787] (**) Option "xkb_model" "pc105"
[    26.787] (**) Option "xkb_layout" "us"
[    26.928] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.979] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.979] (II) Using input driver 'evdev' for 'Power Button'
[    26.979] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.979] (**) Power Button: always reports core events
[    26.980] (**) Power Button: Device: "/dev/input/event1"
[    26.980] (--) Power Button: Found keys
[    26.980] (II) Power Button: Configuring as keyboard
[    26.980] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.980] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.981] (**) Option "xkb_rules" "evdev"
[    26.981] (**) Option "xkb_model" "pc105"
[    26.981] (**) Option "xkb_layout" "us"
[    26.992] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.993] (II) No input driver/identifier specified (ignoring)
[    26.995] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.995] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.995] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.004] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.004] (**) Sleep Button: always reports core events
[    27.004] (**) Sleep Button: Device: "/dev/input/event2"
[    27.004] (--) Sleep Button: Found keys
[    27.005] (II) Sleep Button: Configuring as keyboard
[    27.005] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    27.005] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    27.005] (**) Option "xkb_rules" "evdev"
[    27.005] (**) Option "xkb_model" "pc105"
[    27.005] (**) Option "xkb_layout" "us"
[    27.230] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.230] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.231] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.231] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.231] (**) AT Translated Set 2 keyboard: always reports core events
[    27.231] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.240] (--) AT Translated Set 2 keyboard: Found keys
[    27.240] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    27.240] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    27.240] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    27.240] (**) Option "xkb_rules" "evdev"
[    27.240] (**) Option "xkb_model" "pc105"
[    27.241] (**) Option "xkb_layout" "us"
[    27.252] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    27.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.253] (II) LoadModule: "synaptics"
[    27.253] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.277] (II) Module synaptics: vendor="X.Org Foundation"
[    27.277]     compiled for 1.10.1, module version = 1.3.99
[    27.278]     Module class: X.Org XInput Driver
[    27.278]     ABI class: X.Org XInput driver, version 12.3
[    27.278] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.278] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.278] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.279] (**) Option "Device" "/dev/input/event5"
[    27.279] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    27.279] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    27.279] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.279] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.280] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    27.280] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.280] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.280] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    27.280] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    27.281] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.281] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    27.281] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    27.282] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.282] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.282] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.282] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.283] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    27.283] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.293] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.293] (II) No input driver/identifier specified (ignoring)
[   212.972] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[   212.972] (EE) intel(0): When reporting this, please include i915_error_state from debugfs and the full dmesg.
``````
lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff memory:f6f80000-f6ffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```Any follow up? I plan to restart a few times to make sure that it sticks, if so I will post that and switch the thread to solved.

---

### Post by JSchultheis on 2011-09-26
just seems to hang at startup... so at black-screen-of-death, I force powercycle


getting small screen still sometimes

---

### Post by realzippy on 2011-09-26
According logs i915 driver running at @1024x768 now....
but last lines:
```
[   212.972] (EE) intel(0): Detected a hung GPU, disabling acceleration.
```

Everything running smoothly?

---

### Post by JSchultheis on 2011-09-26
> **.... said:**
> I suspect you need to increase the range of horizsync in that example (30-82 is common). Even without the intel driver, you should still be able to get 1024x768 with the fbdev or vesa driver.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)
Example xorg.conf's are given in that link. You should also add the horizsync and vertrefresh options to the monitor section because older displays often report no/incorrect edid info and X uses conservative values.

That Xorg.conf has been mv and is now

```
Section "Device"
Identifier "Card0"
Driver "intel"
EndSection
```

---

### Post by JSchultheis on 2011-09-26
> **realzippy said:**
> According logs i915 driver running at @1024x768 now....
but last lines:
```
[   212.972] (EE) intel(0): Detected a hung GPU, disabling acceleration.
```

Everything running smoothly?

ummm, no not yet :D

it hangs or starts with small screen

---

### Post by realzippy on 2011-09-26
edit xorg.conf again,
add
```
Option "DRI" "false"
```
to device section..

```
gksudo gedit /etc/X11/xorg.conf

```
```
Section "Device"
Identifier "Card0"
Driver "intel"
Option "DRI" "false"
EndSection
```

...reboot.

Then post output from:

```
fgrep '(EE)' /var/log/Xorg.0.log
```

---

### Post by JSchultheis on 2011-09-26
sorry about the delay and thank you for continuing on with the help. the delay is only because the monitor is hanging. anyway:


```
fgrep '(EE)' /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    61.029] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[    61.029] (EE) intel(0): When reporting this, please include i915_error_state from debugfs and the full dmesg.

```

------

Also: when I go to system>preferences>monitors, the display does now show 'Laptop' ! although "Resolution" does not allow me to change it still. But that is some success :)

---

### Post by realzippy on 2011-09-26
Ok,
I have no idea for the inteldriver.
Suggest we get back;first purge the intel driver modifications
by glasen:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
sudo update-initramfs -u -k all
```

Then delete the just added
```
Option "DRI" "false"

```
from xorg.conf.
Then reboot.
After reboot,post:
```
xrandr -q
```
and whole X log file again:
```
gedit /var/log/Xorg.0.log
```

---

### Post by JSchultheis on 2011-09-26
```
sudo ppa-purge ppa:glasen/libdrm
Updating packages lists
PPA to be removed: glasen libdrm
Warning:  Could not find package list for PPA: glasen libdrm
```
 
but I will continue through the order of sudo processes

---

### Post by realzippy on 2011-09-26
Ignore this.My mistake.No libdrm ppa to purge.All good..  ;-)

---

### Post by JSchultheis on 2011-09-26
:)

```
xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9
```

---

### Post by realzippy on 2011-09-26
edit.
sorry,you seem to be at 640x480 now?
Please,the Xorg.0.log file also....

---

### Post by JSchultheis on 2011-09-26
```
[    23.868] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    23.869] X Protocol Version 11, Revision 0
[    23.869] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    23.869] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    23.869] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    23.869] Build Date: 11 August 2011  03:47:56PM
[    23.869] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    23.869] Current version of pixman: 0.20.2
[    23.869]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.870] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.870] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 13:19:05 2011
[    23.915] (==) Using config file: "/etc/X11/xorg.conf"
[    23.915] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.099] (==) No Layout section.  Using the first Screen section.
[    24.099] (==) No screen section available. Using defaults.
[    24.100] (**) |-->Screen "Default Screen Section" (0)
[    24.100] (**) |   |-->Monitor "<default monitor>"
[    24.100] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    24.100] (**) |   |-->Device "Card0"
[    24.100] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.100] (==) Automatically adding devices
[    24.101] (==) Automatically enabling devices
[    24.142] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.142]     Entry deleted from font path.
[    24.142] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.142]     Entry deleted from font path.
[    24.142] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.142]     Entry deleted from font path.
[    24.143] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.143]     Entry deleted from font path.
[    24.143] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.143]     Entry deleted from font path.
[    24.178] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.178] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.178] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.178] (II) Loader magic: 0x81ffde0
[    24.178] (II) Module ABI versions:
[    24.178]     X.Org ANSI C Emulation: 0.4
[    24.178]     X.Org Video Driver: 10.0
[    24.179]     X.Org XInput driver : 12.3
[    24.179]     X.Org Server Extension : 5.0
[    24.181] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    24.181] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.182] (II) LoadModule: "extmod"
[    24.215] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.256] (II) Module extmod: vendor="X.Org Foundation"
[    24.256]     compiled for 1.10.1, module version = 1.0.0
[    24.256]     Module class: X.Org Server Extension
[    24.256]     ABI class: X.Org Server Extension, version 5.0
[    24.256] (II) Loading extension MIT-SCREEN-SAVER
[    24.256] (II) Loading extension XFree86-VidModeExtension
[    24.256] (II) Loading extension XFree86-DGA
[    24.258] (II) Loading extension DPMS
[    24.259] (II) Loading extension XVideo
[    24.259] (II) Loading extension XVideo-MotionCompensation
[    24.259] (II) Loading extension X-Resource
[    24.259] (II) LoadModule: "dbe"
[    24.259] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.299] (II) Module dbe: vendor="X.Org Foundation"
[    24.300]     compiled for 1.10.1, module version = 1.0.0
[    24.300]     Module class: X.Org Server Extension
[    24.300]     ABI class: X.Org Server Extension, version 5.0
[    24.300] (II) Loading extension DOUBLE-BUFFER
[    24.300] (II) LoadModule: "glx"
[    24.301] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.353] (II) Module glx: vendor="X.Org Foundation"
[    24.353]     compiled for 1.10.1, module version = 1.0.0
[    24.353]     ABI class: X.Org Server Extension, version 5.0
[    24.362] (==) AIGLX enabled
[    24.362] (II) Loading extension GLX
[    24.363] (II) LoadModule: "record"
[    24.364] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.396] (II) Module record: vendor="X.Org Foundation"
[    24.396]     compiled for 1.10.1, module version = 1.13.0
[    24.396]     Module class: X.Org Server Extension
[    24.396]     ABI class: X.Org Server Extension, version 5.0
[    24.396] (II) Loading extension RECORD
[    24.396] (II) LoadModule: "dri"
[    24.397] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.420] (II) Module dri: vendor="X.Org Foundation"
[    24.421]     compiled for 1.10.1, module version = 1.0.0
[    24.421]     ABI class: X.Org Server Extension, version 5.0
[    24.421] (II) Loading extension XFree86-DRI
[    24.421] (II) LoadModule: "dri2"
[    24.421] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.528] (II) Module dri2: vendor="X.Org Foundation"
[    24.528]     compiled for 1.10.1, module version = 1.2.0
[    24.529]     ABI class: X.Org Server Extension, version 5.0
[    24.529] (II) Loading extension DRI2
[    24.529] (II) LoadModule: "intel"
[    24.555] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.612] (II) Module intel: vendor="X.Org Foundation"
[    24.612]     compiled for 1.10.1, module version = 2.14.0
[    24.613]     Module class: X.Org Video Driver
[    24.613]     ABI class: X.Org Video Driver, version 10.0
[    24.613] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    24.615] (++) using VT number 7

[    24.625] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.626] drmOpenDevice: node name is /dev/dri/card0
[    24.626] drmOpenDevice: open result is 8, (OK)
[    24.626] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.626] drmOpenDevice: node name is /dev/dri/card0
[    24.626] drmOpenDevice: open result is 8, (OK)
[    24.626] drmOpenByBusid: drmOpenMinor returns 8
[    24.626] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.627] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.627] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.627] (==) intel(0): RGB weight 888
[    24.632] (==) intel(0): Default visual is TrueColor
[    24.632] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    24.632] (--) intel(0): Chipset: "845G"
[    24.632] (**) intel(0): Relaxed fencing disabled
[    24.632] (**) intel(0): Tiling enabled
[    24.632] (**) intel(0): SwapBuffers wait enabled
[    24.632] (==) intel(0): video overlay key set to 0x101fe
[    24.681] (II) intel(0): Output VGA1 has no monitor section
[    24.701] (II) intel(0): Output LVDS1 has no monitor section
[    24.749] (II) intel(0): EDID for output VGA1
[    24.749] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    24.749] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    24.749] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    24.749] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    24.749] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.750] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    24.750] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    24.751] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    24.751] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.751] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    24.751] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.752] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.756] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.756] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.756] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    24.757] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    24.757] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    24.757] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    24.757] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    24.757] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    24.757] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    24.757] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.757] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.757] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    24.758] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    24.758] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.758] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.758] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.759] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    24.759] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    24.759] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.759] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.759] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.759] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.759] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.759] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.759] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    24.761] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    24.761] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    24.761] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    24.761] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    24.761] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.761] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    24.761] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.761] (II) intel(0): Printing probed modes for output VGA1
[    24.761] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.762] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    24.762] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.762] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.762] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.789] (II) intel(0): EDID for output LVDS1
[    24.789] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.789] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.789] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.789] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.789] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.789] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.790] (II) intel(0): Printing probed modes for output LVDS1
[    24.790] (II) intel(0): Modeline "640x480"x60.0   65.00  640 856 992 1344  480 627 633 806 (48.4 kHz)
[    24.790] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.790] (II) intel(0): Output VGA1 disconnected
[    24.790] (II) intel(0): Output LVDS1 connected
[    24.790] (II) intel(0): Using exact sizes for initial modes
[    24.790] (II) intel(0): Output LVDS1 using initial mode 640x480
[    24.790] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.790] (II) intel(0): Kernel page flipping support detected, enabling
[    24.790] (==) intel(0): DPI set to (96, 96)
[    24.790] (II) Loading sub module "fb"
[    24.790] (II) LoadModule: "fb"
[    24.791] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.813] (II) Module fb: vendor="X.Org Foundation"
[    24.813]     compiled for 1.10.1, module version = 1.0.0
[    24.813]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.813] (==) Depth 24 pixmap format is 32 bpp
[    24.814] (==) intel(0): VideoRam: 131072 KB
[    24.814] (II) intel(0): [DRI2] Setup complete
[    24.814] (II) intel(0): [DRI2]   DRI driver: i915
[    24.814] (II) intel(0): Allocated new frame buffer 640x480 stride 4096, tiled
[    24.872] (II) UXA(0): Driver registered support for the following operations:
[    24.872] (II)         solid
[    24.872] (II)         copy
[    24.872] (II)         composite (RENDER acceleration)
[    24.872] (II)         put_image
[    24.872] (II)         get_image
[    24.872] (==) intel(0): Backing store disabled
[    24.872] (==) intel(0): Silken mouse enabled
[    24.894] (II) intel(0): Initializing HW Cursor
[    24.916] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.916] (==) intel(0): DPMS enabled
[    24.916] (==) intel(0): Intel XvMC decoder disabled
[    24.917] (II) intel(0): Set up overlay video
[    24.917] (II) intel(0): direct rendering: DRI2 Enabled
[    24.917] (==) intel(0): hotplug detection: "enabled"
[    24.917] (--) RandR disabled
[    24.917] (II) Initializing built-in extension Generic Event Extension
[    24.917] (II) Initializing built-in extension SHAPE
[    24.917] (II) Initializing built-in extension MIT-SHM
[    24.917] (II) Initializing built-in extension XInputExtension
[    24.918] (II) Initializing built-in extension XTEST
[    24.918] (II) Initializing built-in extension BIG-REQUESTS
[    24.918] (II) Initializing built-in extension SYNC
[    24.918] (II) Initializing built-in extension XKEYBOARD
[    24.918] (II) Initializing built-in extension XC-MISC
[    24.918] (II) Initializing built-in extension SECURITY
[    24.918] (II) Initializing built-in extension XINERAMA
[    24.918] (II) Initializing built-in extension XFIXES
[    24.918] (II) Initializing built-in extension RENDER
[    24.918] (II) Initializing built-in extension RANDR
[    24.918] (II) Initializing built-in extension COMPOSITE
[    24.918] (II) Initializing built-in extension DAMAGE
[    24.918] (II) Initializing built-in extension GESTURE
[    25.000] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    25.245] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.245] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.245] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.245] (II) AIGLX: enabled GLX_SGI_make_current_read
[    25.245] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.245] (II) AIGLX: Loaded and initialized i915
[    25.245] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.247] (II) intel(0): Setting screen physical size to 169 x 126
[    25.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.593] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.593] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.594] (II) LoadModule: "evdev"
[    25.594] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.663] (II) Module evdev: vendor="X.Org Foundation"
[    25.663]     compiled for 1.10.0.902, module version = 2.6.0
[    25.663]     Module class: X.Org XInput Driver
[    25.663]     ABI class: X.Org XInput driver, version 12.3
[    25.663] (II) Using input driver 'evdev' for 'Video Bus'
[    25.663] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.663] (**) Video Bus: always reports core events
[    25.663] (**) Video Bus: Device: "/dev/input/event4"
[    25.664] (--) Video Bus: Found keys
[    25.664] (II) Video Bus: Configuring as keyboard
[    25.664] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    25.664] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.664] (**) Option "xkb_rules" "evdev"
[    25.664] (**) Option "xkb_model" "pc105"
[    25.664] (**) Option "xkb_layout" "us"
[    25.712] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.712] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.713] (II) Using input driver 'evdev' for 'Power Button'
[    25.713] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.713] (**) Power Button: always reports core events
[    25.713] (**) Power Button: Device: "/dev/input/event1"
[    25.713] (--) Power Button: Found keys
[    25.713] (II) Power Button: Configuring as keyboard
[    25.713] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.713] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.713] (**) Option "xkb_rules" "evdev"
[    25.714] (**) Option "xkb_model" "pc105"
[    25.714] (**) Option "xkb_layout" "us"
[    25.721] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.721] (II) No input driver/identifier specified (ignoring)
[    25.723] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.723] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.723] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.724] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.724] (**) Sleep Button: always reports core events
[    25.724] (**) Sleep Button: Device: "/dev/input/event2"
[    25.724] (--) Sleep Button: Found keys
[    25.724] (II) Sleep Button: Configuring as keyboard
[    25.724] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.724] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.724] (**) Option "xkb_rules" "evdev"
[    25.725] (**) Option "xkb_model" "pc105"
[    25.725] (**) Option "xkb_layout" "us"
[    25.805] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.806] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.806] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.806] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.806] (**) AT Translated Set 2 keyboard: always reports core events
[    25.806] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.806] (--) AT Translated Set 2 keyboard: Found keys
[    25.806] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.806] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.806] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.806] (**) Option "xkb_rules" "evdev"
[    25.807] (**) Option "xkb_model" "pc105"
[    25.807] (**) Option "xkb_layout" "us"
[    25.809] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.809] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.809] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.809] (II) LoadModule: "synaptics"
[    25.810] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.827] (II) Module synaptics: vendor="X.Org Foundation"
[    25.827]     compiled for 1.10.1, module version = 1.3.99
[    25.827]     Module class: X.Org XInput Driver
[    25.827]     ABI class: X.Org XInput driver, version 12.3
[    25.827] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.827] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.828] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.828] (**) Option "Device" "/dev/input/event5"
[    25.828] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.828] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.828] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.828] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.828] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.828] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.829] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.829] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    25.829] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.829] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.829] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.829] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    25.830] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.830] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.830] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.830] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.836] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    25.836] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.837] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.837] (II) No input driver/identifier specified (ignoring)
```

---

### Post by realzippy on 2011-09-26
...something strange happened.
I never saw such an xrandr output,and I have seen a few.
Move current xorg.conf also:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.glasen
```

Reboot.
Then again xrandr output,
and -pleeeease- also the actual
Xorg.0.log file's content.

---

### Post by JSchultheis on 2011-09-26
> **realzippy said:**
> ...something strange happened.
I never saw such an xrandr output,and I have seen a few.
Move current xorg.conf also:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.glasen
```Reboot.
Then again xrandr output,
and -pleeeease- also the actual
Xorg.0.log file's content.


I have mv the xorg.conf.

also:

```
fgrep '(EE)' /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```


or which code do I use to post the actual Xorg.o.log file?

before I used 
```
gedit /var/log/Xorg.0.log

```

although I think we posted at the same time. 

I'm sorry to be creating more work and will make an effort to post less erratically! Thank you for continued help :D

---

### Post by realzippy on 2011-09-26
Ok,
now you have moved xorg.conf and rebooted.
Also Xorg.0.log shows no errors.
Btw,if you wonder why I always want the Xorg.0.log:
It gets created at every boot.
0.log then becomes 1.log,aso.

Now the output from 

```
xrandr -q
```

again.Last xrandr (you deleted when editing) showed a strange output...

---

### Post by JSchultheis on 2011-09-26
cool to know, I didn't realize it was a new boot thing.

so this is since a new boot:


```
gedit /var/log/Xorg.0.log

```

```
[    23.849] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    23.849] X Protocol Version 11, Revision 0
[    23.850] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    23.850] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    23.850] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    23.850] Build Date: 11 August 2011  03:47:56PM
[    23.850] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    23.850] Current version of pixman: 0.20.2
[    23.850]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.850] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.851] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 13:42:53 2011
[    23.927] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.182] (==) No Layout section.  Using the first Screen section.
[    24.182] (==) No screen section available. Using defaults.
[    24.182] (**) |-->Screen "Default Screen Section" (0)
[    24.182] (**) |   |-->Monitor "<default monitor>"
[    24.183] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.183] (==) Automatically adding devices
[    24.183] (==) Automatically enabling devices
[    24.217] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.217]     Entry deleted from font path.
[    24.217] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.217]     Entry deleted from font path.
[    24.217] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.217]     Entry deleted from font path.
[    24.244] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.244]     Entry deleted from font path.
[    24.244] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.244]     Entry deleted from font path.
[    24.258] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.258] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.258] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.258] (II) Loader magic: 0x81ffde0
[    24.258] (II) Module ABI versions:
[    24.258]     X.Org ANSI C Emulation: 0.4
[    24.258]     X.Org Video Driver: 10.0
[    24.258]     X.Org XInput driver : 12.3
[    24.258]     X.Org Server Extension : 5.0
[    24.261] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    24.261] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.261] (II) LoadModule: "extmod"
[    24.279] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.307] (II) Module extmod: vendor="X.Org Foundation"
[    24.307]     compiled for 1.10.1, module version = 1.0.0
[    24.307]     Module class: X.Org Server Extension
[    24.307]     ABI class: X.Org Server Extension, version 5.0
[    24.308] (II) Loading extension MIT-SCREEN-SAVER
[    24.308] (II) Loading extension XFree86-VidModeExtension
[    24.308] (II) Loading extension XFree86-DGA
[    24.308] (II) Loading extension DPMS
[    24.308] (II) Loading extension XVideo
[    24.308] (II) Loading extension XVideo-MotionCompensation
[    24.308] (II) Loading extension X-Resource
[    24.308] (II) LoadModule: "dbe"
[    24.309] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.318] (II) Module dbe: vendor="X.Org Foundation"
[    24.318]     compiled for 1.10.1, module version = 1.0.0
[    24.318]     Module class: X.Org Server Extension
[    24.318]     ABI class: X.Org Server Extension, version 5.0
[    24.318] (II) Loading extension DOUBLE-BUFFER
[    24.318] (II) LoadModule: "glx"
[    24.319] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.361] (II) Module glx: vendor="X.Org Foundation"
[    24.361]     compiled for 1.10.1, module version = 1.0.0
[    24.361]     ABI class: X.Org Server Extension, version 5.0
[    24.370] (==) AIGLX enabled
[    24.370] (II) Loading extension GLX
[    24.370] (II) LoadModule: "record"
[    24.371] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.388] (II) Module record: vendor="X.Org Foundation"
[    24.388]     compiled for 1.10.1, module version = 1.13.0
[    24.388]     Module class: X.Org Server Extension
[    24.388]     ABI class: X.Org Server Extension, version 5.0
[    24.388] (II) Loading extension RECORD
[    24.388] (II) LoadModule: "dri"
[    24.389] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.392] (II) Module dri: vendor="X.Org Foundation"
[    24.392]     compiled for 1.10.1, module version = 1.0.0
[    24.392]     ABI class: X.Org Server Extension, version 5.0
[    24.393] (II) Loading extension XFree86-DRI
[    24.393] (II) LoadModule: "dri2"
[    24.393] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.395] (II) Module dri2: vendor="X.Org Foundation"
[    24.395]     compiled for 1.10.1, module version = 1.2.0
[    24.395]     ABI class: X.Org Server Extension, version 5.0
[    24.395] (II) Loading extension DRI2
[    24.395] (==) Matched vesa as autoconfigured driver 0
[    24.395] (==) Matched fbdev as autoconfigured driver 1
[    24.395] (==) Assigned the driver to the xf86ConfigLayout
[    24.395] (II) LoadModule: "vesa"
[    24.401] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.416] (II) Module vesa: vendor="X.Org Foundation"
[    24.416]     compiled for 1.10.0, module version = 2.3.0
[    24.416]     Module class: X.Org Video Driver
[    24.416]     ABI class: X.Org Video Driver, version 10.0
[    24.417] (II) LoadModule: "fbdev"
[    24.418] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.435] (II) Module fbdev: vendor="X.Org Foundation"
[    24.435]     compiled for 1.10.0, module version = 0.4.2
[    24.436]     ABI class: X.Org Video Driver, version 10.0
[    24.436] (II) VESA: driver for VESA chipsets: vesa
[    24.436] (II) FBDEV: driver for framebuffer: fbdev
[    24.436] (++) using VT number 7

[    24.437] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    24.437] (WW) Falling back to old probe method for vesa
[    24.437] (II) Loading sub module "fbdevhw"
[    24.437] (II) LoadModule: "fbdevhw"
[    24.438] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.451] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.452]     compiled for 1.10.1, module version = 0.0.2
[    24.452]     ABI class: X.Org Video Driver, version 10.0
[    24.452] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.452] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.452] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    24.452] (II) FBDEV(0): using default device
[    24.453] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.453] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    24.453] (==) FBDEV(0): RGB weight 888
[    24.453] (==) FBDEV(0): Default visual is TrueColor
[    24.453] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.453] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    24.453] (II) FBDEV(0): checking modes against framebuffer device...
[    24.453] (II) FBDEV(0): checking modes against monitor...
[    24.453] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    24.454] (**) FBDEV(0):  Built-in mode "current"
[    24.454] (==) FBDEV(0): DPI set to (96, 96)
[    24.454] (II) Loading sub module "fb"
[    24.454] (II) LoadModule: "fb"
[    24.454] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.479] (II) Module fb: vendor="X.Org Foundation"
[    24.479]     compiled for 1.10.1, module version = 1.0.0
[    24.479]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.479] (**) FBDEV(0): using shadow framebuffer
[    24.479] (II) Loading sub module "shadow"
[    24.479] (II) LoadModule: "shadow"
[    24.480] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    24.482] (II) Module shadow: vendor="X.Org Foundation"
[    24.482]     compiled for 1.10.1, module version = 1.1.0
[    24.482]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.482] (==) Depth 24 pixmap format is 32 bpp
[    24.560] (==) FBDEV(0): Backing store disabled
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.568] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.569] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.570] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.571] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.596] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.597] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.598] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.599] (==) FBDEV(0): DPMS enabled
[    24.599] (==) RandR enabled
[    24.604] (II) Initializing built-in extension Generic Event Extension
[    24.604] (II) Initializing built-in extension SHAPE
[    24.604] (II) Initializing built-in extension MIT-SHM
[    24.604] (II) Initializing built-in extension XInputExtension
[    24.604] (II) Initializing built-in extension XTEST
[    24.604] (II) Initializing built-in extension BIG-REQUESTS
[    24.604] (II) Initializing built-in extension SYNC
[    24.604] (II) Initializing built-in extension XKEYBOARD
[    24.604] (II) Initializing built-in extension XC-MISC
[    24.604] (II) Initializing built-in extension SECURITY
[    24.604] (II) Initializing built-in extension XINERAMA
[    24.604] (II) Initializing built-in extension XFIXES
[    24.604] (II) Initializing built-in extension RENDER
[    24.604] (II) Initializing built-in extension RANDR
[    24.604] (II) Initializing built-in extension COMPOSITE
[    24.604] (II) Initializing built-in extension DAMAGE
[    24.604] (II) Initializing built-in extension GESTURE
[    24.638] (II) AIGLX: Screen 0 is not DRI2 capable
[    24.638] (II) AIGLX: Screen 0 is not DRI capable
[    24.639] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    24.804] (II) AIGLX: Loaded and initialized swrast
[    24.804] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    25.025] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.128] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.128] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.132] (II) LoadModule: "evdev"
[    25.132] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.200] (II) Module evdev: vendor="X.Org Foundation"
[    25.200]     compiled for 1.10.0.902, module version = 2.6.0
[    25.200]     Module class: X.Org XInput Driver
[    25.201]     ABI class: X.Org XInput driver, version 12.3
[    25.201] (II) Using input driver 'evdev' for 'Video Bus'
[    25.201] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.201] (**) Video Bus: always reports core events
[    25.201] (**) Video Bus: Device: "/dev/input/event4"
[    25.201] (--) Video Bus: Found keys
[    25.201] (II) Video Bus: Configuring as keyboard
[    25.202] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    25.202] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.202] (**) Option "xkb_rules" "evdev"
[    25.202] (**) Option "xkb_model" "pc105"
[    25.202] (**) Option "xkb_layout" "us"
[    25.243] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.243] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.243] (II) Using input driver 'evdev' for 'Power Button'
[    25.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.243] (**) Power Button: always reports core events
[    25.243] (**) Power Button: Device: "/dev/input/event1"
[    25.252] (--) Power Button: Found keys
[    25.252] (II) Power Button: Configuring as keyboard
[    25.252] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.252] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.252] (**) Option "xkb_rules" "evdev"
[    25.252] (**) Option "xkb_model" "pc105"
[    25.252] (**) Option "xkb_layout" "us"
[    25.254] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.255] (II) No input driver/identifier specified (ignoring)
[    25.260] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.261] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.261] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.261] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.261] (**) Sleep Button: always reports core events
[    25.261] (**) Sleep Button: Device: "/dev/input/event2"
[    25.261] (--) Sleep Button: Found keys
[    25.261] (II) Sleep Button: Configuring as keyboard
[    25.261] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.261] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.261] (**) Option "xkb_rules" "evdev"
[    25.262] (**) Option "xkb_model" "pc105"
[    25.262] (**) Option "xkb_layout" "us"
[    25.337] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.337] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.337] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.337] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.338] (**) AT Translated Set 2 keyboard: always reports core events
[    25.338] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.338] (--) AT Translated Set 2 keyboard: Found keys
[    25.338] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.338] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.338] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.338] (**) Option "xkb_rules" "evdev"
[    25.338] (**) Option "xkb_model" "pc105"
[    25.338] (**) Option "xkb_layout" "us"
[    25.341] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.341] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.341] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.341] (II) LoadModule: "synaptics"
[    25.342] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.365] (II) Module synaptics: vendor="X.Org Foundation"
[    25.365]     compiled for 1.10.1, module version = 1.3.99
[    25.365]     Module class: X.Org XInput Driver
[    25.365]     ABI class: X.Org XInput driver, version 12.3
[    25.365] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.365] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.365] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.365] (**) Option "Device" "/dev/input/event5"
[    25.365] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.365] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.366] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.366] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.366] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.366] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.366] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.366] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    25.366] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.366] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.366] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.366] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    25.367] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.367] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.367] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.367] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.371] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    25.371] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.372] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.372] (II) No input driver/identifier specified (ignoring)
```




```
xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 

```

---

### Post by realzippy on 2011-09-26
Interesting.
Intel driver indeed does not get loaded,if we do not explicitly
load it with a xorg.conf,although KMS is working and we have
i915.modeset=1 as kernel boot option.
Now your are on the fbdev driver  :-) !

We now again use a xorg.conf with
intel and add Hsync/Vrefresh:

```
gksudo gedit /etc/X11/xorg.conf
```

paste into empty file:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 31-60
        VertRefresh 56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

close,save,reboot.
Know procedure meanwhile... ;-)
After reboot again xrandr and Xorg.0.log please...


Btw,
we have to hurry a bit,
we opened just a bottle of wine here.
Alcohol confuses me...  :)

---

### Post by JSchultheis on 2011-09-26
well the first boot was full screen, Xorg.0.log was:

```
[    24.074] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    24.074] X Protocol Version 11, Revision 0
[    24.074] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    24.074] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    24.074] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    24.075] Build Date: 11 August 2011  03:47:56PM
[    24.075] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    24.075] Current version of pixman: 0.20.2
[    24.075]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.075] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.075] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 14:07:32 2011
[    24.092] (==) Using config file: "/etc/X11/xorg.conf"
[    24.092] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.171] (==) No Layout section.  Using the first Screen section.
[    24.171] (**) |-->Screen "Default Screen" (0)
[    24.171] (**) |   |-->Monitor "Configured Monitor"
[    24.172] (**) |   |-->Device "Configured Video Device"
[    24.172] (==) Automatically adding devices
[    24.172] (==) Automatically enabling devices
[    24.186] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.186]     Entry deleted from font path.
[    24.186] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.187]     Entry deleted from font path.
[    24.187] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.187]     Entry deleted from font path.
[    24.198] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.198]     Entry deleted from font path.
[    24.199] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.199]     Entry deleted from font path.
[    24.213] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.213] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.213] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.213] (II) Loader magic: 0x81ffde0
[    24.213] (II) Module ABI versions:
[    24.213]     X.Org ANSI C Emulation: 0.4
[    24.213]     X.Org Video Driver: 10.0
[    24.213]     X.Org XInput driver : 12.3
[    24.213]     X.Org Server Extension : 5.0
[    24.220] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    24.220] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.220] (II) LoadModule: "extmod"
[    24.248] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.276] (II) Module extmod: vendor="X.Org Foundation"
[    24.276]     compiled for 1.10.1, module version = 1.0.0
[    24.276]     Module class: X.Org Server Extension
[    24.276]     ABI class: X.Org Server Extension, version 5.0
[    24.276] (II) Loading extension MIT-SCREEN-SAVER
[    24.277] (II) Loading extension XFree86-VidModeExtension
[    24.277] (II) Loading extension XFree86-DGA
[    24.277] (II) Loading extension DPMS
[    24.277] (II) Loading extension XVideo
[    24.277] (II) Loading extension XVideo-MotionCompensation
[    24.277] (II) Loading extension X-Resource
[    24.277] (II) LoadModule: "dbe"
[    24.278] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.287] (II) Module dbe: vendor="X.Org Foundation"
[    24.287]     compiled for 1.10.1, module version = 1.0.0
[    24.287]     Module class: X.Org Server Extension
[    24.287]     ABI class: X.Org Server Extension, version 5.0
[    24.287] (II) Loading extension DOUBLE-BUFFER
[    24.287] (II) LoadModule: "glx"
[    24.288] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.330] (II) Module glx: vendor="X.Org Foundation"
[    24.330]     compiled for 1.10.1, module version = 1.0.0
[    24.330]     ABI class: X.Org Server Extension, version 5.0
[    24.339] (==) AIGLX enabled
[    24.339] (II) Loading extension GLX
[    24.339] (II) LoadModule: "record"
[    24.340] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.356] (II) Module record: vendor="X.Org Foundation"
[    24.357]     compiled for 1.10.1, module version = 1.13.0
[    24.357]     Module class: X.Org Server Extension
[    24.357]     ABI class: X.Org Server Extension, version 5.0
[    24.357] (II) Loading extension RECORD
[    24.357] (II) LoadModule: "dri"
[    24.357] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.361] (II) Module dri: vendor="X.Org Foundation"
[    24.361]     compiled for 1.10.1, module version = 1.0.0
[    24.361]     ABI class: X.Org Server Extension, version 5.0
[    24.362] (II) Loading extension XFree86-DRI
[    24.362] (II) LoadModule: "dri2"
[    24.362] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.364] (II) Module dri2: vendor="X.Org Foundation"
[    24.364]     compiled for 1.10.1, module version = 1.2.0
[    24.364]     ABI class: X.Org Server Extension, version 5.0
[    24.364] (II) Loading extension DRI2
[    24.364] (II) LoadModule: "intel"
[    24.373] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.418] (II) Module intel: vendor="X.Org Foundation"
[    24.419]     compiled for 1.10.1, module version = 2.14.0
[    24.419]     Module class: X.Org Video Driver
[    24.419]     ABI class: X.Org Video Driver, version 10.0
[    24.419] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    24.421] (++) using VT number 7

[    24.437] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.438] drmOpenDevice: node name is /dev/dri/card0
[    24.438] drmOpenDevice: open result is 8, (OK)
[    24.439] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.439] drmOpenDevice: node name is /dev/dri/card0
[    24.439] drmOpenDevice: open result is 8, (OK)
[    24.439] drmOpenByBusid: drmOpenMinor returns 8
[    24.439] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.439] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    24.439] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.439] (==) intel(0): RGB weight 888
[    24.439] (==) intel(0): Default visual is TrueColor
[    24.439] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    24.448] (--) intel(0): Chipset: "845G"
[    24.448] (**) intel(0): Relaxed fencing disabled
[    24.448] (**) intel(0): Tiling enabled
[    24.448] (**) intel(0): SwapBuffers wait enabled
[    24.448] (==) intel(0): video overlay key set to 0x101fe
[    24.520] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    24.549] (II) intel(0): Output LVDS1 has no monitor section
[    24.625] (II) intel(0): EDID for output VGA1
[    24.625] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    24.625] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    24.625] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    24.625] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    24.625] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    24.625] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    24.626] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    24.626] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    24.626] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.626] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.627] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    24.627] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    24.627] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    24.627] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    24.627] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    24.627] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.627] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.632] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    24.632] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    24.633] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    24.633] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    24.633] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    24.633] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    24.633] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.633] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    24.634] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.634] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.634] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.634] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    24.634] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    24.634] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    24.634] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.634] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.635] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    24.635] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.635] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.635] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    24.644] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    24.644] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    24.644] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    24.644] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    24.644] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.644] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    24.645] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.645] (II) intel(0): Printing probed modes for output VGA1
[    24.645] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    24.645] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    24.645] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.645] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    24.645] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.645] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    24.645] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.645] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.646] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    24.646] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.646] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.646] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.646] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    24.646] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.646] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.685] (II) intel(0): EDID for output LVDS1
[    24.685] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.685] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.685] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.685] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.686] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.687] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.687] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.687] (II) intel(0): Printing probed modes for output LVDS1
[    24.687] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
[    24.687] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.687] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.687] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.687] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.687] (II) intel(0): Output VGA1 disconnected
[    24.687] (II) intel(0): Output LVDS1 connected
[    24.688] (II) intel(0): Using exact sizes for initial modes
[    24.688] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    24.688] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.688] (II) intel(0): Kernel page flipping support detected, enabling
[    24.688] (==) intel(0): DPI set to (96, 96)
[    24.688] (II) Loading sub module "fb"
[    24.688] (II) LoadModule: "fb"
[    24.689] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.705] (II) Module fb: vendor="X.Org Foundation"
[    24.705]     compiled for 1.10.1, module version = 1.0.0
[    24.705]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.705] (==) Depth 24 pixmap format is 32 bpp
[    24.705] (==) intel(0): VideoRam: 131072 KB
[    24.706] (II) intel(0): [DRI2] Setup complete
[    24.706] (II) intel(0): [DRI2]   DRI driver: i915
[    24.706] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    24.751] (II) UXA(0): Driver registered support for the following operations:
[    24.751] (II)         solid
[    24.751] (II)         copy
[    24.751] (II)         composite (RENDER acceleration)
[    24.751] (II)         put_image
[    24.751] (II)         get_image
[    24.751] (==) intel(0): Backing store disabled
[    24.751] (==) intel(0): Silken mouse enabled
[    24.757] (II) intel(0): Initializing HW Cursor
[    24.796] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.796] (==) intel(0): DPMS enabled
[    24.796] (==) intel(0): Intel XvMC decoder disabled
[    24.797] (II) intel(0): Set up overlay video
[    24.797] (II) intel(0): direct rendering: DRI2 Enabled
[    24.797] (==) intel(0): hotplug detection: "enabled"
[    24.797] (--) RandR disabled
[    24.798] (II) Initializing built-in extension Generic Event Extension
[    24.798] (II) Initializing built-in extension SHAPE
[    24.798] (II) Initializing built-in extension MIT-SHM
[    24.798] (II) Initializing built-in extension XInputExtension
[    24.798] (II) Initializing built-in extension XTEST
[    24.798] (II) Initializing built-in extension BIG-REQUESTS
[    24.798] (II) Initializing built-in extension SYNC
[    24.798] (II) Initializing built-in extension XKEYBOARD
[    24.798] (II) Initializing built-in extension XC-MISC
[    24.798] (II) Initializing built-in extension SECURITY
[    24.798] (II) Initializing built-in extension XINERAMA
[    24.798] (II) Initializing built-in extension XFIXES
[    24.798] (II) Initializing built-in extension RENDER
[    24.798] (II) Initializing built-in extension RANDR
[    24.798] (II) Initializing built-in extension COMPOSITE
[    24.798] (II) Initializing built-in extension DAMAGE
[    24.798] (II) Initializing built-in extension GESTURE
[    24.857] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    25.079] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.080] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.080] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.080] (II) AIGLX: enabled GLX_SGI_make_current_read
[    25.080] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.080] (II) AIGLX: Loaded and initialized i915
[    25.080] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.082] (II) intel(0): Setting screen physical size to 270 x 203
[    25.308] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.439] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.439] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.448] (II) LoadModule: "evdev"
[    25.448] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.512] (II) Module evdev: vendor="X.Org Foundation"
[    25.512]     compiled for 1.10.0.902, module version = 2.6.0
[    25.512]     Module class: X.Org XInput Driver
[    25.512]     ABI class: X.Org XInput driver, version 12.3
[    25.512] (II) Using input driver 'evdev' for 'Video Bus'
[    25.512] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.512] (**) Video Bus: always reports core events
[    25.512] (**) Video Bus: Device: "/dev/input/event4"
[    25.513] (--) Video Bus: Found keys
[    25.513] (II) Video Bus: Configuring as keyboard
[    25.513] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    25.513] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.513] (**) Option "xkb_rules" "evdev"
[    25.513] (**) Option "xkb_model" "pc105"
[    25.513] (**) Option "xkb_layout" "us"
[    25.583] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.583] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.591] (II) Using input driver 'evdev' for 'Power Button'
[    25.591] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.591] (**) Power Button: always reports core events
[    25.591] (**) Power Button: Device: "/dev/input/event1"
[    25.591] (--) Power Button: Found keys
[    25.591] (II) Power Button: Configuring as keyboard
[    25.591] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.591] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.592] (**) Option "xkb_rules" "evdev"
[    25.592] (**) Option "xkb_model" "pc105"
[    25.592] (**) Option "xkb_layout" "us"
[    25.594] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.594] (II) No input driver/identifier specified (ignoring)
[    25.604] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.604] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.605] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.605] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.605] (**) Sleep Button: always reports core events
[    25.605] (**) Sleep Button: Device: "/dev/input/event2"
[    25.605] (--) Sleep Button: Found keys
[    25.605] (II) Sleep Button: Configuring as keyboard
[    25.605] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.605] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.606] (**) Option "xkb_rules" "evdev"
[    25.606] (**) Option "xkb_model" "pc105"
[    25.606] (**) Option "xkb_layout" "us"
[    25.741] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.741] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.741] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.741] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.741] (**) AT Translated Set 2 keyboard: always reports core events
[    25.741] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.742] (--) AT Translated Set 2 keyboard: Found keys
[    25.742] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.742] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.742] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.742] (**) Option "xkb_rules" "evdev"
[    25.742] (**) Option "xkb_model" "pc105"
[    25.742] (**) Option "xkb_layout" "us"
[    25.756] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.757] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.757] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.757] (II) LoadModule: "synaptics"
[    25.759] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.919] (II) Module synaptics: vendor="X.Org Foundation"
[    25.919]     compiled for 1.10.1, module version = 1.3.99
[    25.919]     Module class: X.Org XInput Driver
[    25.919]     ABI class: X.Org XInput driver, version 12.3
[    25.919] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.919] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.919] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.919] (**) Option "Device" "/dev/input/event5"
[    25.920] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.920] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.920] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.920] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.920] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.920] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.920] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.920] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    25.921] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.921] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.921] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.921] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    25.921] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.922] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.922] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.922] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.922] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    25.922] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.928] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.928] (II) No input driver/identifier specified (ignoring)
```


so I rebooted, just to see if it would stick (was this a mistake?)
and the display is small again.


log now upon reboot with small display:
```
[    24.717] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    24.717] X Protocol Version 11, Revision 0
[    24.717] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    24.717] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    24.717] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    24.717] Build Date: 11 August 2011  03:47:56PM
[    24.717] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    24.717] Current version of pixman: 0.20.2
[    24.717]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.717] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.718] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 14:10:12 2011
[    24.748] (==) Using config file: "/etc/X11/xorg.conf"
[    24.749] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.899] (==) No Layout section.  Using the first Screen section.
[    24.899] (**) |-->Screen "Default Screen" (0)
[    24.899] (**) |   |-->Monitor "Configured Monitor"
[    24.900] (**) |   |-->Device "Configured Video Device"
[    24.900] (==) Automatically adding devices
[    24.900] (==) Automatically enabling devices
[    24.933] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.933]     Entry deleted from font path.
[    24.933] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.933]     Entry deleted from font path.
[    24.934] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.934]     Entry deleted from font path.
[    24.941] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.941]     Entry deleted from font path.
[    24.941] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.941]     Entry deleted from font path.
[    24.969] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.969] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.969] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.969] (II) Loader magic: 0x81ffde0
[    24.969] (II) Module ABI versions:
[    24.969]     X.Org ANSI C Emulation: 0.4
[    24.969]     X.Org Video Driver: 10.0
[    24.969]     X.Org XInput driver : 12.3
[    24.969]     X.Org Server Extension : 5.0
[    24.972] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    24.972] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.973] (II) LoadModule: "extmod"
[    25.006] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.033] (II) Module extmod: vendor="X.Org Foundation"
[    25.033]     compiled for 1.10.1, module version = 1.0.0
[    25.033]     Module class: X.Org Server Extension
[    25.033]     ABI class: X.Org Server Extension, version 5.0
[    25.033] (II) Loading extension MIT-SCREEN-SAVER
[    25.033] (II) Loading extension XFree86-VidModeExtension
[    25.033] (II) Loading extension XFree86-DGA
[    25.033] (II) Loading extension DPMS
[    25.033] (II) Loading extension XVideo
[    25.033] (II) Loading extension XVideo-MotionCompensation
[    25.033] (II) Loading extension X-Resource
[    25.033] (II) LoadModule: "dbe"
[    25.034] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.045] (II) Module dbe: vendor="X.Org Foundation"
[    25.046]     compiled for 1.10.1, module version = 1.0.0
[    25.047]     Module class: X.Org Server Extension
[    25.047]     ABI class: X.Org Server Extension, version 5.0
[    25.047] (II) Loading extension DOUBLE-BUFFER
[    25.047] (II) LoadModule: "glx"
[    25.048] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.144] (II) Module glx: vendor="X.Org Foundation"
[    25.144]     compiled for 1.10.1, module version = 1.0.0
[    25.144]     ABI class: X.Org Server Extension, version 5.0
[    25.152] (==) AIGLX enabled
[    25.153] (II) Loading extension GLX
[    25.154] (II) LoadModule: "record"
[    25.156] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.199] (II) Module record: vendor="X.Org Foundation"
[    25.199]     compiled for 1.10.1, module version = 1.13.0
[    25.199]     Module class: X.Org Server Extension
[    25.199]     ABI class: X.Org Server Extension, version 5.0
[    25.199] (II) Loading extension RECORD
[    25.199] (II) LoadModule: "dri"
[    25.200] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.317] (II) Module dri: vendor="X.Org Foundation"
[    25.318]     compiled for 1.10.1, module version = 1.0.0
[    25.318]     ABI class: X.Org Server Extension, version 5.0
[    25.318] (II) Loading extension XFree86-DRI
[    25.318] (II) LoadModule: "dri2"
[    25.318] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.320] (II) Module dri2: vendor="X.Org Foundation"
[    25.320]     compiled for 1.10.1, module version = 1.2.0
[    25.320]     ABI class: X.Org Server Extension, version 5.0
[    25.320] (II) Loading extension DRI2
[    25.320] (II) LoadModule: "intel"
[    25.346] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.403] (II) Module intel: vendor="X.Org Foundation"
[    25.403]     compiled for 1.10.1, module version = 2.14.0
[    25.403]     Module class: X.Org Video Driver
[    25.403]     ABI class: X.Org Video Driver, version 10.0
[    25.404] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    25.406] (++) using VT number 7

[    25.420] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.420] drmOpenDevice: node name is /dev/dri/card0
[    25.420] drmOpenDevice: open result is 8, (OK)
[    25.421] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.421] drmOpenDevice: node name is /dev/dri/card0
[    25.421] drmOpenDevice: open result is 8, (OK)
[    25.421] drmOpenByBusid: drmOpenMinor returns 8
[    25.421] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.421] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    25.421] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.421] (==) intel(0): RGB weight 888
[    25.421] (==) intel(0): Default visual is TrueColor
[    25.421] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    25.422] (--) intel(0): Chipset: "845G"
[    25.422] (**) intel(0): Relaxed fencing disabled
[    25.422] (**) intel(0): Tiling enabled
[    25.422] (**) intel(0): SwapBuffers wait enabled
[    25.422] (==) intel(0): video overlay key set to 0x101fe
[    25.489] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    25.509] (II) intel(0): Output LVDS1 has no monitor section
[    25.557] (II) intel(0): EDID for output VGA1
[    25.558] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    25.558] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    25.558] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    25.558] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.558] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    25.558] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.559] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    25.559] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    25.559] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.559] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.560] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.560] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.560] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    25.560] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.560] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    25.564] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    25.564] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    25.564] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.564] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.564] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.564] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.564] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.565] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.565] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    25.565] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    25.566] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.566] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.566] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    25.567] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.567] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.567] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.567] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    25.567] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    25.567] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.567] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    25.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.572] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    25.572] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.573] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    25.573] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.573] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    25.573] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.573] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    25.573] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.573] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    25.573] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.573] (II) intel(0): Printing probed modes for output VGA1
[    25.573] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.573] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.573] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.574] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    25.574] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.574] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.574] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.574] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.574] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.574] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.574] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.574] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.574] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.575] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.575] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.600] (II) intel(0): EDID for output LVDS1
[    25.601] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.601] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.601] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.601] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.601] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.601] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.601] (II) intel(0): Printing probed modes for output LVDS1
[    25.601] (II) intel(0): Modeline "640x480"x60.0   65.00  640 856 992 1344  480 627 633 806 (48.4 kHz)
[    25.601] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.601] (II) intel(0): Output VGA1 disconnected
[    25.601] (II) intel(0): Output LVDS1 connected
[    25.602] (II) intel(0): Using exact sizes for initial modes
[    25.602] (II) intel(0): Output LVDS1 using initial mode 640x480
[    25.602] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.602] (II) intel(0): Kernel page flipping support detected, enabling
[    25.602] (==) intel(0): DPI set to (96, 96)
[    25.602] (II) Loading sub module "fb"
[    25.602] (II) LoadModule: "fb"
[    25.603] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.633] (II) Module fb: vendor="X.Org Foundation"
[    25.633]     compiled for 1.10.1, module version = 1.0.0
[    25.633]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.633] (==) Depth 24 pixmap format is 32 bpp
[    25.633] (==) intel(0): VideoRam: 131072 KB
[    25.633] (II) intel(0): [DRI2] Setup complete
[    25.634] (II) intel(0): [DRI2]   DRI driver: i915
[    25.634] (II) intel(0): Allocated new frame buffer 640x480 stride 4096, tiled
[    25.678] (II) UXA(0): Driver registered support for the following operations:
[    25.678] (II)         solid
[    25.679] (II)         copy
[    25.679] (II)         composite (RENDER acceleration)
[    25.679] (II)         put_image
[    25.679] (II)         get_image
[    25.679] (==) intel(0): Backing store disabled
[    25.679] (==) intel(0): Silken mouse enabled
[    25.685] (II) intel(0): Initializing HW Cursor
[    25.720] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.720] (==) intel(0): DPMS enabled
[    25.720] (==) intel(0): Intel XvMC decoder disabled
[    25.721] (II) intel(0): Set up overlay video
[    25.721] (II) intel(0): direct rendering: DRI2 Enabled
[    25.721] (==) intel(0): hotplug detection: "enabled"
[    25.721] (--) RandR disabled
[    25.721] (II) Initializing built-in extension Generic Event Extension
[    25.721] (II) Initializing built-in extension SHAPE
[    25.721] (II) Initializing built-in extension MIT-SHM
[    25.721] (II) Initializing built-in extension XInputExtension
[    25.722] (II) Initializing built-in extension XTEST
[    25.722] (II) Initializing built-in extension BIG-REQUESTS
[    25.722] (II) Initializing built-in extension SYNC
[    25.722] (II) Initializing built-in extension XKEYBOARD
[    25.722] (II) Initializing built-in extension XC-MISC
[    25.722] (II) Initializing built-in extension SECURITY
[    25.722] (II) Initializing built-in extension XINERAMA
[    25.722] (II) Initializing built-in extension XFIXES
[    25.722] (II) Initializing built-in extension RENDER
[    25.722] (II) Initializing built-in extension RANDR
[    25.722] (II) Initializing built-in extension COMPOSITE
[    25.722] (II) Initializing built-in extension DAMAGE
[    25.722] (II) Initializing built-in extension GESTURE
[    25.768] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    26.136] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.136] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.136] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.136] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.136] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.136] (II) AIGLX: Loaded and initialized i915
[    26.136] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.138] (II) intel(0): Setting screen physical size to 169 x 126
[    26.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.466] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.466] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.466] (II) LoadModule: "evdev"
[    26.466] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.539] (II) Module evdev: vendor="X.Org Foundation"
[    26.539]     compiled for 1.10.0.902, module version = 2.6.0
[    26.539]     Module class: X.Org XInput Driver
[    26.539]     ABI class: X.Org XInput driver, version 12.3
[    26.539] (II) Using input driver 'evdev' for 'Video Bus'
[    26.540] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.540] (**) Video Bus: always reports core events
[    26.540] (**) Video Bus: Device: "/dev/input/event4"
[    26.540] (--) Video Bus: Found keys
[    26.540] (II) Video Bus: Configuring as keyboard
[    26.541] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    26.541] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.541] (**) Option "xkb_rules" "evdev"
[    26.541] (**) Option "xkb_model" "pc105"
[    26.541] (**) Option "xkb_layout" "us"
[    26.591] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.591] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.591] (II) Using input driver 'evdev' for 'Power Button'
[    26.591] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.591] (**) Power Button: always reports core events
[    26.591] (**) Power Button: Device: "/dev/input/event1"
[    26.592] (--) Power Button: Found keys
[    26.592] (II) Power Button: Configuring as keyboard
[    26.592] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.592] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.592] (**) Option "xkb_rules" "evdev"
[    26.592] (**) Option "xkb_model" "pc105"
[    26.592] (**) Option "xkb_layout" "us"
[    26.600] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.600] (II) No input driver/identifier specified (ignoring)
[    26.601] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.602] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.602] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.602] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.602] (**) Sleep Button: always reports core events
[    26.602] (**) Sleep Button: Device: "/dev/input/event2"
[    26.602] (--) Sleep Button: Found keys
[    26.602] (II) Sleep Button: Configuring as keyboard
[    26.602] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    26.602] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    26.603] (**) Option "xkb_rules" "evdev"
[    26.603] (**) Option "xkb_model" "pc105"
[    26.603] (**) Option "xkb_layout" "us"
[    26.678] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.678] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.678] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.678] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.678] (**) AT Translated Set 2 keyboard: always reports core events
[    26.678] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.678] (--) AT Translated Set 2 keyboard: Found keys
[    26.679] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.679] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    26.679] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.679] (**) Option "xkb_rules" "evdev"
[    26.679] (**) Option "xkb_model" "pc105"
[    26.679] (**) Option "xkb_layout" "us"
[    26.685] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    26.685] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.685] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.685] (II) LoadModule: "synaptics"
[    26.686] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.704] (II) Module synaptics: vendor="X.Org Foundation"
[    26.704]     compiled for 1.10.1, module version = 1.3.99
[    26.704]     Module class: X.Org XInput Driver
[    26.704]     ABI class: X.Org XInput driver, version 12.3
[    26.704] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    26.704] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.704] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.704] (**) Option "Device" "/dev/input/event5"
[    26.705] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    26.705] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    26.705] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    26.705] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    26.705] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    26.705] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.705] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.705] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    26.705] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    26.706] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    26.706] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    26.706] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    26.706] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    26.706] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    26.706] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    26.707] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    26.707] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    26.707] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.712] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    26.713] (II) No input driver/identifier specified (ignoring)
```


```
xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     59.9  
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9 
```


wine sounds especially good after all this!! :p

---

### Post by JSchultheis on 2011-09-26
getting: ```
 ureadahead main process (202) terminated with status 5
``` during startup

---

### Post by realzippy on 2011-09-26
You mean after 1rst reboot resolution was perfect,
which didn't persist 2nd reboot?
.................................................
run:

```
xrandr --newmode “1024x768&#8243; 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
```
xrandr --addmode LVDS1 1024x768
```
```
xrandr --output LVDS1 --mode 1024x768
```

what happens?

---

### Post by JSchultheis on 2011-09-26
First code
```
xrandr --newmode “1024x768&#8243; 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

``` went right in.

Next:
```
xrandr --addmode LVDS1 1024x768
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  22
  Current serial number in output stream:  23

```


Final:
```
xrandr --output LVDS1 --mode 1024x768
xrandr: cannot find mode 1024x768

```


Now I will reboot and post stuff!

---

### Post by JSchultheis on 2011-09-26
seems to keep hanging... 

I am posting between two computers

---

### Post by realzippy on 2011-09-26
> **JSchultheis said:**
> 
Now I will reboot and post stuff!

..reboot won't change anything...xrandr commands are per session only.

Edit xorg.conf,change
```
Identifier	"Default Screen"
```
to
```
Identifier	"LVDS-1"
```

Reboot.
If you can't see the screen after reboot,boot in 
recovery mode,drop to shell,run:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by realzippy on 2011-09-26
..we crossposted again..
so what is status now?
Can't boot?

---

### Post by JSchultheis on 2011-09-26
finally booted. 

I'm working post #32.

---

### Post by JSchultheis on 2011-09-26
Well it seems to freeze three times, on the fourth it boots with small screen.

```
xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     59.9  
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  

```

```
[    25.267] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    25.268] X Protocol Version 11, Revision 0
[    25.268] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    25.268] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    25.268] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    25.268] Build Date: 11 August 2011  03:47:56PM
[    25.268] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    25.268] Current version of pixman: 0.20.2
[    25.269]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    25.269] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.269] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 14:59:43 2011
[    25.298] (==) Using config file: "/etc/X11/xorg.conf"
[    25.298] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.416] (==) No Layout section.  Using the first Screen section.
[    25.416] (**) |-->Screen "LVDS-1" (0)
[    25.416] (**) |   |-->Monitor "Configured Monitor"
[    25.417] (**) |   |-->Device "Configured Video Device"
[    25.417] (==) Automatically adding devices
[    25.417] (==) Automatically enabling devices
[    25.450] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.450]     Entry deleted from font path.
[    25.450] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.450]     Entry deleted from font path.
[    25.450] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.451]     Entry deleted from font path.
[    25.476] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.476]     Entry deleted from font path.
[    25.476] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.476]     Entry deleted from font path.
[    25.496] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    25.496] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.496] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.496] (II) Loader magic: 0x81ffde0
[    25.497] (II) Module ABI versions:
[    25.497]     X.Org ANSI C Emulation: 0.4
[    25.497]     X.Org Video Driver: 10.0
[    25.497]     X.Org XInput driver : 12.3
[    25.497]     X.Org Server Extension : 5.0
[    25.499] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    25.504] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    25.504] (II) LoadModule: "extmod"
[    25.526] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.553] (II) Module extmod: vendor="X.Org Foundation"
[    25.553]     compiled for 1.10.1, module version = 1.0.0
[    25.553]     Module class: X.Org Server Extension
[    25.553]     ABI class: X.Org Server Extension, version 5.0
[    25.553] (II) Loading extension MIT-SCREEN-SAVER
[    25.554] (II) Loading extension XFree86-VidModeExtension
[    25.554] (II) Loading extension XFree86-DGA
[    25.554] (II) Loading extension DPMS
[    25.554] (II) Loading extension XVideo
[    25.554] (II) Loading extension XVideo-MotionCompensation
[    25.554] (II) Loading extension X-Resource
[    25.554] (II) LoadModule: "dbe"
[    25.554] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.564] (II) Module dbe: vendor="X.Org Foundation"
[    25.564]     compiled for 1.10.1, module version = 1.0.0
[    25.564]     Module class: X.Org Server Extension
[    25.564]     ABI class: X.Org Server Extension, version 5.0
[    25.564] (II) Loading extension DOUBLE-BUFFER
[    25.564] (II) LoadModule: "glx"
[    25.565] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.607] (II) Module glx: vendor="X.Org Foundation"
[    25.607]     compiled for 1.10.1, module version = 1.0.0
[    25.607]     ABI class: X.Org Server Extension, version 5.0
[    25.616] (==) AIGLX enabled
[    25.616] (II) Loading extension GLX
[    25.616] (II) LoadModule: "record"
[    25.617] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.712] (II) Module record: vendor="X.Org Foundation"
[    25.712]     compiled for 1.10.1, module version = 1.13.0
[    25.712]     Module class: X.Org Server Extension
[    25.713]     ABI class: X.Org Server Extension, version 5.0
[    25.713] (II) Loading extension RECORD
[    25.713] (II) LoadModule: "dri"
[    25.713] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.715] (II) Module dri: vendor="X.Org Foundation"
[    25.716]     compiled for 1.10.1, module version = 1.0.0
[    25.716]     ABI class: X.Org Server Extension, version 5.0
[    25.716] (II) Loading extension XFree86-DRI
[    25.716] (II) LoadModule: "dri2"
[    25.716] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.718] (II) Module dri2: vendor="X.Org Foundation"
[    25.718]     compiled for 1.10.1, module version = 1.2.0
[    25.718]     ABI class: X.Org Server Extension, version 5.0
[    25.718] (II) Loading extension DRI2
[    25.718] (II) LoadModule: "intel"
[    25.739] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.795] (II) Module intel: vendor="X.Org Foundation"
[    25.796]     compiled for 1.10.1, module version = 2.14.0
[    25.796]     Module class: X.Org Video Driver
[    25.796]     ABI class: X.Org Video Driver, version 10.0
[    25.796] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    25.798] (++) using VT number 7

[    25.809] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.809] drmOpenDevice: node name is /dev/dri/card0
[    25.810] drmOpenDevice: open result is 8, (OK)
[    25.810] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.810] drmOpenDevice: node name is /dev/dri/card0
[    25.810] drmOpenDevice: open result is 8, (OK)
[    25.810] drmOpenByBusid: drmOpenMinor returns 8
[    25.810] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.810] (II) intel(0): Creating default Display subsection in Screen section
    "LVDS-1" for depth/fbbpp 24/32
[    25.810] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.811] (==) intel(0): RGB weight 888
[    25.811] (==) intel(0): Default visual is TrueColor
[    25.811] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    25.811] (--) intel(0): Chipset: "845G"
[    25.811] (**) intel(0): Relaxed fencing disabled
[    25.811] (**) intel(0): Tiling enabled
[    25.811] (**) intel(0): SwapBuffers wait enabled
[    25.811] (==) intel(0): video overlay key set to 0x101fe
[    25.868] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    25.884] (II) intel(0): Output LVDS1 has no monitor section
[    25.934] (II) intel(0): EDID for output VGA1
[    25.935] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    25.935] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    25.935] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    25.935] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    25.935] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.935] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    25.936] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    25.936] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    25.936] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.936] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.936] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    25.937] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    25.937] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.937] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    25.937] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    25.938] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    25.938] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.938] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    25.939] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    25.939] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.939] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.939] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.944] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    25.944] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    25.944] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    25.944] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.944] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.944] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.944] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.945] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    25.945] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    25.945] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    25.945] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    25.945] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    25.945] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.945] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    25.945] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.946] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    25.946] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.946] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    25.946] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.946] (II) intel(0): Printing probed modes for output VGA1
[    25.946] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.946] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.946] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.946] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    25.946] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.946] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.947] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.947] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.947] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.947] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.947] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.947] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.947] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.947] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.947] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.971] (II) intel(0): EDID for output LVDS1
[    25.972] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.972] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.972] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.972] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.972] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.972] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.972] (II) intel(0): Printing probed modes for output LVDS1
[    25.972] (II) intel(0): Modeline "640x480"x60.0   65.00  640 856 992 1344  480 627 633 806 (48.4 kHz)
[    25.972] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.972] (II) intel(0): Output VGA1 disconnected
[    25.972] (II) intel(0): Output LVDS1 connected
[    25.972] (II) intel(0): Using exact sizes for initial modes
[    25.973] (II) intel(0): Output LVDS1 using initial mode 640x480
[    25.973] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.973] (II) intel(0): Kernel page flipping support detected, enabling
[    25.973] (==) intel(0): DPI set to (96, 96)
[    25.973] (II) Loading sub module "fb"
[    25.973] (II) LoadModule: "fb"
[    25.973] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.996] (II) Module fb: vendor="X.Org Foundation"
[    25.996]     compiled for 1.10.1, module version = 1.0.0
[    25.996]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.997] (==) Depth 24 pixmap format is 32 bpp
[    25.997] (==) intel(0): VideoRam: 131072 KB
[    25.997] (II) intel(0): [DRI2] Setup complete
[    25.997] (II) intel(0): [DRI2]   DRI driver: i915
[    25.997] (II) intel(0): Allocated new frame buffer 640x480 stride 4096, tiled
[    26.042] (II) UXA(0): Driver registered support for the following operations:
[    26.042] (II)         solid
[    26.042] (II)         copy
[    26.042] (II)         composite (RENDER acceleration)
[    26.042] (II)         put_image
[    26.042] (II)         get_image
[    26.042] (==) intel(0): Backing store disabled
[    26.042] (==) intel(0): Silken mouse enabled
[    26.048] (II) intel(0): Initializing HW Cursor
[    26.068] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.068] (==) intel(0): DPMS enabled
[    26.068] (==) intel(0): Intel XvMC decoder disabled
[    26.069] (II) intel(0): Set up overlay video
[    26.069] (II) intel(0): direct rendering: DRI2 Enabled
[    26.069] (==) intel(0): hotplug detection: "enabled"
[    26.069] (--) RandR disabled
[    26.069] (II) Initializing built-in extension Generic Event Extension
[    26.069] (II) Initializing built-in extension SHAPE
[    26.069] (II) Initializing built-in extension MIT-SHM
[    26.069] (II) Initializing built-in extension XInputExtension
[    26.070] (II) Initializing built-in extension XTEST
[    26.070] (II) Initializing built-in extension BIG-REQUESTS
[    26.070] (II) Initializing built-in extension SYNC
[    26.070] (II) Initializing built-in extension XKEYBOARD
[    26.070] (II) Initializing built-in extension XC-MISC
[    26.070] (II) Initializing built-in extension SECURITY
[    26.070] (II) Initializing built-in extension XINERAMA
[    26.070] (II) Initializing built-in extension XFIXES
[    26.070] (II) Initializing built-in extension RENDER
[    26.070] (II) Initializing built-in extension RANDR
[    26.070] (II) Initializing built-in extension COMPOSITE
[    26.070] (II) Initializing built-in extension DAMAGE
[    26.070] (II) Initializing built-in extension GESTURE
[    26.112] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    26.342] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.342] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.342] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.343] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.343] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.343] (II) AIGLX: Loaded and initialized i915
[    26.343] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.346] (II) intel(0): Setting screen physical size to 169 x 126
[    26.599] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.692] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.692] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.693] (II) LoadModule: "evdev"
[    26.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.760] (II) Module evdev: vendor="X.Org Foundation"
[    26.760]     compiled for 1.10.0.902, module version = 2.6.0
[    26.760]     Module class: X.Org XInput Driver
[    26.761]     ABI class: X.Org XInput driver, version 12.3
[    26.761] (II) Using input driver 'evdev' for 'Video Bus'
[    26.761] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.761] (**) Video Bus: always reports core events
[    26.761] (**) Video Bus: Device: "/dev/input/event4"
[    26.762] (--) Video Bus: Found keys
[    26.762] (II) Video Bus: Configuring as keyboard
[    26.762] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    26.762] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.762] (**) Option "xkb_rules" "evdev"
[    26.762] (**) Option "xkb_model" "pc105"
[    26.762] (**) Option "xkb_layout" "us"
[    26.810] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.810] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.811] (II) Using input driver 'evdev' for 'Power Button'
[    26.811] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.811] (**) Power Button: always reports core events
[    26.811] (**) Power Button: Device: "/dev/input/event1"
[    26.811] (--) Power Button: Found keys
[    26.811] (II) Power Button: Configuring as keyboard
[    26.811] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.811] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.812] (**) Option "xkb_rules" "evdev"
[    26.822] (**) Option "xkb_model" "pc105"
[    26.822] (**) Option "xkb_layout" "us"
[    26.825] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.825] (II) No input driver/identifier specified (ignoring)
[    26.826] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.827] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.827] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.827] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.827] (**) Sleep Button: always reports core events
[    26.827] (**) Sleep Button: Device: "/dev/input/event2"
[    26.843] (--) Sleep Button: Found keys
[    26.843] (II) Sleep Button: Configuring as keyboard
[    26.843] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    26.843] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    26.843] (**) Option "xkb_rules" "evdev"
[    26.843] (**) Option "xkb_model" "pc105"
[    26.843] (**) Option "xkb_layout" "us"
[    26.933] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.934] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.934] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.934] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.934] (**) AT Translated Set 2 keyboard: always reports core events
[    26.934] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.934] (--) AT Translated Set 2 keyboard: Found keys
[    26.934] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.934] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    26.934] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.934] (**) Option "xkb_rules" "evdev"
[    26.935] (**) Option "xkb_model" "pc105"
[    26.935] (**) Option "xkb_layout" "us"
[    26.945] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    26.945] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.945] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.945] (II) LoadModule: "synaptics"
[    26.945] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.982] (II) Module synaptics: vendor="X.Org Foundation"
[    26.982]     compiled for 1.10.1, module version = 1.3.99
[    26.982]     Module class: X.Org XInput Driver
[    26.982]     ABI class: X.Org XInput driver, version 12.3
[    26.982] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    26.982] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.982] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.982] (**) Option "Device" "/dev/input/event5"
[    26.982] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    26.983] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    26.983] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    26.983] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    26.983] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    26.983] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.983] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.983] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    26.983] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    26.983] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    26.984] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    26.984] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    26.984] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    26.984] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    26.985] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    26.985] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    26.985] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    26.985] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.986] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    26.986] (II) No input driver/identifier specified (ignoring)
```

---

### Post by JSchultheis on 2011-09-26
I did not have to boot in recovery mode

---

### Post by realzippy on 2011-09-26
Ok,see some dust settling..

We need to tell the intel driver explicitly to use the monitor section
for LVDS1 :
```
 [    25.489] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    25.509] (II) intel(0): Output LVDS1 has no monitor section
```

I am not sure how to do this at the moment,intel manpages offer an option
in the device section;
we can try:
edit xorg.conf again,delete all,paste in:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
        Option          "LVDS1"
EndSection

Section "Monitor"
	Identifier	"LVDS1"
        HorizSync   31-60
        VertRefresh 56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"LVDS1""
	Device		"Configured Video Device"
EndSection
```

Sorry,I had to investigate further,if this not works.
We had to go on tomorrow.it is late here meanwhile.
Until then we can "reset" your system if it is unusable now.

---

### Post by JSchultheis on 2011-09-26
Very good and thank you! I will plug that in and post the results. But then tomorrow sometime we can pick back up if need be!! :D

---

### Post by JSchultheis on 2011-09-26
Just to touch base, I don't think I can boot up. A few more tries and I am going to boot to recovery mode.

---

### Post by realzippy on 2011-09-26
```
sudo mv /etc/X11/xorg.conf.strange /etc/X11/xorg.conf
```
resets system to post #1 status. (hopefully)..
Send me a pm when you have time tomorrow to go on.
We have to use vesa/fbdev if we cannot run intel stable,means without reboot trouble.Although the problem (LVDS1 vs VGA1) may remain...
have fun,zippy

---

### Post by JSchultheis on 2011-09-26
well, 
the screen never came up, so

I logged into shell 
```
rm /etc/X11/xorg.conf
```after rebooting it actually is full screen.

```
gedit /var/log/Xorg.0.log
```gives me
```
[    23.967] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    23.968] X Protocol Version 11, Revision 0
[    23.968] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    23.968] Current Operating System: Linux poslaptop 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686
[    23.968] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.1-030001-generic root=UUID=d096bdec-c52f-491e-a23a-710a60f1c6b1 ro quiet splash i915.modeset=1 vt.handoff=7
[    23.968] Build Date: 11 August 2011  03:47:56PM
[    23.968] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    23.968] Current version of pixman: 0.20.2
[    23.968]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.969] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.969] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 26 16:14:19 2011
[    24.033] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.199] (==) No Layout section.  Using the first Screen section.
[    24.199] (==) No screen section available. Using defaults.
[    24.199] (**) |-->Screen "Default Screen Section" (0)
[    24.199] (**) |   |-->Monitor "<default monitor>"
[    24.199] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.200] (==) Automatically adding devices
[    24.200] (==) Automatically enabling devices
[    24.224] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.224]     Entry deleted from font path.
[    24.224] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.224]     Entry deleted from font path.
[    24.225] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.225]     Entry deleted from font path.
[    24.250] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.251]     Entry deleted from font path.
[    24.251] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.251]     Entry deleted from font path.
[    24.293] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.293] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.293] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.293] (II) Loader magic: 0x81ffde0
[    24.293] (II) Module ABI versions:
[    24.293]     X.Org ANSI C Emulation: 0.4
[    24.293]     X.Org Video Driver: 10.0
[    24.294]     X.Org XInput driver : 12.3
[    24.294]     X.Org Server Extension : 5.0
[    24.296] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    24.297] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.297] (II) LoadModule: "extmod"
[    24.330] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.369] (II) Module extmod: vendor="X.Org Foundation"
[    24.369]     compiled for 1.10.1, module version = 1.0.0
[    24.370]     Module class: X.Org Server Extension
[    24.370]     ABI class: X.Org Server Extension, version 5.0
[    24.370] (II) Loading extension MIT-SCREEN-SAVER
[    24.370] (II) Loading extension XFree86-VidModeExtension
[    24.370] (II) Loading extension XFree86-DGA
[    24.370] (II) Loading extension DPMS
[    24.370] (II) Loading extension XVideo
[    24.370] (II) Loading extension XVideo-MotionCompensation
[    24.370] (II) Loading extension X-Resource
[    24.370] (II) LoadModule: "dbe"
[    24.371] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.384] (II) Module dbe: vendor="X.Org Foundation"
[    24.385]     compiled for 1.10.1, module version = 1.0.0
[    24.385]     Module class: X.Org Server Extension
[    24.385]     ABI class: X.Org Server Extension, version 5.0
[    24.385] (II) Loading extension DOUBLE-BUFFER
[    24.385] (II) LoadModule: "glx"
[    24.386] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.496] (II) Module glx: vendor="X.Org Foundation"
[    24.496]     compiled for 1.10.1, module version = 1.0.0
[    24.496]     ABI class: X.Org Server Extension, version 5.0
[    24.505] (==) AIGLX enabled
[    24.505] (II) Loading extension GLX
[    24.505] (II) LoadModule: "record"
[    24.505] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.522] (II) Module record: vendor="X.Org Foundation"
[    24.522]     compiled for 1.10.1, module version = 1.13.0
[    24.522]     Module class: X.Org Server Extension
[    24.522]     ABI class: X.Org Server Extension, version 5.0
[    24.522] (II) Loading extension RECORD
[    24.523] (II) LoadModule: "dri"
[    24.523] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.527] (II) Module dri: vendor="X.Org Foundation"
[    24.527]     compiled for 1.10.1, module version = 1.0.0
[    24.527]     ABI class: X.Org Server Extension, version 5.0
[    24.527] (II) Loading extension XFree86-DRI
[    24.527] (II) LoadModule: "dri2"
[    24.528] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.529] (II) Module dri2: vendor="X.Org Foundation"
[    24.529]     compiled for 1.10.1, module version = 1.2.0
[    24.529]     ABI class: X.Org Server Extension, version 5.0
[    24.530] (II) Loading extension DRI2
[    24.530] (==) Matched vesa as autoconfigured driver 0
[    24.530] (==) Matched fbdev as autoconfigured driver 1
[    24.530] (==) Assigned the driver to the xf86ConfigLayout
[    24.530] (II) LoadModule: "vesa"
[    24.555] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.579] (II) Module vesa: vendor="X.Org Foundation"
[    24.580]     compiled for 1.10.0, module version = 2.3.0
[    24.580]     Module class: X.Org Video Driver
[    24.580]     ABI class: X.Org Video Driver, version 10.0
[    24.580] (II) LoadModule: "fbdev"
[    24.581] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.672] (II) Module fbdev: vendor="X.Org Foundation"
[    24.672]     compiled for 1.10.0, module version = 0.4.2
[    24.672]     ABI class: X.Org Video Driver, version 10.0
[    24.673] (II) VESA: driver for VESA chipsets: vesa
[    24.673] (II) FBDEV: driver for framebuffer: fbdev
[    24.673] (++) using VT number 7

[    24.674] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    24.674] (WW) Falling back to old probe method for vesa
[    24.674] (II) Loading sub module "fbdevhw"
[    24.674] (II) LoadModule: "fbdevhw"
[    24.674] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.686] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.686]     compiled for 1.10.1, module version = 0.0.2
[    24.686]     ABI class: X.Org Video Driver, version 10.0
[    24.686] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.686] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.687] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    24.687] (II) FBDEV(0): using default device
[    24.687] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.687] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    24.687] (==) FBDEV(0): RGB weight 888
[    24.687] (==) FBDEV(0): Default visual is TrueColor
[    24.687] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.688] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    24.688] (II) FBDEV(0): checking modes against framebuffer device...
[    24.688] (II) FBDEV(0): checking modes against monitor...
[    24.688] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    24.688] (**) FBDEV(0):  Built-in mode "current"
[    24.688] (==) FBDEV(0): DPI set to (96, 96)
[    24.688] (II) Loading sub module "fb"
[    24.688] (II) LoadModule: "fb"
[    24.689] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.714] (II) Module fb: vendor="X.Org Foundation"
[    24.714]     compiled for 1.10.1, module version = 1.0.0
[    24.714]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.714] (**) FBDEV(0): using shadow framebuffer
[    24.714] (II) Loading sub module "shadow"
[    24.714] (II) LoadModule: "shadow"
[    24.715] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    24.717] (II) Module shadow: vendor="X.Org Foundation"
[    24.717]     compiled for 1.10.1, module version = 1.1.0
[    24.717]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.717] (==) Depth 24 pixmap format is 32 bpp
[    24.809] (==) FBDEV(0): Backing store disabled
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.810] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.811] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.815] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.822] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.822] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.852] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.853] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.854] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.855] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.864] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.867] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.867] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.867] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.867] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.867] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.868] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.869] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.870] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.871] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.876] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.877] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.878] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.878] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    24.878] (==) FBDEV(0): DPMS enabled
[    24.878] (==) RandR enabled
[    24.878] (II) Initializing built-in extension Generic Event Extension
[    24.878] (II) Initializing built-in extension SHAPE
[    24.878] (II) Initializing built-in extension MIT-SHM
[    24.878] (II) Initializing built-in extension XInputExtension
[    24.878] (II) Initializing built-in extension XTEST
[    24.878] (II) Initializing built-in extension BIG-REQUESTS
[    24.878] (II) Initializing built-in extension SYNC
[    24.878] (II) Initializing built-in extension XKEYBOARD
[    24.878] (II) Initializing built-in extension XC-MISC
[    24.879] (II) Initializing built-in extension SECURITY
[    24.879] (II) Initializing built-in extension XINERAMA
[    24.879] (II) Initializing built-in extension XFIXES
[    24.879] (II) Initializing built-in extension RENDER
[    24.879] (II) Initializing built-in extension RANDR
[    24.879] (II) Initializing built-in extension COMPOSITE
[    24.879] (II) Initializing built-in extension DAMAGE
[    24.879] (II) Initializing built-in extension GESTURE
[    24.975] (II) AIGLX: Screen 0 is not DRI2 capable
[    24.975] (II) AIGLX: Screen 0 is not DRI capable
[    24.976] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    25.182] (II) AIGLX: Loaded and initialized swrast
[    25.182] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    25.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.484] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.484] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.484] (II) LoadModule: "evdev"
[    25.485] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.549] (II) Module evdev: vendor="X.Org Foundation"
[    25.549]     compiled for 1.10.0.902, module version = 2.6.0
[    25.549]     Module class: X.Org XInput Driver
[    25.549]     ABI class: X.Org XInput driver, version 12.3
[    25.549] (II) Using input driver 'evdev' for 'Video Bus'
[    25.549] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.550] (**) Video Bus: always reports core events
[    25.550] (**) Video Bus: Device: "/dev/input/event4"
[    25.551] (--) Video Bus: Found keys
[    25.551] (II) Video Bus: Configuring as keyboard
[    25.551] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    25.551] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.551] (**) Option "xkb_rules" "evdev"
[    25.551] (**) Option "xkb_model" "pc105"
[    25.551] (**) Option "xkb_layout" "us"
[    25.598] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.599] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.599] (II) Using input driver 'evdev' for 'Power Button'
[    25.599] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.599] (**) Power Button: always reports core events
[    25.599] (**) Power Button: Device: "/dev/input/event1"
[    25.599] (--) Power Button: Found keys
[    25.599] (II) Power Button: Configuring as keyboard
[    25.599] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.608] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.608] (**) Option "xkb_rules" "evdev"
[    25.608] (**) Option "xkb_model" "pc105"
[    25.608] (**) Option "xkb_layout" "us"
[    25.610] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.610] (II) No input driver/identifier specified (ignoring)
[    25.616] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.617] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.617] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.617] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.617] (**) Sleep Button: always reports core events
[    25.617] (**) Sleep Button: Device: "/dev/input/event2"
[    25.617] (--) Sleep Button: Found keys
[    25.617] (II) Sleep Button: Configuring as keyboard
[    25.617] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.618] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.618] (**) Option "xkb_rules" "evdev"
[    25.618] (**) Option "xkb_model" "pc105"
[    25.618] (**) Option "xkb_layout" "us"
[    25.696] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.696] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.696] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.696] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.697] (**) AT Translated Set 2 keyboard: always reports core events
[    25.697] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.697] (--) AT Translated Set 2 keyboard: Found keys
[    25.697] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.697] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.697] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.697] (**) Option "xkb_rules" "evdev"
[    25.697] (**) Option "xkb_model" "pc105"
[    25.697] (**) Option "xkb_layout" "us"
[    25.708] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.708] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.708] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.708] (II) LoadModule: "synaptics"
[    25.709] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.728] (II) Module synaptics: vendor="X.Org Foundation"
[    25.728]     compiled for 1.10.1, module version = 1.3.99
[    25.728]     Module class: X.Org XInput Driver
[    25.728]     ABI class: X.Org XInput driver, version 12.3
[    25.728] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.728] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.728] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.728] (**) Option "Device" "/dev/input/event5"
[    25.729] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.729] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.729] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.729] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.729] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.729] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.729] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.729] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    25.730] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.730] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.730] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.730] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    25.730] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.730] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.731] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.731] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.731] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    25.731] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.736] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.736] (II) No input driver/identifier specified (ignoring)
``````
xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 

```
I don't get it. lolol but for now I am going to leave everything alone until I hear back from you.:popcorn:

---

### Post by realzippy on 2011-09-26
Yep.
Rebooted?**Edit:** Means,does it persist a reboot this time?
The framebuffer driver now is running,not the intel.
Means,you have no accelerated graphics;eg
googleearth will be pretty slow.If you can live with that,we need no more messing around,although it is fun,don't you think? :p
Maybe there is a reason why canonical blacklisted the chip for 11.04...
Btw,why not running 10.04 LTS ? (afaik Intel 82845 works there)

---

### Post by JSchultheis on 2011-09-26
> **realzippy said:**
> Yep.
Rebooted?**Edit:** Means,does it persist a reboot this time?
The framebuffer driver now is running,not the intel.
Means,you have no accelerated graphics;eg
googleearth will be pretty slow.If you can live with that,we need no more messing around,although it is fun,don't you think? :p
Maybe there is a reason why canonical blacklisted the chip for 11.04...
Btw,why not running 10.04 LTS ? (afaik Intel 82845 works there)

Heck yeah man! I want googleearth and easystroke and compiz... all the goodies!!!!! lol

TBQH, this laptop is not really going to see that much GPU action, but I think I am sold on 10.04.3 LTS. Downloading now...:P

---

### Post by realzippy on 2011-09-27
Gooood Morning.
You not need to install 10.04,when you run it as live CD,you
should see in your Xorg.0.log which driver is running..

---

### Post by .... on 2011-09-27
> **JSchultheis said:**
> Heck yeah man! I want googleearth and easystroke and compiz... all the goodies!!!!! lol

TBQH, this laptop is not really going to see that much GPU action, but I think I am sold on 10.04.3 LTS. Downloading now...:P
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by realzippy on 2011-09-27
> **.... said:**
> [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


...guess this means same problems as in 10.04...  (?)

---

### Post by JSchultheis on 2011-09-27
Ended up wiping HDD and starting from scratch; nice clean install:guitar:

Fresh out of the oven, Win XP / Ubuntu 10.04.3

Currently have a large screen on first boot.





```
xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA disconnected (normal left inverted right x axis y axis)
LVDS unknown connection 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  

```

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux poslaptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=7d99d72a-d586-4a1c-9392-5e7101980061 ro quiet splash
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 27 07:26:30 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2562:1028:0149 Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF6F80000 size 524288
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(II) intel(0): No SDVO device is found in VBT
(II) intel(0): 1 display pipe available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA has no monitor section
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers/sil164.so
(II) Module sil164: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers/ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers/ivch.so
(II) Module ivch: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers/tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers/ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C device "DVOI2C_E:CH7017/7018/7019 LVDS Controller" registered at address 0xEA.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 8060 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) intel(0): Comparing regs from server start up to After PreInit
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): Kernel reported 357120 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1428476 kB available
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x007df000:            end of stolen memory
(II) intel(0): 0x007df000-0x07ffefff: DRI memory manager (123008 kB)
(II) intel(0): 0x07fff000-0x07ffffff: overlay registers (4 kB, 0x000000002e6e7000 physical
)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007df000:            start of memory manager
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00c00000-0x00c04fff: HW cursors (20 kB)
(II) intel(0): 0x07fff000:            end of memory manager
(II) intel(0): Registers before mode setting
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_INPUT: 00
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_OUTPUT: 00
(II) intel(0): CH7017_VERTICAL_ACTIVE_LINE_OUTPUT: 00
(II) intel(0): CH7017_ACTIVE_INPUT_LINE_OUTPUT: 1a
(II) intel(0): CH7017_LVDS_PLL_VCO_CONTROL: ad
(II) intel(0): CH7017_LVDS_PLL_FEEDBACK_DIV: ad
(II) intel(0): CH7017_LVDS_CONTROL_2: 80
(II) intel(0): CH7017_OUTPUTS_ENABLE: c8
(II) intel(0): CH7017_LVDS_POWER_DOWN: 53
(II) intel(0): Registers after mode setting
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_INPUT: 00
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_OUTPUT: 00
(II) intel(0): CH7017_VERTICAL_ACTIVE_LINE_OUTPUT: 00
(II) intel(0): CH7017_ACTIVE_INPUT_LINE_OUTPUT: 1c
(II) intel(0): CH7017_LVDS_PLL_VCO_CONTROL: a3
(II) intel(0): CH7017_LVDS_PLL_FEEDBACK_DIV: ad
(II) intel(0): CH7017_LVDS_CONTROL_2: 20
(II) intel(0): CH7017_OUTPUTS_ENABLE: 08
(II) intel(0): CH7017_LVDS_POWER_DOWN: 0c
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
```


I like the full size screen but wonder if it will last! :)

---

### Post by realzippy on 2011-09-27
Hi there...
That log looks good.
Intel driver running,accelerated (DRI2) graphics,resolution correct.

```
(II) intel(0): Output LVDS using initial mode 1024x768
```

If it persisted 1rst reboot,it likely will be allright....

....so     :popcorn:     **?**
zippy

---

### Post by JSchultheis on 2011-09-27
Well I hear a loud login sound, and that is it. Eventually a screen starts blinking with white vertical lines. 

I think there may be no resolve for this old laptop.

---

### Post by realzippy on 2011-09-27
So same effect as usual?
I think it is pretty strange that it works fine,and after a reboot
it gets stuck.
I mean,it is no coffee machine.....
This might be worth a new thread...

Do you want to try disabling KernelModeSetting and setting up VESA ?

---

### Post by JSchultheis on 2011-09-27
this laptop is a joke
lol

---

### Post by JSchultheis on 2011-09-30
Joke as it may be, I haven't quite given up.
I started over with a new install, and I am no longer dual booting.
I installed Jaunty Jackaloupe, then through Update Manager, I upgraded all the way to Lucid Lynx 10.04.3

Jaunty Jackaloupe gave the option of 640x480 or 800x600 monitors, so I was happy to upgrade from there, although I would really like to get to 10242x768.

Well as I was writing this out, I decided to start over at the beginning of the thread: 

> **realzippy said:**
> ```
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
sudo update-initramfs -u -k all
```Run those commands to add *glasen's* patched intel drivers.
Since Canonical blacklisted i830, i845 und i855 in 11.04,also run:

```
gksudo gedit /etc/X11/xorg.conf
```Paste in:
```
Section "Device"
Identifier "Card0"
Driver "intel"
EndSection
```Reboot.
If no success,post again

```
xrandr -q
```and

```
cat /var/log/Xorg.0.log
``````
lshw -c video
```


So that is what I did and now I have a full display. I tested it for several restarts and used the P.O.S. laptop for several hours last night and this morning and the screen is still 1024x768.

One note: an actual xorg.conf came up, full of several details when I went to paste in the info quoted, so I mv the file and created a new xorg.conf putting in the info above. Upon that restart I finally had full screen!

```
xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 unknown connection 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

``````
cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux poslaptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686
Kernel command line: root=UUID=24e80428-1d46-4945-8097-c010a629f55d ro xforcevesa quiet splash 
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 30 08:02:25 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
(**) |   |-->Device "Card0"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2562:1028:0149 Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.15.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: Interface 1.4 failed, trying 1.1
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(**) intel(0): Relaxed fencing disabled
(**) intel(0): Framebuffer tiled
(**) intel(0): Pixmaps tiled
(**) intel(0): 3D buffers tiled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 connected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(II) intel(0): Output LVDS1 using initial mode 1024x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): Kernel page flipping support detected, enabling
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "dri2"
(II) LoadModule: "dri2"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(II)         get_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
(==) intel(0): hotplug detection: "enabled"
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

``````
lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff(prefetchable) memory:f6f80000-f6ffffff

``````
gksudo gedit /etc/X11/xorg.conf

Section "Device"
Identifier "Card0"
Driver "intel"
EndSection
```
```
uname -a
Linux poslaptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

```So it is finally done! Thank you realzippy for sticking with me and encouraging me to beat this challenge8-)

---

### Post by RichiePantsBegone on 2012-06-14
I should mention I am a completely new user that has already spent days searching everywhere for a solution.  

I am trying this with all the same hardware but with the newest ubuntu release of 12.04.  I see all the processes for the end summary worked correctly save editing '/etc/X11/xorg.conf'.  This was a blank file. I assume it has to do with the version this was perfected on was 11 and this version is 12.  Regardless, all effects seemed to take place smoothly up to this point.  

What changes for these instructions when using version 12.04?

Cheers

---

