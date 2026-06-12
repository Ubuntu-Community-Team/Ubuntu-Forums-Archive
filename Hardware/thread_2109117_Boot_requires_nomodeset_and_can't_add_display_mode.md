---
title: "Boot requires nomodeset and can't add display modes ?"
date: 2013-01-26
forum: Hardware
---

### Post by ChM on 2013-01-26
I have a new PC with i3-3225 processor and Asus P8H77-1 motherboard. I use the HD4000 GPU in the CPU connected to a Belinea display with 1280x1024 resolution. The display is connected through a KVM switch. I've installed Xubuntu 12.04 64bit.

Here are some infos:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)

```

```
$ sudo lshw -c video
  *-display NON-RÉCLAMÉ   
       description: VGA compatible controller
       produit: Ivy Bridge Graphics Controller
       fabriquant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 09
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       ressources: mémoire:f7800000-f7bfffff mémoire:e0000000-efffffff portE/S:f000(taille=64)

```

The first problem I have is that I need nomodeset option to get the splash screen and login screen. Without it, I do see the grub2 screen with a 1280x1024 resolution, but after boot starts, the display don't get a signal anymore and turns black. When I set the nomodeset option, the system boots and is usable. 

The second problem I have is that if I boot with the display set to another computer by the KVM switchn, the screen resolution is limited to 1024x768 max. I tried to change the mode by using xrandr but it always fails with an error. 

I suspect it could be a consequence of the nomodeset option which disable the KMS system. So maybe if I solve this problem first, I may solve the second problem. Could the need for the nomodeset option result from a misconfigured bios ?

---

### Post by oldfred on 2013-01-26
I think nomodeset prevents the Intel driver from loading. You are forcing nouveau.

There is only one Intel driver for all versions. Try this:
Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1    

       With 11.04:SandyBridge
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)
acpi_osi=linux pci=noacpi
[http://ubuntuforums.org/showthread.php?t=1900897](http://ubuntuforums.org/showthread.php?t=1900897)

    
       For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by ChM on 2013-01-27
Unfortunately none of these options worked. I then suspected it could be caused by the KVM switch because I also had to add nomodeset to VIA PC connected to the KVM switch. 

I then connected the display directly to the PC and tried to boot without nomodeset and it succeeded. 

So the KVM is the cause of the problem. 

Here is the Xorg.0.log section relative to the video driver initialization **without KVM switch**

```

[     4.906] (==) Matched intel as autoconfigured driver 0
[     4.906] (==) Matched vesa as autoconfigured driver 1
[     4.906] (==) Matched fbdev as autoconfigured driver 2
[     4.906] (==) Assigned the driver to the xf86ConfigLayout
[     4.906] (II) LoadModule: "intel"
[     4.906] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.907] (II) Module intel: vendor="X.Org Foundation"
[     4.907]    compiled for 1.11.3, module version = 2.17.0
[     4.907]    Module class: X.Org Video Driver
[     4.907]    ABI class: X.Org Video Driver, version 11.0
[     4.907] (II) LoadModule: "vesa"
[     4.907] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.907] (II) Module vesa: vendor="X.Org Foundation"
[     4.907]    compiled for 1.11.3, module version = 2.3.0
[     4.907]    Module class: X.Org Video Driver
[     4.907]    ABI class: X.Org Video Driver, version 11.0
[     4.907] (II) LoadModule: "fbdev"
[     4.907] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.907] (II) Module fbdev: vendor="X.Org Foundation"
[     4.907]    compiled for 1.11.3, module version = 0.4.2
[     4.907]    ABI class: X.Org Video Driver, version 11.0
[     4.907] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     4.907] (II) VESA: driver for VESA chipsets: vesa
[     4.907] (II) FBDEV: driver for framebuffer: fbdev
[     4.907] (++) using VT number 7

[     4.908] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.908] (WW) Falling back to old probe method for vesa
[     4.908] (WW) Falling back to old probe method for fbdev
[     4.908] (II) Loading sub module "fbdevhw"
[     4.908] (II) LoadModule: "fbdevhw"
[     4.908] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.908] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.908]    compiled for 1.11.3, module version = 0.0.2
[     4.908]    ABI class: X.Org Video Driver, version 11.0
[     4.908] drmOpenDevice: node name is /dev/dri/card0
[     4.908] drmOpenDevice: open result is 9, (OK)
[     4.908] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     4.908] drmOpenDevice: node name is /dev/dri/card0
[     4.908] drmOpenDevice: open result is 9, (OK)
[     4.908] drmOpenByBusid: drmOpenMinor returns 9
[     4.908] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     4.908] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     4.908] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     4.908] (==) intel(0): RGB weight 888
[     4.908] (==) intel(0): Default visual is TrueColor
[     4.908] (II) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT2)
[     4.908] (--) intel(0): Chipset: "Ivybridge Desktop (GT2)"
[     4.908] (**) intel(0): Relaxed fencing enabled
[     4.908] (**) intel(0): Wait on SwapBuffers? enabled
[     4.908] (**) intel(0): Triple buffering? enabled
[     4.908] (**) intel(0): Framebuffer tiled
[     4.908] (**) intel(0): Pixmaps tiled
[     4.908] (**) intel(0): 3D buffers tiled
[     4.908] (**) intel(0): SwapBuffers wait enabled
[     4.908] (==) intel(0): video overlay key set to 0x101fe
[     4.967] (II) intel(0): Output VGA1 has no monitor section
[     4.971] (II) intel(0): Output HDMI1 has no monitor section
[     4.976] (II) intel(0): Output HDMI2 has no monitor section
[     5.024] (II) intel(0): Output DP1 has no monitor section
[     5.072] (II) intel(0): Output DP2 has no monitor section
[     5.130] (II) intel(0): EDID for output VGA1
[     5.130] (II) intel(0): Manufacturer: MAX  Model: 78e  Serial#: 5185
[     5.130] (II) intel(0): Year: 2006  Week: 43
[     5.130] (II) intel(0): EDID Version: 1.3
[     5.130] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[     5.130] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[     5.130] (II) intel(0): Max Image Size [cm]: horiz.: 37  vert.: 30
[     5.130] (II) intel(0): Gamma: 2.20

```

Here is the xrandr output:

```

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

Here is the Xorg.0.log section relative to the video driver initialization **with KVM switch** and without nomodeset. I connected through ssh to get it because the display disabled. 

```

[     4.560] (==) Matched intel as autoconfigured driver 0
[     4.560] (==) Matched vesa as autoconfigured driver 1
[     4.560] (==) Matched fbdev as autoconfigured driver 2
[     4.560] (==) Assigned the driver to the xf86ConfigLayout
[     4.560] (II) LoadModule: "intel"
[     4.560] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.561] (II) Module intel: vendor="X.Org Foundation"
[     4.561]    compiled for 1.11.3, module version = 2.17.0
[     4.561]    Module class: X.Org Video Driver
[     4.561]    ABI class: X.Org Video Driver, version 11.0
[     4.561] (II) LoadModule: "vesa"
[     4.562] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.562] (II) Module vesa: vendor="X.Org Foundation"
[     4.562]    compiled for 1.11.3, module version = 2.3.0
[     4.562]    Module class: X.Org Video Driver
[     4.562]    ABI class: X.Org Video Driver, version 11.0
[     4.562] (II) LoadModule: "fbdev"
[     4.562] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.563] (II) Module fbdev: vendor="X.Org Foundation"
[     4.563]    compiled for 1.11.3, module version = 0.4.2
[     4.563]    ABI class: X.Org Video Driver, version 11.0
[     4.563] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     4.563] (II) VESA: driver for VESA chipsets: vesa
[     4.563] (II) FBDEV: driver for framebuffer: fbdev
[     4.563] (++) using VT number 7

[     4.564] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.564] (WW) Falling back to old probe method for vesa
[     4.564] (WW) Falling back to old probe method for fbdev
[     4.564] (II) Loading sub module "fbdevhw"
[     4.564] (II) LoadModule: "fbdevhw"
[     4.564] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.564] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.564]    compiled for 1.11.3, module version = 0.0.2
[     4.564]    ABI class: X.Org Video Driver, version 11.0
[     4.564] drmOpenDevice: node name is /dev/dri/card0
[     4.564] drmOpenDevice: open result is 9, (OK)
[     4.565] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     4.565] drmOpenDevice: node name is /dev/dri/card0
[     4.565] drmOpenDevice: open result is 9, (OK)
[     4.565] drmOpenByBusid: drmOpenMinor returns 9
[     4.565] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     4.565] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     4.565] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     4.565] (==) intel(0): RGB weight 888
[     4.565] (==) intel(0): Default visual is TrueColor
[     4.565] (II) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT2)
[     4.565] (--) intel(0): Chipset: "Ivybridge Desktop (GT2)"
[     4.565] (**) intel(0): Relaxed fencing enabled
[     4.565] (**) intel(0): Wait on SwapBuffers? enabled
[     4.565] (**) intel(0): Triple buffering? enabled
[     4.565] (**) intel(0): Framebuffer tiled
[     4.565] (**) intel(0): Pixmaps tiled
[     4.565] (**) intel(0): 3D buffers tiled
[     4.565] (**) intel(0): SwapBuffers wait enabled
[     4.565] (==) intel(0): video overlay key set to 0x101fe
[     4.565] (II) intel(0): Output VGA1 has no monitor section
[     4.569] (II) intel(0): Output HDMI1 has no monitor section
[     4.574] (II) intel(0): Output HDMI2 has no monitor section
[     4.620] (II) intel(0): Output DP1 has no monitor section
[     4.668] (II) intel(0): Output DP2 has no monitor section
[     4.668] (II) intel(0): EDID for output VGA1
[     4.672] (II) intel(0): EDID for output HDMI1
[     4.677] (II) intel(0): EDID for output HDMI2
[     4.728] (II) intel(0): EDID for output DP1
[     4.776] (II) intel(0): EDID for output DP2
[     4.776] (II) intel(0): Output VGA1 disconnected
[     4.776] (II) intel(0): Output HDMI1 disconnected
[     4.776] (II) intel(0): Output HDMI2 disconnected
[     4.776] (II) intel(0): Output DP1 disconnected
[     4.776] (II) intel(0): Output DP2 disconnected
[     4.776] (WW) intel(0): No outputs definitely connected, trying again...
[     4.776] (II) intel(0): Output VGA1 disconnected
[     4.776] (II) intel(0): Output HDMI1 disconnected
[     4.776] (II) intel(0): Output HDMI2 disconnected
[     4.776] (II) intel(0): Output DP1 disconnected
[     4.776] (II) intel(0): Output DP2 disconnected
[     4.776] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[     4.776] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     4.776] (II) intel(0): Kernel page flipping support detected, enabling
[     4.776] (==) intel(0): DPI set to (96, 96)
[     4.776] (II) Loading sub module "fb"
[     4.776] (II) LoadModule: "fb"
[     4.776] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.777] (II) Module fb: vendor="X.Org Foundation"
[     4.777]    compiled for 1.11.3, module version = 1.0.0
[     4.777]    ABI class: X.Org ANSI C Emulation, version 0.4
[     4.777] (II) Loading sub module "dri2"
[     4.777] (II) LoadModule: "dri2"
[     4.777] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     4.777] (II) Module dri2: vendor="X.Org Foundation"
[     4.777]    compiled for 1.11.3, module version = 1.2.0
[     4.777]    ABI class: X.Org Server Extension, version 6.0
[     4.777] (II) UnloadModule: "vesa"
[     4.777] (II) Unloading vesa
[     4.777] (II) UnloadModule: "fbdev"
[     4.777] (II) Unloading fbdev
[     4.777] (II) UnloadModule: "fbdevhw"
[     4.777] (II) Unloading fbdevhw
[     4.777] (==) Depth 24 pixmap format is 32 bpp
[     4.777] (II) intel(0): [DRI2] Setup complete
[     4.777] (II) intel(0): [DRI2]   DRI driver: i965
[     4.777] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[     4.778] (II) UXA(0): Driver registered support for the following operations:
[     4.778] (II)         solid
[     4.778] (II)         copy
[     4.778] (II)         composite (RENDER acceleration)
[     4.778] (II)         put_image
[     4.778] (II)         get_image
[     4.778] (==) intel(0): Backing store disabled
[     4.778] (==) intel(0): Silken mouse enabled
[     4.778] (II) intel(0): Initializing HW Cursor
[     4.779] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.779] (==) intel(0): DPMS enabled
[     4.779] (==) intel(0): Intel XvMC decoder enabled
[     4.779] (II) intel(0): Set up textured video
[     4.779] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     4.779] (II) intel(0): direct rendering: DRI2 Enabled
[     4.779] (==) intel(0): hotplug detection: "enabled"
[     4.779] (--) RandR disabled

```

I can't get an xrandr output since it is disabled. 

When booting with nomodeset the VESA driver is loaded instead of the intel driver. 

This is the xrandr output with the VESA driver:

```

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```

The KVM is a TRENDnet tk-409. The problem is apparently that the PC doesn't have access to the display while the intel driver is started. I guess this may happen if the graphic card output is cut, in which case the KVM switch cuts the connection to the display. Restoring the graphic card output power some time later doesn't help. 

**Conclusion **

So the Intel driver is loaded but for some unknown reason the driver can't get a connection to the display (VGA1) and thus shutsdown the display output.

---

### Post by ChM on 2013-02-05
I found the explanation. The problem is caused by the cheap KVM switch I used. See [http://askubuntu.com/a/251137/15352](http://askubuntu.com/a/251137/15352) for a detailed explanation and feedback on the new "smarter" KVM I bought.

---

