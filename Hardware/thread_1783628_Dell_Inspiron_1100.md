---
title: "Dell Inspiron 1100"
date: 2011-06-16
forum: Hardware
---

### Post by zaboo_3.0 on 2011-06-16
Hi I am still fairly new to linux. I have this old dell inspiron 1100 laptop laying around the house and thought it would be fun project to install linux on and learn it.  I installed xubuntu 11.04.  I am having display issues.  It is stuck in lower res and much of the screen is black.  I tried searching for the answer in forms and can't find anything that works. Help would be greatly appreciated. 

Thnanks

---

### Post by Toz on 2011-06-16
Can we see a copy of your **/var/log/Xorg.0.log** file? And also, open a terminal window, type in the following command, and post back the results:```
lspci | grep VGA
```

---

### Post by zaboo_3.0 on 2011-06-17
Thanks I figured it out.  Display is working great now But having more hardware issues. Battery is dead and have to keep plugged in now and the pwr connector on the motherboard itself is not getting good connection.  Already bought a new pwr cord don't want to put anymore money into it. So i am going to just buy an asus Eee PC 1215b and replace windows with Xubuntu :-)

---

### Post by Rob Glenn on 2011-06-23
May I ask how you fixed the low resolution display issue?

---

### Post by Toz on 2011-06-23
Feel free to post a copy of your **/var/log/Xorg.0.log** file so we can have a look and see whats happening.

Also, what kind of video card is in it the system? Open a terminal window, type in the following command, and post back the results:```
lspci -v | grep VGA
```

---

### Post by azure kitsune on 2011-06-29
Hello. I also installed Xubuntu 11.04 on my Dell Inspiron 1100 and I am having trouble with the display as well. I have attached a picture of what the screen looks like.

Here is a copy of my **/var/log/Xorg.0.log** file:

```

[    36.599] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    36.600] X Protocol Version 11, Revision 0
[    36.600] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    36.600] Current Operating System: Linux ryan-Inspiron-1100 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    36.600] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=648cae40-5dcf-4689-b587-ea8ad9de32c6 ro quiet splash vt.handoff=7
[    36.600] Build Date: 19 April 2011  03:33:17PM
[    36.600] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    36.658] Current version of pixman: 0.20.2
[    36.658]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.659] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.659] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 29 13:08:18 2011
[    36.849] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    37.156] (==) No Layout section.  Using the first Screen section.
[    37.156] (==) No screen section available. Using defaults.
[    37.156] (**) |-->Screen "Default Screen Section" (0)
[    37.156] (**) |   |-->Monitor "<default monitor>"
[    37.179] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    37.179] (==) Automatically adding devices
[    37.179] (==) Automatically enabling devices
[    37.180] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    37.180]     Entry deleted from font path.
[    37.180] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    37.180]     Entry deleted from font path.
[    37.180] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    37.180]     Entry deleted from font path.
[    37.180] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    37.181]     Entry deleted from font path.
[    37.181] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    37.181]     Entry deleted from font path.
[    37.242] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    37.242] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    37.242] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    37.242] (II) Loader magic: 0x81ffde0
[    37.242] (II) Module ABI versions:
[    37.242]     X.Org ANSI C Emulation: 0.4
[    37.242]     X.Org Video Driver: 10.0
[    37.242]     X.Org XInput driver : 12.3
[    37.242]     X.Org Server Extension : 5.0
[    37.245] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    37.245] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    37.246] (II) LoadModule: "extmod"
[    37.437] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    37.532] (II) Module extmod: vendor="X.Org Foundation"
[    37.532]     compiled for 1.10.1, module version = 1.0.0
[    37.532]     Module class: X.Org Server Extension
[    37.532]     ABI class: X.Org Server Extension, version 5.0
[    37.533] (II) Loading extension MIT-SCREEN-SAVER
[    37.533] (II) Loading extension XFree86-VidModeExtension
[    37.533] (II) Loading extension XFree86-DGA
[    37.557] (II) Loading extension DPMS
[    37.558] (II) Loading extension XVideo
[    37.558] (II) Loading extension XVideo-MotionCompensation
[    37.558] (II) Loading extension X-Resource
[    37.558] (II) LoadModule: "dbe"
[    37.559] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    37.565] (II) Module dbe: vendor="X.Org Foundation"
[    37.565]     compiled for 1.10.1, module version = 1.0.0
[    37.565]     Module class: X.Org Server Extension
[    37.565]     ABI class: X.Org Server Extension, version 5.0
[    37.565] (II) Loading extension DOUBLE-BUFFER
[    37.565] (II) LoadModule: "glx"
[    37.566] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    37.713] (II) Module glx: vendor="X.Org Foundation"
[    37.713]     compiled for 1.10.1, module version = 1.0.0
[    37.713]     ABI class: X.Org Server Extension, version 5.0
[    37.723] (==) AIGLX enabled
[    37.723] (II) Loading extension GLX
[    37.723] (II) LoadModule: "record"
[    37.724] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    37.844] (II) Module record: vendor="X.Org Foundation"
[    37.844]     compiled for 1.10.1, module version = 1.13.0
[    37.844]     Module class: X.Org Server Extension
[    37.844]     ABI class: X.Org Server Extension, version 5.0
[    37.844] (II) Loading extension RECORD
[    37.844] (II) LoadModule: "dri"
[    37.845] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    37.978] (II) Module dri: vendor="X.Org Foundation"
[    37.978]     compiled for 1.10.1, module version = 1.0.0
[    37.978]     ABI class: X.Org Server Extension, version 5.0
[    37.978] (II) Loading extension XFree86-DRI
[    37.979] (II) LoadModule: "dri2"
[    37.979] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    38.054] (II) Module dri2: vendor="X.Org Foundation"
[    38.054]     compiled for 1.10.1, module version = 1.2.0
[    38.054]     ABI class: X.Org Server Extension, version 5.0
[    38.054] (II) Loading extension DRI2
[    38.054] (==) Matched vesa as autoconfigured driver 0
[    38.054] (==) Matched fbdev as autoconfigured driver 1
[    38.054] (==) Assigned the driver to the xf86ConfigLayout
[    38.054] (II) LoadModule: "vesa"
[    38.080] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.180] (II) Module vesa: vendor="X.Org Foundation"
[    38.180]     compiled for 1.10.0, module version = 2.3.0
[    38.181]     Module class: X.Org Video Driver
[    38.181]     ABI class: X.Org Video Driver, version 10.0
[    38.181] (II) LoadModule: "fbdev"
[    38.182] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.360] (II) Module fbdev: vendor="X.Org Foundation"
[    38.360]     compiled for 1.10.0, module version = 0.4.2
[    38.360]     ABI class: X.Org Video Driver, version 10.0
[    38.360] (II) VESA: driver for VESA chipsets: vesa
[    38.360] (II) FBDEV: driver for framebuffer: fbdev
[    38.360] (++) using VT number 7

[    38.361] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    38.361] (WW) Falling back to old probe method for vesa
[    38.361] (II) Loading sub module "fbdevhw"
[    38.361] (II) LoadModule: "fbdevhw"
[    38.362] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.517] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.518]     compiled for 1.10.1, module version = 0.0.2
[    38.518]     ABI class: X.Org Video Driver, version 10.0
[    38.518] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.518] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.518] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    38.518] (II) FBDEV(0): using default device
[    38.519] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    38.519] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    38.519] (==) FBDEV(0): RGB weight 888
[    38.519] (==) FBDEV(0): Default visual is TrueColor
[    38.519] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    38.519] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    38.519] (II) FBDEV(0): checking modes against framebuffer device...
[    38.519] (II) FBDEV(0): checking modes against monitor...
[    38.520] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    38.520] (**) FBDEV(0):  Built-in mode "current"
[    38.520] (==) FBDEV(0): DPI set to (96, 96)
[    38.520] (II) Loading sub module "fb"
[    38.520] (II) LoadModule: "fb"
[    38.521] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.523] (II) Module fb: vendor="X.Org Foundation"
[    38.523]     compiled for 1.10.1, module version = 1.0.0
[    38.523]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.523] (**) FBDEV(0): using shadow framebuffer
[    38.523] (II) Loading sub module "shadow"
[    38.524] (II) LoadModule: "shadow"
[    38.524] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    38.528] (II) Module shadow: vendor="X.Org Foundation"
[    38.528]     compiled for 1.10.1, module version = 1.1.0
[    38.528]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.528] (==) Depth 24 pixmap format is 32 bpp
[    38.729] (==) FBDEV(0): Backing store disabled
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.731] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.732] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.733] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.734] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.735] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.741] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.741] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.741] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.741] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.741] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.742] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.743] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.744] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.744] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.745] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.745] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.745] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.746] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.746] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.746] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.746] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.747] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.747] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.747] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.748] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.748] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.748] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.748] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.749] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.749] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.749] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.750] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.750] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.751] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.751] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.751] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.751] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.753] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.753] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.753] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.753] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.753] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.754] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.755] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.756] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.756] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.757] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.758] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.758] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.758] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.758] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.758] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.760] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.760] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.760] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.760] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.760] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.761] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.761] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.761] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.761] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.762] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.763] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.763] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.763] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.763] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.764] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.764] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.764] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.764] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.765] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.765] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.766] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.769] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.769] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.769] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.769] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.770] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.771] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.772] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.773] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.774] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.775] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.784] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.784] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.784] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    38.784] (==) FBDEV(0): DPMS enabled
[    38.784] (==) RandR enabled
[    38.784] (II) Initializing built-in extension Generic Event Extension
[    38.784] (II) Initializing built-in extension SHAPE
[    38.784] (II) Initializing built-in extension MIT-SHM
[    38.784] (II) Initializing built-in extension XInputExtension
[    38.784] (II) Initializing built-in extension XTEST
[    38.785] (II) Initializing built-in extension BIG-REQUESTS
[    38.785] (II) Initializing built-in extension SYNC
[    38.785] (II) Initializing built-in extension XKEYBOARD
[    38.785] (II) Initializing built-in extension XC-MISC
[    38.785] (II) Initializing built-in extension SECURITY
[    38.785] (II) Initializing built-in extension XINERAMA
[    38.785] (II) Initializing built-in extension XFIXES
[    38.785] (II) Initializing built-in extension RENDER
[    38.785] (II) Initializing built-in extension RANDR
[    38.785] (II) Initializing built-in extension COMPOSITE
[    38.785] (II) Initializing built-in extension DAMAGE
[    38.785] (II) Initializing built-in extension GESTURE
[    39.141] (II) AIGLX: Screen 0 is not DRI2 capable
[    39.141] (II) AIGLX: Screen 0 is not DRI capable
[    39.141] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    41.686] (II) AIGLX: Loaded and initialized swrast
[    41.692] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    42.346] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    43.522] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    43.522] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.522] (II) LoadModule: "evdev"
[    43.559] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.622] (II) Module evdev: vendor="X.Org Foundation"
[    43.622]     compiled for 1.10.0.902, module version = 2.6.0
[    43.622]     Module class: X.Org XInput Driver
[    43.622]     ABI class: X.Org XInput driver, version 12.3
[    43.622] (II) Using input driver 'evdev' for 'Video Bus'
[    43.623] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.623] (**) Video Bus: always reports core events
[    43.623] (**) Video Bus: Device: "/dev/input/event5"
[    43.623] (--) Video Bus: Found keys
[    43.623] (II) Video Bus: Configuring as keyboard
[    43.623] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input5/event5"
[    43.624] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    43.624] (**) Option "xkb_rules" "evdev"
[    43.624] (**) Option "xkb_model" "pc105"
[    43.624] (**) Option "xkb_layout" "us"
[    43.664] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    43.664] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.664] (II) Using input driver 'evdev' for 'Power Button'
[    43.664] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.664] (**) Power Button: always reports core events
[    43.664] (**) Power Button: Device: "/dev/input/event1"
[    43.665] (--) Power Button: Found keys
[    43.665] (II) Power Button: Configuring as keyboard
[    43.665] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    43.665] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    43.665] (**) Option "xkb_rules" "evdev"
[    43.665] (**) Option "xkb_model" "pc105"
[    43.665] (**) Option "xkb_layout" "us"
[    43.671] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    43.671] (II) No input driver/identifier specified (ignoring)
[    43.673] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    43.673] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    43.673] (II) Using input driver 'evdev' for 'Sleep Button'
[    43.673] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.674] (**) Sleep Button: always reports core events
[    43.674] (**) Sleep Button: Device: "/dev/input/event2"
[    43.674] (--) Sleep Button: Found keys
[    43.674] (II) Sleep Button: Configuring as keyboard
[    43.674] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    43.674] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    43.674] (**) Option "xkb_rules" "evdev"
[    43.674] (**) Option "xkb_model" "pc105"
[    43.674] (**) Option "xkb_layout" "us"
[    43.702] (II) config/udev: Adding input device HID 04b3:3109 (/dev/input/event4)
[    43.702] (**) HID 04b3:3109: Applying InputClass "evdev pointer catchall"
[    43.702] (II) Using input driver 'evdev' for 'HID 04b3:3109'
[    43.702] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.703] (**) HID 04b3:3109: always reports core events
[    43.703] (**) HID 04b3:3109: Device: "/dev/input/event4"
[    43.703] (--) HID 04b3:3109: Found 3 mouse buttons
[    43.703] (--) HID 04b3:3109: Found scroll wheel(s)
[    43.703] (--) HID 04b3:3109: Found relative axes
[    43.703] (--) HID 04b3:3109: Found x and y relative axes
[    43.703] (II) HID 04b3:3109: Configuring as mouse
[    43.703] (II) HID 04b3:3109: Adding scrollwheel support
[    43.703] (**) HID 04b3:3109: YAxisMapping: buttons 4 and 5
[    43.716] (**) HID 04b3:3109: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.716] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4/event4"
[    43.716] (II) XINPUT: Adding extended input device "HID 04b3:3109" (type: MOUSE)
[    43.716] (II) HID 04b3:3109: initialized for relative axes.
[    43.716] (**) HID 04b3:3109: (accel) keeping acceleration scheme 1
[    43.717] (**) HID 04b3:3109: (accel) acceleration profile 0
[    43.717] (**) HID 04b3:3109: (accel) acceleration factor: 2.000
[    43.717] (**) HID 04b3:3109: (accel) acceleration threshold: 4
[    43.718] (II) config/udev: Adding input device HID 04b3:3109 (/dev/input/mouse0)
[    43.718] (II) No input driver/identifier specified (ignoring)
[    43.794] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    43.794] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    43.794] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    43.794] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.794] (**) AT Translated Set 2 keyboard: always reports core events
[    43.795] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    43.795] (--) AT Translated Set 2 keyboard: Found keys
[    43.795] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    43.795] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    43.795] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    43.795] (**) Option "xkb_rules" "evdev"
[    43.795] (**) Option "xkb_model" "pc105"
[    43.795] (**) Option "xkb_layout" "us"
[    43.798] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    43.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    43.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    43.798] (II) LoadModule: "synaptics"
[    43.799] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.833] (II) Module synaptics: vendor="X.Org Foundation"
[    43.833]     compiled for 1.10.0.902, module version = 1.3.99
[    43.833]     Module class: X.Org XInput Driver
[    43.833]     ABI class: X.Org XInput driver, version 12.3
[    43.833] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    43.833] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.833] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.833] (**) Option "Device" "/dev/input/event6"
[    43.834] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    43.834] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    43.834] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    43.834] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    43.834] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    43.834] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.834] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.834] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    43.834] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    43.835] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    43.835] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    43.835] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    43.835] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    43.835] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    43.835] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    43.839] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    43.840] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    43.840] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.841] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    43.841] (II) No input driver/identifier specified (ignoring)

```And here is what I get by running **lspci -v | grep VGA** :

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

Does anyone have any suggestions on how to fix this? Thanks! :)

---

### Post by Toz on 2011-06-29
See:

[http://ubuntuforums.org/showpost.php?p=3705155&postcount=8]("http://ubuntuforums.org/showpost.php?p=3705155&postcount=8") 

Point #4 in that list refers this xorg.conf file: [http://ubuntuforums.org/showpost.php?p=3692801&postcount=7]("http://ubuntuforums.org/showpost.php?p=3692801&postcount=7")

You might also have to boot with the **nomodeset** or **i915.modeset=1** kernel parameters. See here for instructions on how to do it temporarily during boot for testing: [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot")

---

### Post by azure kitsune on 2011-06-30
Thanks for the response! I tried those changes, but they didn't work out that well. (I think it might be because they don't apply well to 11.04. For example, the 915resolution package doesn't exist anymore.)

I tried creating the xorg.conf file, but when I restarted the computer, I couldn't get to the log-in screen. The screen turned black before I got there.

---

### Post by Toz on 2011-06-30
> [    38.361] (EE) VESA: Kernel modesetting driver in use, refusing to load

What happens if you boot with only the kernel parameters **nomodeset** or **i915.modeset=0** (no xorg.conf file)?

Maybe you can post back the Xorg.0.log files for each attempt.

---

### Post by Rbgtag on 2011-08-03
> **azure kitsune said:**
> Thanks for the response! I tried those changes, but they didn't work out that well. (I think it might be because they don't apply well to 11.04. For example, the 915resolution package doesn't exist anymore.)

I tried creating the xorg.conf file, but when I restarted the computer, I couldn't get to the log-in screen. The screen turned black before I got there.

Did you ever get this fixed.  I am having the same problem.  Finally got bios updated, but can't seem to get the video issue fixed.

Scott

---

### Post by azure kitsune on 2011-08-09
I'm sorry for this late response. I was trying to help fix my parents's old computer when I was staying with them, but I had to leave, so I haven't had time to try and fix it. I never got the problem resolved.

---

### Post by T J Wells on 2011-10-20
I have a Dell Inspiron 1100 with 512 of ram.  On 10/19/2011 I switched to Linux Mint Debian and it work at 1024 x 768 resolution.  Also I previously used Linux Mint 10.0 and it worked well.  Mint 11.0 based on Ubuntu and Ubuntu 11.04 and 11.10 did not work above 640 x 480.

---

### Post by reap3r119 on 2012-09-24
I apologize for replying to an old thread, but I've spent two and a half days going through page after page of everything I could find regarding this. I have the xorg.conf file fixed, I tried using kernel parameters **nomodeset**, **i915.modeset=0**, and **i915.modeset=1** (i915.modeset=1 fixed it temporarily), but the fixes aren't working since I'm using BIOS A27. 

I have two files: I1100A32.exe and I1100A32.iso. The .exe is useless since I'm using Xubuntu and Wine can't make it work. Is there any way to update the BIOS using a USB Flash Drive instead of a CD? I tried using **dd** to flash it onto the USB, but I can't get it to update. Is it possible to do it from a USB, or do I have to buy a CD?

---

### Post by BigD77 on 2012-10-20
I have the same problem occasionally since installing 12.04.  I have to shut the laptop off and restart.  Most times that takes care of the problem. 

I had the same problem with all varieties of 11.10, Ubuntu, Lubuntu, Kubuntu, and Xubuntu. 

What I did was upgrade the BIOS to the latest version.

Update the video memory in the BIOS to 8MB from 1MB

Run the 915 resolution (Which I have seen in other threads no longer exists.

However, it does get frustrating having to shut off the laptop and restart it.  

10.10 was the last version that I had absolutely no problems with.

---

