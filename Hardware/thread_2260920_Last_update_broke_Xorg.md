---
title: "Last update broke Xorg"
date: 2015-01-15
forum: Hardware
---

### Post by TWFJR on 2015-01-15
The last "Software Update," where there was a kernel update broke Xorg. ddcprobe shows that I have a GK104 Board - 20040001 Chip Rev, memory 14336kb; this is NVIDIA graphics. I am running Intel Core i7-3960X CPU @ 3.30GHz X 12, 62.4 GiB memory, 64 bit, 876.9 GB with RAID 0. Using X.OrgX server - Noueau display driver. I believe this driver now has a bug. I really don't know what to call the problem. I do not understand enough about what or how to discover the real problem. I do wonder if I can resolve this problem by simply removing the driver and installing another driver, proprietary driver like NVIDIA binary driver 331.113 . . . updates. Please advise regarding possible bug and whether changing the graphics driver will solve the problem. Is NVIDIA binary driver 331.113 going to work with my graphics board? Will I need to change to version 331.113 that has been tested first before updating to 331 update? I read where I should update the graphics driver and all hardware before reporting a bug.

Unity icons are large and 2nd monitor is not recognized.

---

### Post by Sally_Joshua on 2015-01-15
something in the kernel already bound the video card and prevents the driver to do his job properly. Try setting the distorted displays to 1920x1080@60 using xrandr:

---

### Post by TWFJR on 2015-01-15
Thanks, I am not literate enough with 'xrandr' to understand the options and where I should be changing the displays to 1920x1080@60. 

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

 "Failed to get size of gamma for output default" seems to be causing a problem to move forward.

---

### Post by Yellow Pasque on 2015-01-15
> **TWFJR said:**
> Is NVIDIA binary driver 331.113 going to work with my graphics board?

Theoretically, it should support it. Only one way to find out..

> Will I need to change to version 331.113 that has been tested first before updating to 331 update?

Right now, nvidia-331-updates also has 331.113 driver, so it is exactly the same as nvidia-331.

>  I do not understand enough about what or how to discover the real problem
Pastebin your /var/log/Xorg.0.log file (or post it, but make sure you use code tags since it's a lot of text).

---

### Post by kurt18947 on 2015-01-15
I have simpler Nvidia cards (Geforce 210?) and the Nouveau driver has not worked well for quite some time. I have what may be an odd setup in that I have AMD based systems with ATI/AMD onboard video disabled and Nvidia PCIe cards active.  Activating the Nvidia drivers seems to fix any driver problem.

---

### Post by TWFJR on 2015-01-16
I hope that I've used "tags" correctly. If not, my apologies.

```
[     4.737] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[     4.737] X Protocol Version 11, Revision 0
[     4.737] Build Operating System: Linux 3.2.0-54-generic x86_64 Ubuntu
[     4.737] Current Operating System: Linux tom-desktop 3.16.0-29-generic #39-Ubuntu SMP Mon Dec 15 22:27:29 UTC 2014 x86_64
[     4.737] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-29-generic root=UUID=93d2b3b2-48dd-499b-8d41-6ac3bcb0e68d ro quiet splash vt.handoff=7
[     4.737] Build Date: 09 December 2014  11:01:03PM
[     4.737] xorg-server 2:1.16.0-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.737] Current version of pixman: 0.32.4
[     4.737]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.737] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.737] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 14 15:30:29 2015
[     4.738] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.738] (==) No Layout section.  Using the first Screen section.
[     4.738] (==) No screen section available. Using defaults.
[     4.738] (**) |-->Screen "Default Screen Section" (0)
[     4.738] (**) |   |-->Monitor "<default monitor>"
[     4.738] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.738] (==) Automatically adding devices
[     4.738] (==) Automatically enabling devices
[     4.738] (==) Automatically adding GPU devices
[     4.739] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.739]     Entry deleted from font path.
[     4.739] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.739]     Entry deleted from font path.
[     4.739] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.739]     Entry deleted from font path.
[     4.739] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.739]     Entry deleted from font path.
[     4.739] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.739]     Entry deleted from font path.
[     4.739] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.739] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.739] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.739] (II) Loader magic: 0x7f7597e93d80
[     4.739] (II) Module ABI versions:
[     4.739]     X.Org ANSI C Emulation: 0.4
[     4.739]     X.Org Video Driver: 18.0
[     4.739]     X.Org XInput driver : 21.0
[     4.739]     X.Org Server Extension : 8.0
[     4.742] (--) PCI:*(0:2:0:0) 10de:1183:1043:841f rev 161, Mem @ 0xea000000/16777216, 0xe0000000/134217728, 0xe8000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[     4.742] (II) LoadModule: "glx"
[     4.743] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.749] (II) Module glx: vendor="X.Org Foundation"
[     4.749]     compiled for 1.16.0, module version = 1.0.0
[     4.749]     ABI class: X.Org Server Extension, version 8.0
[     4.749] (==) AIGLX enabled
[     4.749] (==) Matched nvidia as autoconfigured driver 0
[     4.749] (==) Matched nouveau as autoconfigured driver 1
[     4.749] (==) Matched modesetting as autoconfigured driver 2
[     4.749] (==) Matched fbdev as autoconfigured driver 3
[     4.749] (==) Matched vesa as autoconfigured driver 4
[     4.749] (==) Assigned the driver to the xf86ConfigLayout
[     4.749] (II) LoadModule: "nvidia"
[     4.750] (WW) Warning, couldn't open module nvidia
[     4.750] (II) UnloadModule: "nvidia"
[     4.750] (II) Unloading nvidia
[     4.750] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.750] (II) LoadModule: "nouveau"
[     4.750] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.752] (II) Module nouveau: vendor="X.Org Foundation"
[     4.752]     compiled for 1.16.0, module version = 1.0.11
[     4.752]     Module class: X.Org Video Driver
[     4.752]     ABI class: X.Org Video Driver, version 18.0
[     4.752] (II) LoadModule: "modesetting"
[     4.752] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.752] (II) Module modesetting: vendor="X.Org Foundation"
[     4.752]     compiled for 1.16.0, module version = 0.9.0
[     4.752]     Module class: X.Org Video Driver
[     4.752]     ABI class: X.Org Video Driver, version 18.0
[     4.752] (II) LoadModule: "fbdev"
[     4.753] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.753] (II) Module fbdev: vendor="X.Org Foundation"
[     4.753]     compiled for 1.16.0, module version = 0.4.4
[     4.753]     Module class: X.Org Video Driver
[     4.753]     ABI class: X.Org Video Driver, version 18.0
[     4.753] (II) LoadModule: "vesa"
[     4.753] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.754] (II) Module vesa: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 2.3.3
[     4.754]     Module class: X.Org Video Driver
[     4.754]     ABI class: X.Org Video Driver, version 18.0
[     4.754] (==) Matched nvidia as autoconfigured driver 0
[     4.754] (==) Matched nouveau as autoconfigured driver 1
[     4.754] (==) Matched modesetting as autoconfigured driver 2
[     4.754] (==) Matched fbdev as autoconfigured driver 3
[     4.754] (==) Matched vesa as autoconfigured driver 4
[     4.754] (==) Assigned the driver to the xf86ConfigLayout
[     4.754] (II) LoadModule: "nvidia"
[     4.754] (WW) Warning, couldn't open module nvidia
[     4.754] (II) UnloadModule: "nvidia"
[     4.754] (II) Unloading nvidia
[     4.754] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.754] (II) LoadModule: "nouveau"
[     4.754] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.754] (II) Module nouveau: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 1.0.11
[     4.754]     Module class: X.Org Video Driver
[     4.754]     ABI class: X.Org Video Driver, version 18.0
[     4.754] (II) UnloadModule: "nouveau"
[     4.754] (II) Unloading nouveau
[     4.754] (II) Failed to load module "nouveau" (already loaded, 0)
[     4.754] (II) LoadModule: "modesetting"
[     4.754] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.754] (II) Module modesetting: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 0.9.0
[     4.754]     Module class: X.Org Video Driver
[     4.754]     ABI class: X.Org Video Driver, version 18.0
[     4.754] (II) UnloadModule: "modesetting"
[     4.754] (II) Unloading modesetting
[     4.754] (II) Failed to load module "modesetting" (already loaded, 0)
[     4.754] (II) LoadModule: "fbdev"
[     4.754] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.754] (II) Module fbdev: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 0.4.4
[     4.754]     Module class: X.Org Video Driver
[     4.754]     ABI class: X.Org Video Driver, version 18.0
[     4.754] (II) UnloadModule: "fbdev"
[     4.754] (II) Unloading fbdev
[     4.754] (II) Failed to load module "fbdev" (already loaded, 0)
[     4.754] (II) LoadModule: "vesa"
[     4.754] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.754] (II) Module vesa: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 2.3.3
[     4.754]     Module class: X.Org Video Driver
[     4.754]     ABI class: X.Org Video Driver, version 18.0
[     4.754] (II) UnloadModule: "vesa"
[     4.754] (II) Unloading vesa
[     4.754] (II) Failed to load module "vesa" (already loaded, 0)
[     4.754] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[     4.754] (II) NOUVEAU driver for NVIDIA chipset families :
[     4.754]     RIVA TNT        (NV04)
[     4.754]     RIVA TNT2       (NV05)
[     4.754]     GeForce 256     (NV10)
[     4.754]     GeForce 2       (NV11, NV15)
[     4.755]     GeForce 4MX     (NV17, NV18)
[     4.755]     GeForce 3       (NV20)
[     4.755]     GeForce 4Ti     (NV25, NV28)
[     4.755]     GeForce FX      (NV3x)
[     4.755]     GeForce 6       (NV4x)
[     4.755]     GeForce 7       (G7x)
[     4.755]     GeForce 8       (G8x)
[     4.755]     GeForce GTX 200 (NVA0)
[     4.755]     GeForce GTX 400 (NVC0)
[     4.755] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.755] (II) FBDEV: driver for framebuffer: fbdev
[     4.755] (II) VESA: driver for VESA chipsets: vesa
[     4.755] (++) using VT number 7

[     4.755] (EE) [drm] KMS not enabled
[     4.755] (EE) [drm] KMS not enabled
[     4.755] (EE) open /dev/dri/card0: No such file or directory
[     4.755] (EE) open /dev/dri/card0: No such file or directory
[     4.755] (WW) Falling back to old probe method for modesetting
[     4.755] (EE) open /dev/dri/card0: No such file or directory
[     4.755] (EE) open /dev/dri/card0: No such file or directory
[     4.755] (II) Loading sub module "fbdevhw"
[     4.755] (II) LoadModule: "fbdevhw"
[     4.755] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.755] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.755]     compiled for 1.16.0, module version = 0.0.2
[     4.755]     ABI class: X.Org Video Driver, version 18.0
[     4.755] (EE) open /dev/fb0: No such file or directory
[     4.755] (II) Loading sub module "fbdevhw"
[     4.755] (II) LoadModule: "fbdevhw"
[     4.755] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.755] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.755]     compiled for 1.16.0, module version = 0.0.2
[     4.755]     ABI class: X.Org Video Driver, version 18.0
[     4.755] (EE) open /dev/fb0: No such file or directory
[     4.755] (WW) Falling back to old probe method for fbdev
[     4.755] (II) Loading sub module "fbdevhw"
[     4.755] (II) LoadModule: "fbdevhw"
[     4.756] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.756] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.756]     compiled for 1.16.0, module version = 0.0.2
[     4.756]     ABI class: X.Org Video Driver, version 18.0
[     4.756] (EE) open /dev/fb0: No such file or directory
[     4.756] (EE) open /dev/fb0: No such file or directory
[     4.756] (EE) Screen 0 deleted because of no matching config section.
[     4.756] (II) UnloadModule: "modesetting"
[     4.756] (EE) Screen 0 deleted because of no matching config section.
[     4.756] (II) UnloadModule: "modesetting"
[     4.756] (EE) Screen 0 deleted because of no matching config section.
[     4.756] (II) UnloadModule: "fbdev"
[     4.756] (II) UnloadSubModule: "fbdevhw"
[     4.756] (EE) Screen 0 deleted because of no matching config section.
[     4.756] (II) UnloadModule: "fbdev"
[     4.756] (II) UnloadSubModule: "fbdevhw"
[     4.756] (II) UnloadSubModule: "fbdevhw"
[     4.756] (II) Loading sub module "vbe"
[     4.756] (II) LoadModule: "vbe"
[     4.756] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     4.756] (II) Module vbe: vendor="X.Org Foundation"
[     4.756]     compiled for 1.16.0, module version = 1.1.0
[     4.756]     ABI class: X.Org Video Driver, version 18.0
[     4.756] (II) Loading sub module "int10"
[     4.756] (II) LoadModule: "int10"
[     4.756] (II) Loading /usr/lib/xorg/modules/libint10.so
[     4.757] (II) Module int10: vendor="X.Org Foundation"
[     4.757]     compiled for 1.16.0, module version = 1.0.0
[     4.757]     ABI class: X.Org Video Driver, version 18.0
[     4.757] (II) VESA(0): initializing int10
[     4.758] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[     4.801] (II) VESA(0): VESA BIOS detected
[     4.801] (II) VESA(0): VESA VBE Version 3.0
[     4.801] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[     4.801] (II) VESA(0): VESA VBE OEM: NVIDIA
[     4.801] (II) VESA(0): VESA VBE OEM Software Rev: 128.4
[     4.801] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[     4.801] (II) VESA(0): VESA VBE OEM Product: GK104 Board - 20040001
[     4.801] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[     4.875] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     4.875] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[     4.875] (==) VESA(0): RGB weight 888
[     4.875] (==) VESA(0): Default visual is TrueColor
[     4.875] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[     4.875] (II) Loading sub module "ddc"
[     4.875] (II) LoadModule: "ddc"
[     4.875] (II) Module "ddc" already built-in
[     4.876] (II) VESA(0): VESA VBE DDC supported
[     4.876] (II) VESA(0): VESA VBE DDC Level 2
[     4.876] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[     4.909] (II) VESA(0): VESA VBE DDC read successfully
[     4.909] (II) VESA(0): Manufacturer: ACI  Model: 249a  Serial#: 47478
[     4.909] (II) VESA(0): Year: 2012  Week: 28
[     4.909] (II) VESA(0): EDID Version: 1.3
[     4.909] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[     4.909] (II) VESA(0): Sync:  Separate
[     4.909] (II) VESA(0): Max Image Size [cm]: horiz.: 52  vert.: 29
[     4.909] (II) VESA(0): Gamma: 2.20
[     4.909] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[     4.909] (II) VESA(0): First detailed timing is preferred mode
[     4.909] (II) VESA(0): redX: 0.641 redY: 0.338   greenX: 0.311 greenY: 0.619
[     4.909] (II) VESA(0): blueX: 0.159 blueY: 0.059   whiteX: 0.313 whiteY: 0.329
[     4.909] (II) VESA(0): Supported established timings:
[     4.909] (II) VESA(0): 720x400@70Hz
[     4.909] (II) VESA(0): 640x480@60Hz
[     4.909] (II) VESA(0): 640x480@67Hz
[     4.909] (II) VESA(0): 640x480@75Hz
[     4.909] (II) VESA(0): 800x600@56Hz
[     4.909] (II) VESA(0): 800x600@60Hz
[     4.909] (II) VESA(0): 800x600@72Hz
[     4.909] (II) VESA(0): 800x600@75Hz
[     4.909] (II) VESA(0): 832x624@75Hz
[     4.909] (II) VESA(0): 1024x768@60Hz
[     4.909] (II) VESA(0): 1024x768@70Hz
[     4.909] (II) VESA(0): 1024x768@75Hz
[     4.909] (II) VESA(0): 1280x1024@75Hz
[     4.909] (II) VESA(0): Manufacturer's mask: 0
[     4.909] (II) VESA(0): Supported standard timings:
[     4.909] (II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     4.909] (II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     4.909] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     4.909] (II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     4.909] (II) VESA(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     4.909] (II) VESA(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     4.909] (II) VESA(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     4.909] (II) VESA(0): #7: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     4.909] (II) VESA(0): Supported detailed timing:
[     4.909] (II) VESA(0): clock: 148.5 MHz   Image Size:  521 x 293 mm
[     4.909] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     4.909] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     4.909] (II) VESA(0): Serial No: C7LMTF047478
[     4.909] (II) VESA(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[     4.909] (II) VESA(0): Monitor name: ASUS VS247
[     4.909] (II) VESA(0): EDID (in hex):
[     4.909] (II) VESA(0):     00ffffffffffff0004699a2476b90000
[     4.909] (II) VESA(0):     1c16010368341d782a2ac5a4564f9e28
[     4.909] (II) VESA(0):     0f5054b7ef00714f814081809500b300
[     4.909] (II) VESA(0):     d1c081c08100023a801871382d40582c
[     4.909] (II) VESA(0):     450009252100001e000000ff0043374c
[     4.909] (II) VESA(0):     4d54463034373437380a000000fd0032
[     4.909] (II) VESA(0):     4b185311000a202020202020000000fc
[     4.909] (II) VESA(0):     00415355532056533234370a202000eb
[     4.909] (II) VESA(0): EDID vendor "ACI", prod id 9370
[     4.909] (II) VESA(0): Using EDID range info for horizontal sync
[     4.909] (II) VESA(0): Using EDID range info for vertical refresh
[     4.909] (II) VESA(0): Printing DDC gathered Modelines:
[     4.909] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     4.909] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     4.909] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     4.909] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     4.909] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     4.909] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     4.909] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     4.909] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     4.909] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     4.909] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     4.909] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     4.909] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     4.909] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     4.909] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     4.909] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     4.909] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     4.909] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     4.909] (II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[     4.909] (II) VESA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     4.909] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     4.909] (II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     4.909] (II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[     4.909] (II) VESA(0): Searching for matching VESA mode(s):
[     4.911] Mode: 100 (640x400)
[     4.911]     ModeAttributes: 0x3bf
[     4.911]     WinAAttributes: 0x7
[     4.911]     WinBAttributes: 0x0
[     4.911]     WinGranularity: 64
[     4.911]     WinSize: 64
[     4.911]     WinASegment: 0xa000
[     4.911]     WinBSegment: 0x0
[     4.911]     WinFuncPtr: 0xc0007eac
[     4.911]     BytesPerScanline: 640
[     4.911]     XResolution: 640
[     4.911]     YResolution: 400
[     4.911]     XCharSize: 8
[     4.911]     YCharSize: 16
[     4.911]     NumberOfPlanes: 1
[     4.911]     BitsPerPixel: 8
[     4.911]     NumberOfBanks: 1
[     4.911]     MemoryModel: 4
[     4.911]     BankSize: 0
[     4.911]     NumberOfImages: 14
[     4.911]     RedMaskSize: 0
[     4.911]     RedFieldPosition: 0
[     4.911]     GreenMaskSize: 0
[     4.911]     GreenFieldPosition: 0
[     4.911]     BlueMaskSize: 0
[     4.911]     BlueFieldPosition: 0
[     4.911]     RsvdMaskSize: 0
[     4.911]     RsvdFieldPosition: 0
[     4.911]     DirectColorModeInfo: 0
[     4.911]     PhysBasePtr: 0xe9000000
[     4.911]     LinBytesPerScanLine: 640
[     4.911]     BnkNumberOfImagePages: 14
[     4.911]     LinNumberOfImagePages: 14
[     4.911]     LinRedMaskSize: 0
[     4.911]     LinRedFieldPosition: 0
[     4.911]     LinGreenMaskSize: 0
[     4.911]     LinGreenFieldPosition: 0
[     4.911]     LinBlueMaskSize: 0
[     4.911]     LinBlueFieldPosition: 0
[     4.911]     LinRsvdMaskSize: 0
[     4.911]     LinRsvdFieldPosition: 0
[     4.911]     MaxPixelClock: 229500000
[     4.912] Mode: 101 (640x480)
[     4.912]     ModeAttributes: 0x3bf
[     4.912]     WinAAttributes: 0x7
[     4.912]     WinBAttributes: 0x0
[     4.912]     WinGranularity: 64
[     4.912]     WinSize: 64
[     4.912]     WinASegment: 0xa000
[     4.912]     WinBSegment: 0x0
[     4.912]     WinFuncPtr: 0xc0007eac
[     4.912]     BytesPerScanline: 640
[     4.912]     XResolution: 640
[     4.912]     YResolution: 480
[     4.912]     XCharSize: 8
[     4.912]     YCharSize: 16
[     4.912]     NumberOfPlanes: 1
[     4.912]     BitsPerPixel: 8
[     4.912]     NumberOfBanks: 1
[     4.912]     MemoryModel: 4
[     4.912]     BankSize: 0
[     4.912]     NumberOfImages: 10
[     4.912]     RedMaskSize: 0
[     4.912]     RedFieldPosition: 0
[     4.912]     GreenMaskSize: 0
[     4.912]     GreenFieldPosition: 0
[     4.912]     BlueMaskSize: 0
[     4.912]     BlueFieldPosition: 0
[     4.912]     RsvdMaskSize: 0
[     4.912]     RsvdFieldPosition: 0
[     4.912]     DirectColorModeInfo: 0
[     4.912]     PhysBasePtr: 0xe9000000
[     4.912]     LinBytesPerScanLine: 640
[     4.912]     BnkNumberOfImagePages: 10
[     4.912]     LinNumberOfImagePages: 10
[     4.912]     LinRedMaskSize: 0
[     4.912]     LinRedFieldPosition: 0
[     4.912]     LinGreenMaskSize: 0
[     4.912]     LinGreenFieldPosition: 0
[     4.912]     LinBlueMaskSize: 0
[     4.912]     LinBlueFieldPosition: 0
[     4.912]     LinRsvdMaskSize: 0
[     4.912]     LinRsvdFieldPosition: 0
[     4.912]     MaxPixelClock: 229500000
[     4.913] Mode: 102 (800x600)
[     4.913]     ModeAttributes: 0x33f
[     4.913]     WinAAttributes: 0x7
[     4.913]     WinBAttributes: 0x0
[     4.913]     WinGranularity: 64
[     4.913]     WinSize: 64
[     4.913]     WinASegment: 0xa000
[     4.913]     WinBSegment: 0x0
[     4.913]     WinFuncPtr: 0xc0007eac
[     4.913]     BytesPerScanline: 100
[     4.913]     XResolution: 800
[     4.913]     YResolution: 600
[     4.913]     XCharSize: 8
[     4.913]     YCharSize: 16
[     4.913]     NumberOfPlanes: 4
[     4.913]     BitsPerPixel: 4
[     4.913]     NumberOfBanks: 1
[     4.913]     MemoryModel: 3
[     4.913]     BankSize: 0
[     4.913]     NumberOfImages: 2
[     4.913]     RedMaskSize: 0
[     4.913]     RedFieldPosition: 0
[     4.913]     GreenMaskSize: 0
[     4.913]     GreenFieldPosition: 0
[     4.913]     BlueMaskSize: 0
[     4.913]     BlueFieldPosition: 0
[     4.913]     RsvdMaskSize: 0
[     4.913]     RsvdFieldPosition: 0
[     4.913]     DirectColorModeInfo: 0
[     4.913]     PhysBasePtr: 0x0
[     4.913]     LinBytesPerScanLine: 100
[     4.913]     BnkNumberOfImagePages: 2
[     4.913]     LinNumberOfImagePages: 2
[     4.913]     LinRedMaskSize: 0
[     4.913]     LinRedFieldPosition: 0
[     4.913]     LinGreenMaskSize: 0
[     4.913]     LinGreenFieldPosition: 0
[     4.913]     LinBlueMaskSize: 0
[     4.913]     LinBlueFieldPosition: 0
[     4.913]     LinRsvdMaskSize: 0
[     4.913]     LinRsvdFieldPosition: 0
[     4.913]     MaxPixelClock: 108500000
[     4.914] Mode: 103 (800x600)
[     4.914]     ModeAttributes: 0x3bf
[     4.914]     WinAAttributes: 0x7
[     4.914]     WinBAttributes: 0x0
[     4.914]     WinGranularity: 64
[     4.914]     WinSize: 64
[     4.914]     WinASegment: 0xa000
[     4.914]     WinBSegment: 0x0
[     4.914]     WinFuncPtr: 0xc0007eac
[     4.914]     BytesPerScanline: 800
[     4.914]     XResolution: 800
[     4.914]     YResolution: 600
[     4.914]     XCharSize: 8
[     4.914]     YCharSize: 16
[     4.914]     NumberOfPlanes: 1
[     4.914]     BitsPerPixel: 8
[     4.914]     NumberOfBanks: 1
[     4.914]     MemoryModel: 4
[     4.914]     BankSize: 0
[     4.914]     NumberOfImages: 6
[     4.914]     RedMaskSize: 0
[     4.914]     RedFieldPosition: 0
[     4.914]     GreenMaskSize: 0
[     4.914]     GreenFieldPosition: 0
[     4.914]     BlueMaskSize: 0
[     4.914]     BlueFieldPosition: 0
[     4.914]     RsvdMaskSize: 0
[     4.914]     RsvdFieldPosition: 0
[     4.915]     DirectColorModeInfo: 0
[     4.915]     PhysBasePtr: 0xe9000000
[     4.915]     LinBytesPerScanLine: 800
[     4.915]     BnkNumberOfImagePages: 6
[     4.915]     LinNumberOfImagePages: 6
[     4.915]     LinRedMaskSize: 0
[     4.915]     LinRedFieldPosition: 0
[     4.915]     LinGreenMaskSize: 0
[     4.915]     LinGreenFieldPosition: 0
[     4.915]     LinBlueMaskSize: 0
[     4.915]     LinBlueFieldPosition: 0
[     4.915]     LinRsvdMaskSize: 0
[     4.915]     LinRsvdFieldPosition: 0
[     4.915]     MaxPixelClock: 229500000
[     4.916] Mode: 104 (1024x768)
[     4.916]     ModeAttributes: 0x33f
[     4.916]     WinAAttributes: 0x7
[     4.916]     WinBAttributes: 0x0
[     4.916]     WinGranularity: 64
[     4.916]     WinSize: 64
[     4.916]     WinASegment: 0xa000
[     4.916]     WinBSegment: 0x0
[     4.916]     WinFuncPtr: 0xc0007eac
[     4.916]     BytesPerScanline: 128
[     4.916]     XResolution: 1024
[     4.916]     YResolution: 768
[     4.916]     XCharSize: 8
[     4.916]     YCharSize: 16
[     4.916]     NumberOfPlanes: 4
[     4.916]     BitsPerPixel: 4
[     4.916]     NumberOfBanks: 1
[     4.916]     MemoryModel: 3
[     4.916]     BankSize: 0
[     4.916]     NumberOfImages: 1
[     4.916]     RedMaskSize: 0
[     4.916]     RedFieldPosition: 0
[     4.916]     GreenMaskSize: 0
[     4.916]     GreenFieldPosition: 0
[     4.916]     BlueMaskSize: 0
[     4.916]     BlueFieldPosition: 0
[     4.916]     RsvdMaskSize: 0
[     4.916]     RsvdFieldPosition: 0
[     4.916]     DirectColorModeInfo: 0
[     4.916]     PhysBasePtr: 0x0
[     4.916]     LinBytesPerScanLine: 128
[     4.916]     BnkNumberOfImagePages: 1
[     4.916]     LinNumberOfImagePages: 1
[     4.916]     LinRedMaskSize: 0
[     4.916]     LinRedFieldPosition: 0
[     4.916]     LinGreenMaskSize: 0
[     4.916]     LinGreenFieldPosition: 0
[     4.916]     LinBlueMaskSize: 0
[     4.916]     LinBlueFieldPosition: 0
[     4.916]     LinRsvdMaskSize: 0
[     4.916]     LinRsvdFieldPosition: 0
[     4.916]     MaxPixelClock: 108500000
[     4.917] Mode: 105 (1024x768)
[     4.917]     ModeAttributes: 0x3bf
[     4.917]     WinAAttributes: 0x7
[     4.917]     WinBAttributes: 0x0
[     4.917]     WinGranularity: 64
[     4.917]     WinSize: 64
[     4.917]     WinASegment: 0xa000
[     4.917]     WinBSegment: 0x0
[     4.917]     WinFuncPtr: 0xc0007eac
[     4.917]     BytesPerScanline: 1024
[     4.917]     XResolution: 1024
[     4.917]     YResolution: 768
[     4.917]     XCharSize: 8
[     4.917]     YCharSize: 16
[     4.917]     NumberOfPlanes: 1
[     4.917]     BitsPerPixel: 8
[     4.917]     NumberOfBanks: 1
[     4.917]     MemoryModel: 4
[     4.917]     BankSize: 0
[     4.917]     NumberOfImages: 3
[     4.917]     RedMaskSize: 0
[     4.917]     RedFieldPosition: 0
[     4.917]     GreenMaskSize: 0
[     4.917]     GreenFieldPosition: 0
[     4.917]     BlueMaskSize: 0
[     4.917]     BlueFieldPosition: 0
[     4.917]     RsvdMaskSize: 0
[     4.917]     RsvdFieldPosition: 0
[     4.917]     DirectColorModeInfo: 0
[     4.917]     PhysBasePtr: 0xe9000000
[     4.917]     LinBytesPerScanLine: 1024
[     4.917]     BnkNumberOfImagePages: 3
[     4.917]     LinNumberOfImagePages: 3
[     4.917]     LinRedMaskSize: 0
[     4.917]     LinRedFieldPosition: 0
[     4.917]     LinGreenMaskSize: 0
[     4.917]     LinGreenFieldPosition: 0
[     4.917]     LinBlueMaskSize: 0
[     4.917]     LinBlueFieldPosition: 0
[     4.917]     LinRsvdMaskSize: 0
[     4.917]     LinRsvdFieldPosition: 0
[     4.917]     MaxPixelClock: 229500000
[     4.918] Mode: 106 (1280x1024)
[     4.918]     ModeAttributes: 0x33f
[     4.918]     WinAAttributes: 0x7
[     4.918]     WinBAttributes: 0x0
[     4.918]     WinGranularity: 64
[     4.918]     WinSize: 64
[     4.918]     WinASegment: 0xa000
[     4.918]     WinBSegment: 0x0
[     4.918]     WinFuncPtr: 0xc0007eac
[     4.918]     BytesPerScanline: 160
[     4.918]     XResolution: 1280
[     4.918]     YResolution: 1024
[     4.918]     XCharSize: 8
[     4.918]     YCharSize: 16
[     4.918]     NumberOfPlanes: 4
[     4.918]     BitsPerPixel: 4
[     4.918]     NumberOfBanks: 1
[     4.918]     MemoryModel: 3
[     4.918]     BankSize: 0
[     4.918]     NumberOfImages: 1
[     4.918]     RedMaskSize: 0
[     4.918]     RedFieldPosition: 0
[     4.918]     GreenMaskSize: 0
[     4.918]     GreenFieldPosition: 0
[     4.918]     BlueMaskSize: 0
[     4.918]     BlueFieldPosition: 0
[     4.918]     RsvdMaskSize: 0
[     4.918]     RsvdFieldPosition: 0
[     4.918]     DirectColorModeInfo: 0
[     4.918]     PhysBasePtr: 0x0
[     4.918]     LinBytesPerScanLine: 160
[     4.918]     BnkNumberOfImagePages: 1
[     4.918]     LinNumberOfImagePages: 1
[     4.918]     LinRedMaskSize: 0
[     4.918]     LinRedFieldPosition: 0
[     4.918]     LinGreenMaskSize: 0
[     4.918]     LinGreenFieldPosition: 0
[     4.918]     LinBlueMaskSize: 0
[     4.918]     LinBlueFieldPosition: 0
[     4.918]     LinRsvdMaskSize: 0
[     4.918]     LinRsvdFieldPosition: 0
[     4.918]     MaxPixelClock: 108500000
[     4.919] Mode: 107 (1280x1024)
[     4.919]     ModeAttributes: 0x3bf
[     4.919]     WinAAttributes: 0x7
[     4.919]     WinBAttributes: 0x0
[     4.919]     WinGranularity: 64
[     4.919]     WinSize: 64
[     4.919]     WinASegment: 0xa000
[     4.919]     WinBSegment: 0x0
[     4.919]     WinFuncPtr: 0xc0007eac
[     4.919]     BytesPerScanline: 1280
[     4.919]     XResolution: 1280
[     4.919]     YResolution: 1024
[     4.919]     XCharSize: 8
[     4.919]     YCharSize: 16
[     4.919]     NumberOfPlanes: 1
[     4.919]     BitsPerPixel: 8
[     4.919]     NumberOfBanks: 1
[     4.919]     MemoryModel: 4
[     4.919]     BankSize: 0
[     4.919]     NumberOfImages: 1
[     4.919]     RedMaskSize: 0
[     4.919]     RedFieldPosition: 0
[     4.919]     GreenMaskSize: 0
[     4.919]     GreenFieldPosition: 0
[     4.919]     BlueMaskSize: 0
[     4.920]     BlueFieldPosition: 0
[     4.920]     RsvdMaskSize: 0
[     4.920]     RsvdFieldPosition: 0
[     4.920]     DirectColorModeInfo: 0
[     4.920]     PhysBasePtr: 0xe9000000
[     4.920]     LinBytesPerScanLine: 1280
[     4.920]     BnkNumberOfImagePages: 1
[     4.920]     LinNumberOfImagePages: 1
[     4.920]     LinRedMaskSize: 0
[     4.920]     LinRedFieldPosition: 0
[     4.920]     LinGreenMaskSize: 0
[     4.920]     LinGreenFieldPosition: 0
[     4.920]     LinBlueMaskSize: 0
[     4.920]     LinBlueFieldPosition: 0
[     4.920]     LinRsvdMaskSize: 0
[     4.920]     LinRsvdFieldPosition: 0
[     4.920]     MaxPixelClock: 229500000
[     4.921] Mode: 10e (320x200)
[     4.921]     ModeAttributes: 0x3bf
[     4.921]     WinAAttributes: 0x7
[     4.921]     WinBAttributes: 0x0
[     4.921]     WinGranularity: 64
[     4.921]     WinSize: 64
[     4.921]     WinASegment: 0xa000
[     4.921]     WinBSegment: 0x0
[     4.921]     WinFuncPtr: 0xc0007eac
[     4.921]     BytesPerScanline: 640
[     4.921]     XResolution: 320
[     4.921]     YResolution: 200
[     4.921]     XCharSize: 8
[     4.921]     YCharSize: 8
[     4.921]     NumberOfPlanes: 1
[     4.921]     BitsPerPixel: 16
[     4.921]     NumberOfBanks: 1
[     4.921]     MemoryModel: 6
[     4.921]     BankSize: 0
[     4.921]     NumberOfImages: 30
[     4.921]     RedMaskSize: 5
[     4.921]     RedFieldPosition: 11
[     4.921]     GreenMaskSize: 6
[     4.921]     GreenFieldPosition: 5
[     4.921]     BlueMaskSize: 5
[     4.921]     BlueFieldPosition: 0
[     4.921]     RsvdMaskSize: 0
[     4.921]     RsvdFieldPosition: 0
[     4.921]     DirectColorModeInfo: 0
[     4.921]     PhysBasePtr: 0xe9000000
[     4.921]     LinBytesPerScanLine: 640
[     4.921]     BnkNumberOfImagePages: 30
[     4.921]     LinNumberOfImagePages: 30
[     4.921]     LinRedMaskSize: 5
[     4.921]     LinRedFieldPosition: 11
[     4.921]     LinGreenMaskSize: 6
[     4.921]     LinGreenFieldPosition: 5
[     4.921]     LinBlueMaskSize: 5
[     4.921]     LinBlueFieldPosition: 0
[     4.921]     LinRsvdMaskSize: 0
[     4.921]     LinRsvdFieldPosition: 0
[     4.921]     MaxPixelClock: 229500000
[     4.922] *Mode: 10f (320x200)
[     4.922]     ModeAttributes: 0x3bf
[     4.922]     WinAAttributes: 0x7
[     4.922]     WinBAttributes: 0x0
[     4.922]     WinGranularity: 64
[     4.922]     WinSize: 64
[     4.922]     WinASegment: 0xa000
[     4.922]     WinBSegment: 0x0
[     4.922]     WinFuncPtr: 0xc0007eac
[     4.922]     BytesPerScanline: 1280
[     4.922]     XResolution: 320
[     4.922]     YResolution: 200
[     4.922]     XCharSize: 8
[     4.922]     YCharSize: 8
[     4.922]     NumberOfPlanes: 1
[     4.922]     BitsPerPixel: 32
[     4.922]     NumberOfBanks: 1
[     4.922]     MemoryModel: 6
[     4.922]     BankSize: 0
[     4.922]     NumberOfImages: 14
[     4.922]     RedMaskSize: 8
[     4.922]     RedFieldPosition: 16
[     4.922]     GreenMaskSize: 8
[     4.922]     GreenFieldPosition: 8
[     4.922]     BlueMaskSize: 8
[     4.922]     BlueFieldPosition: 0
[     4.922]     RsvdMaskSize: 8
[     4.922]     RsvdFieldPosition: 24
[     4.922]     DirectColorModeInfo: 0
[     4.922]     PhysBasePtr: 0xe9000000
[     4.922]     LinBytesPerScanLine: 1280
[     4.922]     BnkNumberOfImagePages: 14
[     4.922]     LinNumberOfImagePages: 14
[     4.922]     LinRedMaskSize: 8
[     4.922]     LinRedFieldPosition: 16
[     4.922]     LinGreenMaskSize: 8
[     4.922]     LinGreenFieldPosition: 8
[     4.922]     LinBlueMaskSize: 8
[     4.922]     LinBlueFieldPosition: 0
[     4.922]     LinRsvdMaskSize: 8
[     4.922]     LinRsvdFieldPosition: 24
[     4.922]     MaxPixelClock: 229500000
[     4.923] Mode: 111 (640x480)
[     4.923]     ModeAttributes: 0x3bf
[     4.923]     WinAAttributes: 0x7
[     4.923]     WinBAttributes: 0x0
[     4.923]     WinGranularity: 64
[     4.923]     WinSize: 64
[     4.923]     WinASegment: 0xa000
[     4.923]     WinBSegment: 0x0
[     4.923]     WinFuncPtr: 0xc0007eac
[     4.923]     BytesPerScanline: 1280
[     4.923]     XResolution: 640
[     4.923]     YResolution: 480
[     4.923]     XCharSize: 8
[     4.923]     YCharSize: 16
[     4.923]     NumberOfPlanes: 1
[     4.923]     BitsPerPixel: 16
[     4.923]     NumberOfBanks: 1
[     4.923]     MemoryModel: 6
[     4.923]     BankSize: 0
[     4.923]     NumberOfImages: 4
[     4.923]     RedMaskSize: 5
[     4.923]     RedFieldPosition: 11
[     4.923]     GreenMaskSize: 6
[     4.923]     GreenFieldPosition: 5
[     4.923]     BlueMaskSize: 5
[     4.923]     BlueFieldPosition: 0
[     4.923]     RsvdMaskSize: 0
[     4.923]     RsvdFieldPosition: 0
[     4.923]     DirectColorModeInfo: 0
[     4.923]     PhysBasePtr: 0xe9000000
[     4.923]     LinBytesPerScanLine: 1280
[     4.923]     BnkNumberOfImagePages: 4
[     4.923]     LinNumberOfImagePages: 4
[     4.923]     LinRedMaskSize: 5
[     4.923]     LinRedFieldPosition: 11
[     4.923]     LinGreenMaskSize: 6
[     4.923]     LinGreenFieldPosition: 5
[     4.923]     LinBlueMaskSize: 5
[     4.923]     LinBlueFieldPosition: 0
[     4.923]     LinRsvdMaskSize: 0
[     4.923]     LinRsvdFieldPosition: 0
[     4.923]     MaxPixelClock: 229500000
[     4.924] *Mode: 112 (640x480)
[     4.924]     ModeAttributes: 0x3bf
[     4.924]     WinAAttributes: 0x7
[     4.924]     WinBAttributes: 0x0
[     4.924]     WinGranularity: 64
[     4.924]     WinSize: 64
[     4.924]     WinASegment: 0xa000
[     4.924]     WinBSegment: 0x0
[     4.924]     WinFuncPtr: 0xc0007eac
[     4.924]     BytesPerScanline: 2560
[     4.924]     XResolution: 640
[     4.924]     YResolution: 480
[     4.924]     XCharSize: 8
[     4.924]     YCharSize: 16
[     4.924]     NumberOfPlanes: 1
[     4.924]     BitsPerPixel: 32
[     4.924]     NumberOfBanks: 1
[     4.924]     MemoryModel: 6
[     4.924]     BankSize: 0
[     4.924]     NumberOfImages: 1
[     4.924]     RedMaskSize: 8
[     4.924]     RedFieldPosition: 16
[     4.924]     GreenMaskSize: 8
[     4.924]     GreenFieldPosition: 8
[     4.924]     BlueMaskSize: 8
[     4.924]     BlueFieldPosition: 0
[     4.924]     RsvdMaskSize: 8
[     4.924]     RsvdFieldPosition: 24
[     4.924]     DirectColorModeInfo: 0
[     4.924]     PhysBasePtr: 0xe9000000
[     4.924]     LinBytesPerScanLine: 2560
[     4.924]     BnkNumberOfImagePages: 1
[     4.924]     LinNumberOfImagePages: 1
[     4.924]     LinRedMaskSize: 8
[     4.924]     LinRedFieldPosition: 16
[     4.924]     LinGreenMaskSize: 8
[     4.924]     LinGreenFieldPosition: 8
[     4.924]     LinBlueMaskSize: 8
[     4.924]     LinBlueFieldPosition: 0
[     4.924]     LinRsvdMaskSize: 8
[     4.925]     LinRsvdFieldPosition: 24
[     4.925]     MaxPixelClock: 229500000
[     4.926] Mode: 114 (800x600)
[     4.926]     ModeAttributes: 0x3bf
[     4.926]     WinAAttributes: 0x7
[     4.926]     WinBAttributes: 0x0
[     4.926]     WinGranularity: 64
[     4.926]     WinSize: 64
[     4.926]     WinASegment: 0xa000
[     4.926]     WinBSegment: 0x0
[     4.926]     WinFuncPtr: 0xc0007eac
[     4.926]     BytesPerScanline: 1600
[     4.926]     XResolution: 800
[     4.926]     YResolution: 600
[     4.926]     XCharSize: 8
[     4.926]     YCharSize: 16
[     4.926]     NumberOfPlanes: 1
[     4.926]     BitsPerPixel: 16
[     4.926]     NumberOfBanks: 1
[     4.926]     MemoryModel: 6
[     4.926]     BankSize: 0
[     4.926]     NumberOfImages: 2
[     4.926]     RedMaskSize: 5
[     4.926]     RedFieldPosition: 11
[     4.926]     GreenMaskSize: 6
[     4.926]     GreenFieldPosition: 5
[     4.926]     BlueMaskSize: 5
[     4.926]     BlueFieldPosition: 0
[     4.926]     RsvdMaskSize: 0
[     4.926]     RsvdFieldPosition: 0
[     4.926]     DirectColorModeInfo: 0
[     4.926]     PhysBasePtr: 0xe9000000
[     4.926]     LinBytesPerScanLine: 1600
[     4.926]     BnkNumberOfImagePages: 2
[     4.926]     LinNumberOfImagePages: 2
[     4.926]     LinRedMaskSize: 5
[     4.926]     LinRedFieldPosition: 11
[     4.926]     LinGreenMaskSize: 6
[     4.926]     LinGreenFieldPosition: 5
[     4.926]     LinBlueMaskSize: 5
[     4.926]     LinBlueFieldPosition: 0
[     4.926]     LinRsvdMaskSize: 0
[     4.926]     LinRsvdFieldPosition: 0
[     4.926]     MaxPixelClock: 229500000
[     4.927] *Mode: 115 (800x600)
[     4.927]     ModeAttributes: 0x3bf
[     4.927]     WinAAttributes: 0x7
[     4.927]     WinBAttributes: 0x0
[     4.927]     WinGranularity: 64
[     4.927]     WinSize: 64
[     4.927]     WinASegment: 0xa000
[     4.927]     WinBSegment: 0x0
[     4.927]     WinFuncPtr: 0xc0007eac
[     4.927]     BytesPerScanline: 3200
[     4.927]     XResolution: 800
[     4.927]     YResolution: 600
[     4.927]     XCharSize: 8
[     4.927]     YCharSize: 16
[     4.927]     NumberOfPlanes: 1
[     4.927]     BitsPerPixel: 32
[     4.927]     NumberOfBanks: 1
[     4.927]     MemoryModel: 6
[     4.927]     BankSize: 0
[     4.927]     NumberOfImages: 1
[     4.927]     RedMaskSize: 8
[     4.927]     RedFieldPosition: 16
[     4.927]     GreenMaskSize: 8
[     4.927]     GreenFieldPosition: 8
[     4.927]     BlueMaskSize: 8
[     4.927]     BlueFieldPosition: 0
[     4.927]     RsvdMaskSize: 8
[     4.927]     RsvdFieldPosition: 24
[     4.927]     DirectColorModeInfo: 0
[     4.927]     PhysBasePtr: 0xe9000000
[     4.927]     LinBytesPerScanLine: 3200
[     4.927]     BnkNumberOfImagePages: 1
[     4.927]     LinNumberOfImagePages: 1
[     4.927]     LinRedMaskSize: 8
[     4.927]     LinRedFieldPosition: 16
[     4.927]     LinGreenMaskSize: 8
[     4.927]     LinGreenFieldPosition: 8
[     4.927]     LinBlueMaskSize: 8
[     4.927]     LinBlueFieldPosition: 0
[     4.927]     LinRsvdMaskSize: 8
[     4.927]     LinRsvdFieldPosition: 24
[     4.927]     MaxPixelClock: 229500000
[     4.928] Mode: 117 (1024x768)
[     4.928]     ModeAttributes: 0x3bf
[     4.928]     WinAAttributes: 0x7
[     4.928]     WinBAttributes: 0x0
[     4.928]     WinGranularity: 64
[     4.928]     WinSize: 64
[     4.928]     WinASegment: 0xa000
[     4.928]     WinBSegment: 0x0
[     4.928]     WinFuncPtr: 0xc0007eac
[     4.928]     BytesPerScanline: 2048
[     4.928]     XResolution: 1024
[     4.928]     YResolution: 768
[     4.928]     XCharSize: 8
[     4.928]     YCharSize: 16
[     4.928]     NumberOfPlanes: 1
[     4.928]     BitsPerPixel: 16
[     4.928]     NumberOfBanks: 1
[     4.928]     MemoryModel: 6
[     4.928]     BankSize: 0
[     4.928]     NumberOfImages: 1
[     4.928]     RedMaskSize: 5
[     4.928]     RedFieldPosition: 11
[     4.928]     GreenMaskSize: 6
[     4.928]     GreenFieldPosition: 5
[     4.928]     BlueMaskSize: 5
[     4.928]     BlueFieldPosition: 0
[     4.928]     RsvdMaskSize: 0
[     4.928]     RsvdFieldPosition: 0
[     4.928]     DirectColorModeInfo: 0
[     4.928]     PhysBasePtr: 0xe9000000
[     4.928]     LinBytesPerScanLine: 2048
[     4.928]     BnkNumberOfImagePages: 1
[     4.928]     LinNumberOfImagePages: 1
[     4.928]     LinRedMaskSize: 5
[     4.928]     LinRedFieldPosition: 11
[     4.928]     LinGreenMaskSize: 6
[     4.928]     LinGreenFieldPosition: 5
[     4.928]     LinBlueMaskSize: 5
[     4.928]     LinBlueFieldPosition: 0
[     4.928]     LinRsvdMaskSize: 0
[     4.928]     LinRsvdFieldPosition: 0
[     4.928]     MaxPixelClock: 229500000
[     4.929] *Mode: 118 (1024x768)
[     4.929]     ModeAttributes: 0x3bf
[     4.929]     WinAAttributes: 0x7
[     4.929]     WinBAttributes: 0x0
[     4.929]     WinGranularity: 64
[     4.929]     WinSize: 64
[     4.929]     WinASegment: 0xa000
[     4.929]     WinBSegment: 0x0
[     4.929]     WinFuncPtr: 0xc0007eac
[     4.929]     BytesPerScanline: 4096
[     4.929]     XResolution: 1024
[     4.929]     YResolution: 768
[     4.929]     XCharSize: 8
[     4.929]     YCharSize: 16
[     4.929]     NumberOfPlanes: 1
[     4.929]     BitsPerPixel: 32
[     4.929]     NumberOfBanks: 1
[     4.929]     MemoryModel: 6
[     4.929]     BankSize: 0
[     4.929]     NumberOfImages: 1
[     4.929]     RedMaskSize: 8
[     4.929]     RedFieldPosition: 16
[     4.929]     GreenMaskSize: 8
[     4.929]     GreenFieldPosition: 8
[     4.929]     BlueMaskSize: 8
[     4.929]     BlueFieldPosition: 0
[     4.929]     RsvdMaskSize: 8
[     4.929]     RsvdFieldPosition: 24
[     4.929]     DirectColorModeInfo: 0
[     4.929]     PhysBasePtr: 0xe9000000
[     4.929]     LinBytesPerScanLine: 4096
[     4.929]     BnkNumberOfImagePages: 1
[     4.929]     LinNumberOfImagePages: 1
[     4.929]     LinRedMaskSize: 8
[     4.930]     LinRedFieldPosition: 16
[     4.930]     LinGreenMaskSize: 8
[     4.930]     LinGreenFieldPosition: 8
[     4.930]     LinBlueMaskSize: 8
[     4.930]     LinBlueFieldPosition: 0
[     4.930]     LinRsvdMaskSize: 8
[     4.930]     LinRsvdFieldPosition: 24
[     4.930]     MaxPixelClock: 229500000
[     4.931] Mode: 11a (1280x1024)
[     4.931]     ModeAttributes: 0x3bf
[     4.931]     WinAAttributes: 0x7
[     4.931]     WinBAttributes: 0x0
[     4.931]     WinGranularity: 64
[     4.931]     WinSize: 64
[     4.931]     WinASegment: 0xa000
[     4.931]     WinBSegment: 0x0
[     4.931]     WinFuncPtr: 0xc0007eac
[     4.931]     BytesPerScanline: 2560
[     4.931]     XResolution: 1280
[     4.931]     YResolution: 1024
[     4.931]     XCharSize: 8
[     4.931]     YCharSize: 16
[     4.931]     NumberOfPlanes: 1
[     4.931]     BitsPerPixel: 16
[     4.931]     NumberOfBanks: 1
[     4.931]     MemoryModel: 6
[     4.931]     BankSize: 0
[     4.931]     NumberOfImages: 1
[     4.931]     RedMaskSize: 5
[     4.931]     RedFieldPosition: 11
[     4.931]     GreenMaskSize: 6
[     4.931]     GreenFieldPosition: 5
[     4.931]     BlueMaskSize: 5
[     4.931]     BlueFieldPosition: 0
[     4.931]     RsvdMaskSize: 0
[     4.931]     RsvdFieldPosition: 0
[     4.931]     DirectColorModeInfo: 0
[     4.931]     PhysBasePtr: 0xe9000000
[     4.931]     LinBytesPerScanLine: 2560
[     4.931]     BnkNumberOfImagePages: 1
[     4.931]     LinNumberOfImagePages: 1
[     4.931]     LinRedMaskSize: 5
[     4.931]     LinRedFieldPosition: 11
[     4.931]     LinGreenMaskSize: 6
[     4.931]     LinGreenFieldPosition: 5
[     4.931]     LinBlueMaskSize: 5
[     4.931]     LinBlueFieldPosition: 0
[     4.931]     LinRsvdMaskSize: 0
[     4.931]     LinRsvdFieldPosition: 0
[     4.931]     MaxPixelClock: 229500000
[     4.932] *Mode: 11b (1280x1024)
[     4.932]     ModeAttributes: 0x3bf
[     4.932]     WinAAttributes: 0x7
[     4.932]     WinBAttributes: 0x0
[     4.932]     WinGranularity: 64
[     4.932]     WinSize: 64
[     4.932]     WinASegment: 0xa000
[     4.932]     WinBSegment: 0x0
[     4.932]     WinFuncPtr: 0xc0007eac
[     4.932]     BytesPerScanline: 5120
[     4.932]     XResolution: 1280
[     4.932]     YResolution: 1024
[     4.932]     XCharSize: 8
[     4.932]     YCharSize: 16
[     4.932]     NumberOfPlanes: 1
[     4.932]     BitsPerPixel: 32
[     4.932]     NumberOfBanks: 1
[     4.932]     MemoryModel: 6
[     4.932]     BankSize: 0
[     4.932]     NumberOfImages: 1
[     4.932]     RedMaskSize: 8
[     4.932]     RedFieldPosition: 16
[     4.932]     GreenMaskSize: 8
[     4.932]     GreenFieldPosition: 8
[     4.932]     BlueMaskSize: 8
[     4.932]     BlueFieldPosition: 0
[     4.932]     RsvdMaskSize: 8
[     4.932]     RsvdFieldPosition: 24
[     4.932]     DirectColorModeInfo: 0
[     4.932]     PhysBasePtr: 0xe9000000
[     4.932]     LinBytesPerScanLine: 5120
[     4.932]     BnkNumberOfImagePages: 1
[     4.932]     LinNumberOfImagePages: 1
[     4.932]     LinRedMaskSize: 8
[     4.932]     LinRedFieldPosition: 16
[     4.932]     LinGreenMaskSize: 8
[     4.932]     LinGreenFieldPosition: 8
[     4.932]     LinBlueMaskSize: 8
[     4.932]     LinBlueFieldPosition: 0
[     4.932]     LinRsvdMaskSize: 8
[     4.932]     LinRsvdFieldPosition: 24
[     4.932]     MaxPixelClock: 229500000
[     4.933] Mode: 130 (320x200)
[     4.933]     ModeAttributes: 0x3bf
[     4.933]     WinAAttributes: 0x7
[     4.933]     WinBAttributes: 0x0
[     4.933]     WinGranularity: 64
[     4.933]     WinSize: 64
[     4.933]     WinASegment: 0xa000
[     4.933]     WinBSegment: 0x0
[     4.933]     WinFuncPtr: 0xc0007eac
[     4.933]     BytesPerScanline: 320
[     4.933]     XResolution: 320
[     4.933]     YResolution: 200
[     4.933]     XCharSize: 8
[     4.933]     YCharSize: 8
[     4.933]     NumberOfPlanes: 1
[     4.933]     BitsPerPixel: 8
[     4.933]     NumberOfBanks: 1
[     4.933]     MemoryModel: 4
[     4.933]     BankSize: 0
[     4.933]     NumberOfImages: 62
[     4.933]     RedMaskSize: 0
[     4.933]     RedFieldPosition: 0
[     4.933]     GreenMaskSize: 0
[     4.933]     GreenFieldPosition: 0
[     4.933]     BlueMaskSize: 0
[     4.933]     BlueFieldPosition: 0
[     4.933]     RsvdMaskSize: 0
[     4.933]     RsvdFieldPosition: 0
[     4.933]     DirectColorModeInfo: 0
[     4.933]     PhysBasePtr: 0xe9000000
[     4.933]     LinBytesPerScanLine: 320
[     4.933]     BnkNumberOfImagePages: 62
[     4.933]     LinNumberOfImagePages: 62
[     4.933]     LinRedMaskSize: 0
[     4.933]     LinRedFieldPosition: 0
[     4.933]     LinGreenMaskSize: 0
[     4.933]     LinGreenFieldPosition: 0
[     4.933]     LinBlueMaskSize: 0
[     4.933]     LinBlueFieldPosition: 0
[     4.933]     LinRsvdMaskSize: 0
[     4.933]     LinRsvdFieldPosition: 0
[     4.933]     MaxPixelClock: 229500000
[     4.934] Mode: 131 (320x400)
[     4.934]     ModeAttributes: 0x3bf
[     4.934]     WinAAttributes: 0x7
[     4.934]     WinBAttributes: 0x0
[     4.934]     WinGranularity: 64
[     4.934]     WinSize: 64
[     4.934]     WinASegment: 0xa000
[     4.934]     WinBSegment: 0x0
[     4.934]     WinFuncPtr: 0xc0007eac
[     4.934]     BytesPerScanline: 320
[     4.934]     XResolution: 320
[     4.934]     YResolution: 400
[     4.934]     XCharSize: 8
[     4.934]     YCharSize: 16
[     4.934]     NumberOfPlanes: 1
[     4.934]     BitsPerPixel: 8
[     4.934]     NumberOfBanks: 1
[     4.934]     MemoryModel: 4
[     4.934]     BankSize: 0
[     4.934]     NumberOfImages: 30
[     4.934]     RedMaskSize: 0
[     4.934]     RedFieldPosition: 0
[     4.934]     GreenMaskSize: 0
[     4.934]     GreenFieldPosition: 0
[     4.934]     BlueMaskSize: 0
[     4.934]     BlueFieldPosition: 0
[     4.934]     RsvdMaskSize: 0
[     4.934]     RsvdFieldPosition: 0
[     4.934]     DirectColorModeInfo: 0
[     4.934]     PhysBasePtr: 0xe9000000
[     4.934]     LinBytesPerScanLine: 320
[     4.934]     BnkNumberOfImagePages: 30
[     4.934]     LinNumberOfImagePages: 30
[     4.935]     LinRedMaskSize: 0
[     4.935]     LinRedFieldPosition: 0
[     4.935]     LinGreenMaskSize: 0
[     4.935]     LinGreenFieldPosition: 0
[     4.935]     LinBlueMaskSize: 0
[     4.935]     LinBlueFieldPosition: 0
[     4.935]     LinRsvdMaskSize: 0
[     4.935]     LinRsvdFieldPosition: 0
[     4.935]     MaxPixelClock: 229500000
[     4.936] Mode: 132 (320x400)
[     4.936]     ModeAttributes: 0x3bf
[     4.936]     WinAAttributes: 0x7
[     4.936]     WinBAttributes: 0x0
[     4.936]     WinGranularity: 64
[     4.936]     WinSize: 64
[     4.936]     WinASegment: 0xa000
[     4.936]     WinBSegment: 0x0
[     4.936]     WinFuncPtr: 0xc0007eac
[     4.936]     BytesPerScanline: 640
[     4.936]     XResolution: 320
[     4.936]     YResolution: 400
[     4.936]     XCharSize: 8
[     4.936]     YCharSize: 16
[     4.936]     NumberOfPlanes: 1
[     4.936]     BitsPerPixel: 16
[     4.936]     NumberOfBanks: 1
[     4.936]     MemoryModel: 6
[     4.936]     BankSize: 0
[     4.936]     NumberOfImages: 14
[     4.936]     RedMaskSize: 5
[     4.936]     RedFieldPosition: 11
[     4.936]     GreenMaskSize: 6
[     4.936]     GreenFieldPosition: 5
[     4.936]     BlueMaskSize: 5
[     4.936]     BlueFieldPosition: 0
[     4.936]     RsvdMaskSize: 0
[     4.936]     RsvdFieldPosition: 0
[     4.936]     DirectColorModeInfo: 0
[     4.936]     PhysBasePtr: 0xe9000000
[     4.936]     LinBytesPerScanLine: 640
[     4.936]     BnkNumberOfImagePages: 14
[     4.936]     LinNumberOfImagePages: 14
[     4.936]     LinRedMaskSize: 5
[     4.936]     LinRedFieldPosition: 11
[     4.936]     LinGreenMaskSize: 6
[     4.936]     LinGreenFieldPosition: 5
[     4.936]     LinBlueMaskSize: 5
[     4.936]     LinBlueFieldPosition: 0
[     4.936]     LinRsvdMaskSize: 0
[     4.936]     LinRsvdFieldPosition: 0
[     4.936]     MaxPixelClock: 229500000
[     4.937] *Mode: 133 (320x400)
[     4.937]     ModeAttributes: 0x3bf
[     4.937]     WinAAttributes: 0x7
[     4.937]     WinBAttributes: 0x0
[     4.937]     WinGranularity: 64
[     4.937]     WinSize: 64
[     4.937]     WinASegment: 0xa000
[     4.937]     WinBSegment: 0x0
[     4.937]     WinFuncPtr: 0xc0007eac
[     4.937]     BytesPerScanline: 1280
[     4.937]     XResolution: 320
[     4.937]     YResolution: 400
[     4.937]     XCharSize: 8
[     4.937]     YCharSize: 16
[     4.937]     NumberOfPlanes: 1
[     4.937]     BitsPerPixel: 32
[     4.937]     NumberOfBanks: 1
[     4.937]     MemoryModel: 6
[     4.937]     BankSize: 0
[     4.937]     NumberOfImages: 6
[     4.937]     RedMaskSize: 8
[     4.937]     RedFieldPosition: 16
[     4.937]     GreenMaskSize: 8
[     4.937]     GreenFieldPosition: 8
[     4.937]     BlueMaskSize: 8
[     4.937]     BlueFieldPosition: 0
[     4.937]     RsvdMaskSize: 8
[     4.937]     RsvdFieldPosition: 24
[     4.937]     DirectColorModeInfo: 0
[     4.937]     PhysBasePtr: 0xe9000000
[     4.937]     LinBytesPerScanLine: 1280
[     4.937]     BnkNumberOfImagePages: 6
[     4.937]     LinNumberOfImagePages: 6
[     4.937]     LinRedMaskSize: 8
[     4.937]     LinRedFieldPosition: 16
[     4.937]     LinGreenMaskSize: 8
[     4.937]     LinGreenFieldPosition: 8
[     4.937]     LinBlueMaskSize: 8
[     4.937]     LinBlueFieldPosition: 0
[     4.937]     LinRsvdMaskSize: 8
[     4.937]     LinRsvdFieldPosition: 24
[     4.937]     MaxPixelClock: 229500000
[     4.938] Mode: 134 (320x240)
[     4.938]     ModeAttributes: 0x3bf
[     4.938]     WinAAttributes: 0x7
[     4.938]     WinBAttributes: 0x0
[     4.938]     WinGranularity: 64
[     4.938]     WinSize: 64
[     4.938]     WinASegment: 0xa000
[     4.938]     WinBSegment: 0x0
[     4.938]     WinFuncPtr: 0xc0007eac
[     4.938]     BytesPerScanline: 320
[     4.938]     XResolution: 320
[     4.938]     YResolution: 240
[     4.938]     XCharSize: 8
[     4.938]     YCharSize: 8
[     4.938]     NumberOfPlanes: 1
[     4.938]     BitsPerPixel: 8
[     4.938]     NumberOfBanks: 1
[     4.938]     MemoryModel: 4
[     4.938]     BankSize: 0
[     4.938]     NumberOfImages: 30
[     4.938]     RedMaskSize: 0
[     4.938]     RedFieldPosition: 0
[     4.938]     GreenMaskSize: 0
[     4.938]     GreenFieldPosition: 0
[     4.938]     BlueMaskSize: 0
[     4.938]     BlueFieldPosition: 0
[     4.938]     RsvdMaskSize: 0
[     4.938]     RsvdFieldPosition: 0
[     4.938]     DirectColorModeInfo: 0
[     4.938]     PhysBasePtr: 0xe9000000
[     4.938]     LinBytesPerScanLine: 320
[     4.938]     BnkNumberOfImagePages: 30
[     4.938]     LinNumberOfImagePages: 30
[     4.938]     LinRedMaskSize: 0
[     4.938]     LinRedFieldPosition: 0
[     4.938]     LinGreenMaskSize: 0
[     4.938]     LinGreenFieldPosition: 0
[     4.938]     LinBlueMaskSize: 0
[     4.938]     LinBlueFieldPosition: 0
[     4.938]     LinRsvdMaskSize: 0
[     4.938]     LinRsvdFieldPosition: 0
[     4.938]     MaxPixelClock: 229500000
[     4.939] Mode: 135 (320x240)
[     4.939]     ModeAttributes: 0x3bf
[     4.939]     WinAAttributes: 0x7
[     4.939]     WinBAttributes: 0x0
[     4.940]     WinGranularity: 64
[     4.940]     WinSize: 64
[     4.940]     WinASegment: 0xa000
[     4.940]     WinBSegment: 0x0
[     4.940]     WinFuncPtr: 0xc0007eac
[     4.940]     BytesPerScanline: 640
[     4.940]     XResolution: 320
[     4.940]     YResolution: 240
[     4.940]     XCharSize: 8
[     4.940]     YCharSize: 8
[     4.940]     NumberOfPlanes: 1
[     4.940]     BitsPerPixel: 16
[     4.940]     NumberOfBanks: 1
[     4.940]     MemoryModel: 6
[     4.940]     BankSize: 0
[     4.940]     NumberOfImages: 19
[     4.940]     RedMaskSize: 5
[     4.940]     RedFieldPosition: 11
[     4.940]     GreenMaskSize: 6
[     4.940]     GreenFieldPosition: 5
[     4.940]     BlueMaskSize: 5
[     4.940]     BlueFieldPosition: 0
[     4.940]     RsvdMaskSize: 0
[     4.940]     RsvdFieldPosition: 0
[     4.940]     DirectColorModeInfo: 0
[     4.940]     PhysBasePtr: 0xe9000000
[     4.940]     LinBytesPerScanLine: 640
[     4.940]     BnkNumberOfImagePages: 19
[     4.940]     LinNumberOfImagePages: 19
[     4.940]     LinRedMaskSize: 5
[     4.940]     LinRedFieldPosition: 11
[     4.940]     LinGreenMaskSize: 6
[     4.940]     LinGreenFieldPosition: 5
[     4.940]     LinBlueMaskSize: 5
[     4.940]     LinBlueFieldPosition: 0
[     4.940]     LinRsvdMaskSize: 0
[     4.940]     LinRsvdFieldPosition: 0
[     4.940]     MaxPixelClock: 229500000
[     4.941] *Mode: 136 (320x240)
[     4.941]     ModeAttributes: 0x3bf
[     4.941]     WinAAttributes: 0x7
[     4.941]     WinBAttributes: 0x0
[     4.941]     WinGranularity: 64
[     4.941]     WinSize: 64
[     4.941]     WinASegment: 0xa000
[     4.941]     WinBSegment: 0x0
[     4.941]     WinFuncPtr: 0xc0007eac
[     4.941]     BytesPerScanline: 1280
[     4.941]     XResolution: 320
[     4.941]     YResolution: 240
[     4.941]     XCharSize: 8
[     4.941]     YCharSize: 8
[     4.941]     NumberOfPlanes: 1
[     4.941]     BitsPerPixel: 32
[     4.941]     NumberOfBanks: 1
[     4.941]     MemoryModel: 6
[     4.941]     BankSize: 0
[     4.941]     NumberOfImages: 10
[     4.941]     RedMaskSize: 8
[     4.941]     RedFieldPosition: 16
[     4.941]     GreenMaskSize: 8
[     4.941]     GreenFieldPosition: 8
[     4.941]     BlueMaskSize: 8
[     4.941]     BlueFieldPosition: 0
[     4.941]     RsvdMaskSize: 8
[     4.941]     RsvdFieldPosition: 24
[     4.941]     DirectColorModeInfo: 0
[     4.941]     PhysBasePtr: 0xe9000000
[     4.941]     LinBytesPerScanLine: 1280
[     4.941]     BnkNumberOfImagePages: 10
[     4.941]     LinNumberOfImagePages: 10
[     4.941]     LinRedMaskSize: 8
[     4.941]     LinRedFieldPosition: 16
[     4.941]     LinGreenMaskSize: 8
[     4.941]     LinGreenFieldPosition: 8
[     4.941]     LinBlueMaskSize: 8
[     4.941]     LinBlueFieldPosition: 0
[     4.941]     LinRsvdMaskSize: 8
[     4.941]     LinRsvdFieldPosition: 24
[     4.941]     MaxPixelClock: 229500000
[     4.942] Mode: 13d (640x400)
[     4.942]     ModeAttributes: 0x3bf
[     4.942]     WinAAttributes: 0x7
[     4.942]     WinBAttributes: 0x0
[     4.942]     WinGranularity: 64
[     4.942]     WinSize: 64
[     4.942]     WinASegment: 0xa000
[     4.942]     WinBSegment: 0x0
[     4.942]     WinFuncPtr: 0xc0007eac
[     4.942]     BytesPerScanline: 1280
[     4.942]     XResolution: 640
[     4.942]     YResolution: 400
[     4.942]     XCharSize: 8
[     4.942]     YCharSize: 16
[     4.942]     NumberOfPlanes: 1
[     4.942]     BitsPerPixel: 16
[     4.942]     NumberOfBanks: 1
[     4.942]     MemoryModel: 6
[     4.942]     BankSize: 0
[     4.942]     NumberOfImages: 6
[     4.942]     RedMaskSize: 5
[     4.942]     RedFieldPosition: 11
[     4.942]     GreenMaskSize: 6
[     4.942]     GreenFieldPosition: 5
[     4.942]     BlueMaskSize: 5
[     4.942]     BlueFieldPosition: 0
[     4.942]     RsvdMaskSize: 0
[     4.942]     RsvdFieldPosition: 0
[     4.942]     DirectColorModeInfo: 0
[     4.942]     PhysBasePtr: 0xe9000000
[     4.942]     LinBytesPerScanLine: 1280
[     4.942]     BnkNumberOfImagePages: 6
[     4.942]     LinNumberOfImagePages: 6
[     4.942]     LinRedMaskSize: 5
[     4.942]     LinRedFieldPosition: 11
[     4.942]     LinGreenMaskSize: 6
[     4.942]     LinGreenFieldPosition: 5
[     4.942]     LinBlueMaskSize: 5
[     4.942]     LinBlueFieldPosition: 0
[     4.942]     LinRsvdMaskSize: 0
[     4.942]     LinRsvdFieldPosition: 0
[     4.942]     MaxPixelClock: 229500000
[     4.943] *Mode: 13e (640x400)
[     4.943]     ModeAttributes: 0x3bf
[     4.943]     WinAAttributes: 0x7
[     4.943]     WinBAttributes: 0x0
[     4.943]     WinGranularity: 64
[     4.943]     WinSize: 64
[     4.943]     WinASegment: 0xa000
[     4.943]     WinBSegment: 0x0
[     4.943]     WinFuncPtr: 0xc0007eac
[     4.943]     BytesPerScanline: 2560
[     4.943]     XResolution: 640
[     4.943]     YResolution: 400
[     4.943]     XCharSize: 8
[     4.943]     YCharSize: 16
[     4.943]     NumberOfPlanes: 1
[     4.943]     BitsPerPixel: 32
[     4.943]     NumberOfBanks: 1
[     4.943]     MemoryModel: 6
[     4.943]     BankSize: 0
[     4.943]     NumberOfImages: 2
[     4.943]     RedMaskSize: 8
[     4.943]     RedFieldPosition: 16
[     4.943]     GreenMaskSize: 8
[     4.943]     GreenFieldPosition: 8
[     4.943]     BlueMaskSize: 8
[     4.943]     BlueFieldPosition: 0
[     4.943]     RsvdMaskSize: 8
[     4.943]     RsvdFieldPosition: 24
[     4.943]     DirectColorModeInfo: 0
[     4.943]     PhysBasePtr: 0xe9000000
[     4.943]     LinBytesPerScanLine: 2560
[     4.943]     BnkNumberOfImagePages: 2
[     4.943]     LinNumberOfImagePages: 2
[     4.943]     LinRedMaskSize: 8
[     4.943]     LinRedFieldPosition: 16
[     4.943]     LinGreenMaskSize: 8
[     4.943]     LinGreenFieldPosition: 8
[     4.943]     LinBlueMaskSize: 8
[     4.943]     LinBlueFieldPosition: 0
[     4.943]     LinRsvdMaskSize: 8
[     4.943]     LinRsvdFieldPosition: 24
[     4.943]     MaxPixelClock: 229500000
[     4.945] Mode: 145 (1600x1200)
[     4.945]     ModeAttributes: 0x3bf
[     4.945]     WinAAttributes: 0x7
[     4.945]     WinBAttributes: 0x0
[     4.945]     WinGranularity: 64
[     4.945]     WinSize: 64
[     4.945]     WinASegment: 0xa000
[     4.945]     WinBSegment: 0x0
[     4.945]     WinFuncPtr: 0xc0007eac
[     4.945]     BytesPerScanline: 1600
[     4.945]     XResolution: 1600
[     4.945]     YResolution: 1200
[     4.945]     XCharSize: 8
[     4.945]     YCharSize: 16
[     4.945]     NumberOfPlanes: 1
[     4.945]     BitsPerPixel: 8
[     4.945]     NumberOfBanks: 1
[     4.945]     MemoryModel: 4
[     4.945]     BankSize: 0
[     4.945]     NumberOfImages: 1
[     4.945]     RedMaskSize: 0
[     4.945]     RedFieldPosition: 0
[     4.945]     GreenMaskSize: 0
[     4.945]     GreenFieldPosition: 0
[     4.945]     BlueMaskSize: 0
[     4.945]     BlueFieldPosition: 0
[     4.945]     RsvdMaskSize: 0
[     4.945]     RsvdFieldPosition: 0
[     4.945]     DirectColorModeInfo: 0
[     4.945]     PhysBasePtr: 0xe9000000
[     4.945]     LinBytesPerScanLine: 1600
[     4.945]     BnkNumberOfImagePages: 1
[     4.945]     LinNumberOfImagePages: 1
[     4.945]     LinRedMaskSize: 0
[     4.945]     LinRedFieldPosition: 0
[     4.945]     LinGreenMaskSize: 0
[     4.945]     LinGreenFieldPosition: 0
[     4.945]     LinBlueMaskSize: 0
[     4.945]     LinBlueFieldPosition: 0
[     4.945]     LinRsvdMaskSize: 0
[     4.945]     LinRsvdFieldPosition: 0
[     4.945]     MaxPixelClock: 229500000
[     4.946] Mode: 146 (1600x1200)
[     4.946]     ModeAttributes: 0x3bf
[     4.946]     WinAAttributes: 0x7
[     4.946]     WinBAttributes: 0x0
[     4.946]     WinGranularity: 64
[     4.946]     WinSize: 64
[     4.946]     WinASegment: 0xa000
[     4.946]     WinBSegment: 0x0
[     4.946]     WinFuncPtr: 0xc0007eac
[     4.946]     BytesPerScanline: 3200
[     4.946]     XResolution: 1600
[     4.946]     YResolution: 1200
[     4.946]     XCharSize: 8
[     4.946]     YCharSize: 16
[     4.946]     NumberOfPlanes: 1
[     4.946]     BitsPerPixel: 16
[     4.946]     NumberOfBanks: 1
[     4.946]     MemoryModel: 6
[     4.946]     BankSize: 0
[     4.946]     NumberOfImages: 1
[     4.946]     RedMaskSize: 5
[     4.946]     RedFieldPosition: 11
[     4.946]     GreenMaskSize: 6
[     4.946]     GreenFieldPosition: 5
[     4.946]     BlueMaskSize: 5
[     4.946]     BlueFieldPosition: 0
[     4.946]     RsvdMaskSize: 0
[     4.946]     RsvdFieldPosition: 0
[     4.946]     DirectColorModeInfo: 0
[     4.946]     PhysBasePtr: 0xe9000000
[     4.946]     LinBytesPerScanLine: 3200
[     4.946]     BnkNumberOfImagePages: 1
[     4.946]     LinNumberOfImagePages: 1
[     4.946]     LinRedMaskSize: 5
[     4.946]     LinRedFieldPosition: 11
[     4.946]     LinGreenMaskSize: 6
[     4.946]     LinGreenFieldPosition: 5
[     4.946]     LinBlueMaskSize: 5
[     4.946]     LinBlueFieldPosition: 0
[     4.946]     LinRsvdMaskSize: 0
[     4.946]     LinRsvdFieldPosition: 0
[     4.946]     MaxPixelClock: 229500000
[     4.947] *Mode: 14a (1600x1200)
[     4.947]     ModeAttributes: 0x3bf
[     4.947]     WinAAttributes: 0x7
[     4.947]     WinBAttributes: 0x0
[     4.947]     WinGranularity: 64
[     4.947]     WinSize: 64
[     4.947]     WinASegment: 0xa000
[     4.947]     WinBSegment: 0x0
[     4.947]     WinFuncPtr: 0xc0007eac
[     4.947]     BytesPerScanline: 6400
[     4.947]     XResolution: 1600
[     4.947]     YResolution: 1200
[     4.947]     XCharSize: 8
[     4.947]     YCharSize: 16
[     4.947]     NumberOfPlanes: 1
[     4.947]     BitsPerPixel: 32
[     4.947]     NumberOfBanks: 1
[     4.947]     MemoryModel: 6
[     4.947]     BankSize: 0
[     4.947]     NumberOfImages: 1
[     4.947]     RedMaskSize: 8
[     4.947]     RedFieldPosition: 16
[     4.947]     GreenMaskSize: 8
[     4.947]     GreenFieldPosition: 8
[     4.947]     BlueMaskSize: 8
[     4.947]     BlueFieldPosition: 0
[     4.947]     RsvdMaskSize: 8
[     4.947]     RsvdFieldPosition: 24
[     4.947]     DirectColorModeInfo: 0
[     4.947]     PhysBasePtr: 0xe9000000
[     4.947]     LinBytesPerScanLine: 6400
[     4.947]     BnkNumberOfImagePages: 1
[     4.947]     LinNumberOfImagePages: 1
[     4.947]     LinRedMaskSize: 8
[     4.947]     LinRedFieldPosition: 16
[     4.947]     LinGreenMaskSize: 8
[     4.947]     LinGreenFieldPosition: 8
[     4.947]     LinBlueMaskSize: 8
[     4.947]     LinBlueFieldPosition: 0
[     4.947]     LinRsvdMaskSize: 8
[     4.947]     LinRsvdFieldPosition: 24
[     4.947]     MaxPixelClock: 229500000
[     4.947] 
[     4.947] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[     4.947] (II) VESA(0): <default monitor>: Using hsync range of 24.00-83.00 kHz
[     4.947] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-75.00 Hz
[     4.947] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[     4.947] (WW) VESA(0): Unable to estimate virtual size
[     4.947] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[     4.950] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[     4.950] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[     4.950] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[     4.950] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[     4.950] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[     4.950] (**) VESA(0): *Built-in mode "1280x1024"
[     4.950] (**) VESA(0): *Built-in mode "1024x768"
[     4.950] (**) VESA(0): *Built-in mode "800x600"
[     4.950] (**) VESA(0): *Built-in mode "640x480"
[     4.950] (**) VESA(0): Display dimensions: (520, 290) mm
[     4.950] (**) VESA(0): DPI set to (62, 89)
[     4.950] (**) VESA(0): Using "Shadow Framebuffer"
[     4.950] (II) Loading sub module "shadow"
[     4.950] (II) LoadModule: "shadow"
[     4.950] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     4.951] (II) Module shadow: vendor="X.Org Foundation"
[     4.951]     compiled for 1.16.0, module version = 1.1.0
[     4.951]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.951] (II) Loading sub module "fb"
[     4.951] (II) LoadModule: "fb"
[     4.951] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.951] (II) Module fb: vendor="X.Org Foundation"
[     4.951]     compiled for 1.16.0, module version = 1.0.0
[     4.951]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.951] (==) Depth 24 pixmap format is 32 bpp
[     4.951] (II) Loading sub module "int10"
[     4.951] (II) LoadModule: "int10"
[     4.951] (II) Loading /usr/lib/xorg/modules/libint10.so
[     4.951] (II) Module int10: vendor="X.Org Foundation"
[     4.951]     compiled for 1.16.0, module version = 1.0.0
[     4.951]     ABI class: X.Org Video Driver, version 18.0
[     4.951] (II) VESA(0): initializing int10
[     4.951] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[     4.993] (II) VESA(0): VESA BIOS detected
[     4.993] (II) VESA(0): VESA VBE Version 3.0
[     4.993] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[     4.993] (II) VESA(0): VESA VBE OEM: NVIDIA
[     4.994] (II) VESA(0): VESA VBE OEM Software Rev: 128.4
[     4.994] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[     4.994] (II) VESA(0): VESA VBE OEM Product: GK104 Board - 20040001
[     4.994] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[     4.994] (II) VESA(0): virtual address = 0x7f758fc4f000,
    physical address = 0xe9000000, size = 14680064
[     4.998] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[     5.105] (==) VESA(0): Default visual is TrueColor
[     5.106] (==) VESA(0): Backing store enabled
[     5.106] (==) VESA(0): DPMS enabled
[     5.106] (==) RandR enabled
[     5.110] (II) SELinux: Disabled on system
[     5.110] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.110] (EE) AIGLX: reverting to software rendering
[     5.127] (II) AIGLX: Loaded and initialized swrast
[     5.127] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.136] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.136] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.136] (II) LoadModule: "evdev"
[     5.136] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.138] (II) Module evdev: vendor="X.Org Foundation"
[     5.138]     compiled for 1.16.0, module version = 2.9.0
[     5.138]     Module class: X.Org XInput Driver
[     5.138]     ABI class: X.Org XInput driver, version 21.0
[     5.138] (II) Using input driver 'evdev' for 'Power Button'
[     5.138] (**) Power Button: always reports core events
[     5.138] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.138] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.138] (--) evdev: Power Button: Found keys
[     5.138] (II) evdev: Power Button: Configuring as keyboard
[     5.138] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.138] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.138] (**) Option "xkb_rules" "evdev"
[     5.138] (**) Option "xkb_model" "pc105"
[     5.138] (**) Option "xkb_layout" "us"
[     5.138] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[     5.138] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     5.139] (II) Using input driver 'evdev' for 'Sleep Button'
[     5.139] (**) Sleep Button: always reports core events
[     5.139] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[     5.139] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     5.139] (--) evdev: Sleep Button: Found keys
[     5.139] (II) evdev: Sleep Button: Configuring as keyboard
[     5.139] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[     5.139] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[     5.139] (**) Option "xkb_rules" "evdev"
[     5.139] (**) Option "xkb_model" "pc105"
[     5.139] (**) Option "xkb_layout" "us"
[     5.139] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[     5.139] (II) No input driver specified, ignoring this device.
[     5.139] (II) This device may have been added with another device file.
[     5.139] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event11)
[     5.139] (II) No input driver specified, ignoring this device.
[     5.139] (II) This device may have been added with another device file.
[     5.139] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[     5.139] (II) No input driver specified, ignoring this device.
[     5.139] (II) This device may have been added with another device file.
[     5.139] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event13)
[     5.139] (II) No input driver specified, ignoring this device.
[     5.139] (II) This device may have been added with another device file.
[     5.140] (II) config/udev: Adding input device Razer Razer BlackWidow Ultimate 2013 (/dev/input/event14)
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: Applying InputClass "evdev keyboard catchall"
[     5.140] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow Ultimate 2013'
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: always reports core events
[     5.140] (**) evdev: Razer Razer BlackWidow Ultimate 2013: Device: "/dev/input/event14"
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Vendor 0x1532 Product 0x11a
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found keys
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Configuring as keyboard
[     5.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:1532:011A.0002/input/input17/event14"
[     5.140] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow Ultimate 2013" (type: KEYBOARD, id 8)
[     5.140] (**) Option "xkb_rules" "evdev"
[     5.140] (**) Option "xkb_model" "pc105"
[     5.140] (**) Option "xkb_layout" "us"
[     5.140] (II) config/udev: Adding input device Razer Razer BlackWidow Ultimate 2013 (/dev/input/event15)
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: Applying InputClass "evdev keyboard catchall"
[     5.140] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow Ultimate 2013'
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: always reports core events
[     5.140] (**) evdev: Razer Razer BlackWidow Ultimate 2013: Device: "/dev/input/event15"
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Vendor 0x1532 Product 0x11a
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found 1 mouse buttons
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found scroll wheel(s)
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found relative axes
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Forcing relative x/y axes to exist.
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found absolute axes
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found absolute multitouch axes
[     5.140] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found keys
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Configuring as mouse
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Configuring as keyboard
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Adding scrollwheel support
[     5.140] (**) evdev: Razer Razer BlackWidow Ultimate 2013: YAxisMapping: buttons 4 and 5
[     5.140] (**) evdev: Razer Razer BlackWidow Ultimate 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1532:011A.0003/input/input18/event15"
[     5.140] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow Ultimate 2013" (type: KEYBOARD, id 9)
[     5.140] (**) Option "xkb_rules" "evdev"
[     5.140] (**) Option "xkb_model" "pc105"
[     5.140] (**) Option "xkb_layout" "us"
[     5.140] (II) evdev: Razer Razer BlackWidow Ultimate 2013: initialized for relative axes.
[     5.140] (WW) evdev: Razer Razer BlackWidow Ultimate 2013: ignoring absolute axes.
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: (accel) keeping acceleration scheme 1
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration profile 0
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration factor: 2.000
[     5.140] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration threshold: 4
[     5.141] (II) config/udev: Adding input device Razer Razer BlackWidow Ultimate 2013 (/dev/input/event16)
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: Applying InputClass "evdev pointer catchall"
[     5.141] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow Ultimate 2013'
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: always reports core events
[     5.141] (**) evdev: Razer Razer BlackWidow Ultimate 2013: Device: "/dev/input/event16"
[     5.141] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Vendor 0x1532 Product 0x11a
[     5.141] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found 3 mouse buttons
[     5.141] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found scroll wheel(s)
[     5.141] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found relative axes
[     5.141] (--) evdev: Razer Razer BlackWidow Ultimate 2013: Found x and y relative axes
[     5.141] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Configuring as mouse
[     5.141] (II) evdev: Razer Razer BlackWidow Ultimate 2013: Adding scrollwheel support
[     5.141] (**) evdev: Razer Razer BlackWidow Ultimate 2013: YAxisMapping: buttons 4 and 5
[     5.141] (**) evdev: Razer Razer BlackWidow Ultimate 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.2/0003:1532:011A.0004/input/input19/event16"
[     5.141] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow Ultimate 2013" (type: MOUSE, id 10)
[     5.141] (II) evdev: Razer Razer BlackWidow Ultimate 2013: initialized for relative axes.
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: (accel) keeping acceleration scheme 1
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration profile 0
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration factor: 2.000
[     5.141] (**) Razer Razer BlackWidow Ultimate 2013: (accel) acceleration threshold: 4
[     5.141] (II) config/udev: Adding input device Razer Razer BlackWidow Ultimate 2013 (/dev/input/mouse1)
[     5.141] (II) No input driver specified, ignoring this device.
[     5.141] (II) This device may have been added with another device file.
[     5.141] (II) config/udev: Adding input device HD Pro Webcam C920 (/dev/input/event17)
[     5.141] (**) HD Pro Webcam C920: Applying InputClass "evdev keyboard catchall"
[     5.141] (II) Using input driver 'evdev' for 'HD Pro Webcam C920'
[     5.141] (**) HD Pro Webcam C920: always reports core events
[     5.141] (**) evdev: HD Pro Webcam C920: Device: "/dev/input/event17"
[     5.141] (--) evdev: HD Pro Webcam C920: Vendor 0x46d Product 0x82d
[     5.141] (--) evdev: HD Pro Webcam C920: Found keys
[     5.141] (II) evdev: HD Pro Webcam C920: Configuring as keyboard
[     5.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input20/event17"
[     5.141] (II) XINPUT: Adding extended input device "HD Pro Webcam C920" (type: KEYBOARD, id 11)
[     5.141] (**) Option "xkb_rules" "evdev"
[     5.141] (**) Option "xkb_model" "pc105"
[     5.141] (**) Option "xkb_layout" "us"
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event7)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event8)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event3)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event4)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.142] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event6)
[     5.142] (II) No input driver specified, ignoring this device.
[     5.142] (II) This device may have been added with another device file.
[     5.143] (II) config/udev: Adding input device ROCCAT ROCCAT Lua (/dev/input/event2)
[     5.143] (**) ROCCAT ROCCAT Lua: Applying InputClass "evdev pointer catchall"
[     5.143] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Lua'
[     5.143] (**) ROCCAT ROCCAT Lua: always reports core events
[     5.143] (**) evdev: ROCCAT ROCCAT Lua: Device: "/dev/input/event2"
[     5.143] (--) evdev: ROCCAT ROCCAT Lua: Vendor 0x1e7d Product 0x2c2e
[     5.143] (--) evdev: ROCCAT ROCCAT Lua: Found 9 mouse buttons
[     5.143] (--) evdev: ROCCAT ROCCAT Lua: Found scroll wheel(s)
[     5.143] (--) evdev: ROCCAT ROCCAT Lua: Found relative axes
[     5.143] (--) evdev: ROCCAT ROCCAT Lua: Found x and y relative axes
[     5.143] (II) evdev: ROCCAT ROCCAT Lua: Configuring as mouse
[     5.143] (II) evdev: ROCCAT ROCCAT Lua: Adding scrollwheel support
[     5.143] (**) evdev: ROCCAT ROCCAT Lua: YAxisMapping: buttons 4 and 5
[     5.143] (**) evdev: ROCCAT ROCCAT Lua: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.143] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:08:00.0/usb5/5-1/5-1:1.0/0003:1E7D:2C2E.0001/input/input5/event2"
[     5.143] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Lua" (type: MOUSE, id 12)
[     5.143] (II) evdev: ROCCAT ROCCAT Lua: initialized for relative axes.
[     5.143] (**) ROCCAT ROCCAT Lua: (accel) keeping acceleration scheme 1
[     5.143] (**) ROCCAT ROCCAT Lua: (accel) acceleration profile 0
[     5.143] (**) ROCCAT ROCCAT Lua: (accel) acceleration factor: 2.000
[     5.143] (**) ROCCAT ROCCAT Lua: (accel) acceleration threshold: 4
[     5.143] (II) config/udev: Adding input device ROCCAT ROCCAT Lua (/dev/input/mouse0)
[     5.143] (II) No input driver specified, ignoring this device.
[     5.143] (II) This device may have been added with another device file.
[    17.397] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    19.586] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.633] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.714] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.743] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.763] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

---

### Post by tokyobadger on 2015-01-16
> **TWFJR said:**
> The last "Software Update," where there was a kernel update broke Xorg. 
- Xorg was working with the exact same hardware before the Software Update?
- Were you using Nouveau or Nvidia driver before the update?
- Was this a regular software update or did you upgrade versions? (what version are you on eg 14.04?)
- Do you know what the previous kernel version was and what the updated kernel version is?

> **TWFJR said:**
> ddcprobe shows that I have a GK104 Board - 20040001 Chip Rev, memory 14336kb; this is NVIDIA graphics. I am running Intel Core i7-3960X CPU @ 3.30GHz X 12, 62.4 GiB memory, 64 bit, 876.9 GB with RAID 0. 
- The card appears to be a GeForce 660Ti - correct?
- Was this a pre-build or did you put it together yourself?

> **TWFJR said:**
> Using X.OrgX server - Noueau display driver. I believe this driver now has a bug. I really don't know what to call the problem. I do not understand enough about what or how to discover the real problem. I do wonder if I can resolve this problem by simply removing the driver and installing another driver, proprietary driver like NVIDIA binary driver 331.113 . . . updates. Please advise regarding possible bug and whether changing the graphics driver will solve the problem. Is NVIDIA binary driver 331.113 going to work with my graphics board? Will I need to change to version 331.113 that has been tested first before updating to 331 update? I read where I should update the graphics driver and all hardware before reporting a bug.

Unity icons are large and 2nd monitor is not recognized.
- Considering the rest of your hardware specs I would have started with the Nvidia drivers rather than Nouveau 
- As Temüjin stated your card should be supported by Nvidia-331 or later drivers

---

### Post by Yellow Pasque on 2015-01-17
```
(EE) [drm] KMS not enabled
```

So the problem seems to be at the kernel level. The nouveau driver chokes, and X falls back to generic VESA driver, which will not give you the resolution you want (or any 3D acceleration).

You can continue to try to troubleshoot the issue, looking for clues in dmesg:
```
dmesg | egrep -i 'nouv|nv'
```

Realistically, the proprietary driver is better for most users at this point. The nouveau driver should be in better shape by the time Ubuntu 15.04 rolls out.

---

### Post by TWFJR on 2015-01-17
-Nouveau was being used as default graphics driver.
-Regular update, the last update that updated the kernel.
-No, I don't know what the previous version was.
-I do believe that the graphics board is 660Ti.
-Local computer company built this computer for me.
- Were you using Nouveau or Nvidia driver before the update?
- Was this a regular software update or did you upgrade versions? (what version are you on eg 14.04?)
- Do you know what the previous kernel version was and what the updated kernel version is?
*
- The card appears to be a GeForce 660Ti - correct?
- Was this a pre-build or did you put it together yourself?

---

### Post by tokyobadger on 2015-01-17
Thanks for the details. I would do as Temüjin suggests and try the proprietary Nvidia drivers:
1. Go to Software & Updates
2. Select the Additional Drivers tab
3. Select Nvidia 331 (might as well choose 331-updates)
4. Apply changes

---

### Post by TWFJR on 2015-01-17
tom@tom-desktop:/var/log$ dmesg | egrep -i 'nouv|nv'
[    0.000000] BIOS-e820: [mem 0x00000000d8f3a000-0x00000000d911dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000db718000-0x00000000db7befff] ACPI NVS
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aEventBlock: 16, using default 32 (20140424/tbfadt-699)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/PmTimerBlock: 24, using default 32 (20140424/tbfadt-699)
[    0.213714] PM: Registering ACPI NVS region [mem 0xd8f3a000-0xd911dfff] (1982464 bytes)
[    0.213714] PM: Registering ACPI NVS region [mem 0xdb718000-0xdb7befff] (684032 bytes)
[    0.712843] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.186525] fb: switching to nouveaufb from VESA VGA
[    2.186877] nouveau  [  DEVICE][0000:02:00.0] BOOT0  : 0x0e4030a2
[    2.186879] nouveau  [  DEVICE][0000:02:00.0] Chipset: GK104 (NVE4)
[    2.186881] nouveau  [  DEVICE][0000:02:00.0] Family : NVE0
[    2.186932] nouveau  [   VBIOS][0000:02:00.0] checking PRAMIN for image...
[    2.186939] nouveau  [   VBIOS][0000:02:00.0] ... signature not found
[    2.186941] nouveau  [   VBIOS][0000:02:00.0] checking PROM for image...
[    2.228902] nouveau  [   VBIOS][0000:02:00.0] ... appears to be valid
[    2.228906] nouveau  [   VBIOS][0000:02:00.0] using image from PROM
[    2.229012] nouveau  [   VBIOS][0000:02:00.0] BIT signature found
[    2.229016] nouveau  [   VBIOS][0000:02:00.0] version 80.04.4b.00.2e
[    2.229542] nouveau 0000:02:00.0: irq 99 for MSI/MSI-X
[    2.229551] nouveau  [     PMC][0000:02:00.0] MSI interrupts enabled
[    2.229598] nouveau  [     PFB][0000:02:00.0] RAM type: GDDR5
[    2.229600] nouveau  [     PFB][0000:02:00.0] RAM size: 2048 MiB
[    2.229601] nouveau  [     PFB][0000:02:00.0]    ZCOMP: 0 tags
[    2.232595] nouveau  [    VOLT][0000:02:00.0] GPU voltage: 987500uv
[    2.261513] nouveau  [  PTHERM][0000:02:00.0] FAN control: PWM
[    2.261527] nouveau  [  PTHERM][0000:02:00.0] fan management: automatic
[    2.261544] nouveau  [  PTHERM][0000:02:00.0] internal sensor: yes
[    2.261576] nouveau  [     CLK][0000:02:00.0] 07: core 324 MHz memory 648 MHz 
[    2.261619] nouveau  [     CLK][0000:02:00.0] 0a: core 324-862 MHz memory 1620 MHz 
[    2.261744] nouveau  [     CLK][0000:02:00.0] 0d: core 540-1254 MHz memory 6008 MHz 
[    2.261885] nouveau  [     CLK][0000:02:00.0] 0f: core 540-1254 MHz memory 6008 MHz 
[    2.261955] nouveau  [     CLK][0000:02:00.0] --: core 324 MHz memory 648 MHz 
[    2.303217] nouveau  [     DRM] VRAM: 2048 MiB
[    2.303218] nouveau  [     DRM] GART: 1048576 MiB
[    2.303221] nouveau  [     DRM] TMDS table version 2.0
[    2.303222] nouveau  [     DRM] DCB version 4.0
[    2.303223] nouveau  [     DRM] DCB outp 00: 01000f02 00020030
[    2.303224] nouveau  [     DRM] DCB outp 01: 02000f00 00000000
[    2.303226] nouveau  [     DRM] DCB outp 02: 08011f82 00020030
[    2.303227] nouveau  [     DRM] DCB outp 03: 02822f62 0f420010
[    2.303228] nouveau  [     DRM] DCB outp 05: 04833fb6 0f420010
[    2.303229] nouveau  [     DRM] DCB outp 06: 04033f72 00020010
[    2.303230] nouveau  [     DRM] DCB conn 00: 00001030
[    2.303232] nouveau  [     DRM] DCB conn 01: 00020131
[    2.303233] nouveau  [     DRM] DCB conn 02: 00002261
[    2.303234] nouveau  [     DRM] DCB conn 03: 00010346
[    2.303235] nouveau  [     DRM] DCB conn 04: 00000460
[    2.338108] nouveau: probe of 0000:02:00.0 failed with error -12
[    2.804913] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1/input13
[    2.805037] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1/input14
[    2.805152] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1/input15
[    2.805281] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1/input16




If changing the Nouveau driver to the NVIDIA driver 331 is a solution, is it necessary to remove Nouveau first and then install NVIDIA or, can I just install NVIDIA without removing Nouveau.

---

### Post by tokyobadger on 2015-01-17
> **TWFJR said:**
> If changing the Nouveau driver to the NVIDIA driver 331 is a solution, is it necessary to remove Nouveau first and then install NVIDIA or, can I just install NVIDIA without removing Nouveau.
I haven't had to do anything in the last couple of years with nouveau when installing nvidia - it used to be (maybe specific to some distros) that you'd need to blacklist nouveau to prevent a conflict but you should be fine to install nvidia and then reboot

---

### Post by Yellow Pasque on 2015-01-17
Ubuntu's nvidia package automatically takes care of blacklisting nouveau driver, so you don't need to do anything special before installing the proprietary driver.

```
nouveau: probe of 0000:02:00.0 failed with error -12
```
Googling this didn't turn up a lot. If you 're still interested in troubleshooting, what kernel were you using before (i.e. the last one that worked)?

---

### Post by TWFJR on 2015-01-18
Many thanks for all the help. I installed NVIDIA 331 tested and rebooted. Everything wrong is now working. As for the bug, it is evident that the last update for Ubuntu 14.10 caused the failure of Noveau. Thanks again for all the assistance.

---

