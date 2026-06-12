---
title: "Problems with Nomodeset and external monitor"
date: 2018-09-04
forum: Hardware
---

### Post by RedChili on 2018-09-04
Hi!

I've previously been running an old laptop connected to an external monitor via VGA.

However, I recently needed some more power, so I bought a new HP gaming laptop with a much better graphics card. But when I tried to install Ubuntu Mate 18.04 on that laptop, I had some serious issues with the monitor not working, so I searched the forum and found that I had to specify "nomodeset" in the Grub file.

When I did that, it worked, with the exception that I cannot change the display preferences, such as resolutuon, which is stuck at 1920x1080.

But now I'm trying to connect the laptop to an extgernal monitor, I can't get any signal. It works with Windows on the same laptop, so it's not a hardware problem. I searched the net and found that the problem may be the nomodeset settiing. The problem is that if I remove that, I won't see anything at all when I power on the laptop.

So, does anybody have any solution to this problem?

Thanks in advance!

---

### Post by RedChili on 2018-09-07
Is there really nobody that can help out with this?

Some more information in case it's needed: I have an HP Pavilion Power 15-CB084NO laptop with a Nvidia Geforce GTX 1050 graphics card.

---

### Post by Bashing-om on 2018-09-07
jon.andersen; Hello;

Try this and report results:
remove the nomodeset boot parameter,
boot to the login screen and here execute ctl+alt+F2 to gain a console interface
login here with username and password ( no response when pass word is entered)

now execute terminal command:
```

sudo lshw -C display | nc termbin.com 9999

```
where the result will be a URL back in terminal that points to the generated file. Pass that link back here so we know what we are dealing with.

[INDENT][INDENT]a process in discoivery
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-07
Bashing-om, thanks, I'll try your suggestion.

I've actually made some progress on this issue by myself. I've been able to install a new driver, nvidia-driver-396, and that made a huge improvement to what my laptop monitor looks like, and I can boot without nomodeset. But my external monitor is still black.

---

### Post by RedChili on 2018-09-07
The result of the query was [http://termbin.com/xobu](http://termbin.com/xobu)

---

### Post by RedChili on 2018-09-07
[ATTACH=CONFIG]281012[/ATTACH]

This is what my monitor preferences looks like right now. And nothing happens when I press "detect monitors." The external monitor is connected via HDMI.

---

### Post by Bashing-om on 2018-09-07
jon.andersen; Well - not 

According to the termbin post, you have no driver loaded for the nvidia card.

Show us:
```

echo $XDG_SESSION_TYPE
sudo apt update
sudo apt full-upgrade
lsmod | grep nvidia
dpkg -l | grep -i nvidia

```

see what we can figure out to get the nvidia driver installed.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-07
The xdg-session type gives the reply x11.

I updated earlier today so the updates and upgrades make no change.

The final command gives the following reply:

> ii  libnvidia-cfg1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                  390.87-0ubuntu0~gpu18.04.1            all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                  396.54-0ubuntu0~gpu18.04.1            all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64           390.87-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386            390.87-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-compute-396:amd64           396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386            396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                 396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  mate-optimus                          18.04.0-1                             all          MATE Desktop applet for controlling NVIDIA Optimus graphics cards
rc  nvidia-compute-utils-390              390.87-0ubuntu0~gpu18.04.1            amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                       390.87-0ubuntu0~gpu18.04.1            amd64        NVIDIA DKMS package
ii  nvidia-dkms-396                       396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-396                     396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390              390.87-0ubuntu0~gpu18.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-396              396.54-0ubuntu0~gpu18.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.8                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       396.54-0ubuntu0~gpu18.04.1            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396         396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary Xorg driver

---

### Post by Bashing-om on 2018-09-07
jon.andersen; Uh huh ...

That shows a driver conflict between 390 and 396
This is mate ? as we have:
> 
ii mate-optimus 18.04.0-1 all MATE Desktop applet for controlling NVIDIA Optimus graphics cards


I do not know how mate controls the graphic's :(
All I can suggest at this point is the purge and try and re-install - again it is mate and they do something different that I do not know about.
But try:
```

sudo apt purge nvidia*
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]a know it all I am not
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-08
This is really weird. When I started this thread, I only had 390 installed, and it didn't work at all. I then installed 396, and when I'm checking what drivers I'm using, it appears that it's the 396 (see below).

[ATTACH=CONFIG]281016[/ATTACH]

Moreover, after I made this change, I could boot without nomodeset, and the monitor looks much brighter than before. So I really don't understand what's going on here.

Later today, I'll try to remove the 390 and see what difference that makes.

And, yes, I'm on Ubuntu Mate 18.04.

Thanks for all help!

---

### Post by RedChili on 2018-09-08
I tried doing what you suggested. It didn't help.

So once more, I tried:
1. Purging nvidia
2. autoremove
3. add repository ppa:graphics-drivers/ppa
4. install nvidia-driver-396 only

Now, it basically looks the same as earlier, but the result of dpkg -l | grep -i nvidia is slightly different:

> ii  libnvidia-cfg1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                  396.54-0ubuntu0~gpu18.04.1            all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64           390.87-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386            390.87-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-compute-396:amd64           396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386            396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                 396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  mate-optimus                          18.04.0-1                             all          MATE Desktop applet for controlling NVIDIA Optimus graphics cards
ii  nvidia-compute-utils-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-396                       396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-396                     396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-396              396.54-0ubuntu0~gpu18.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.8                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       396.54-0ubuntu0~gpu18.04.1            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396         396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary Xorg driver


So, how can I remove only the 390 driver and keep the 396?

---

### Post by Bashing-om on 2018-09-08
jon.andersen; Ouch ..

the 390 versions are marked as 'rc' ( removed but config files remain) -- and will have no further effect. We can remove them however if ya want. 396 appears to be fully installed.

Like I advised, I do not know how mate handles Optimus technology .. 
Tomorrow late I will do some research and see what I can learn, In the meantime will be interesting to see:
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```

[INDENT][INDENT]try and understand
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-09
The result of the first is:
> [    38.264] (--) PCI: (0:1:0:0) 10de:1c8d:103c:836b rev 161, Mem @ 0xb3000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    38.264] (II) LoadModule: "glx"
[    38.264] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    38.453] (II) Module glx: vendor="X.Org Foundation"
[    38.453]     compiled for 1.19.6, module version = 1.0.0
[    38.453]     ABI class: X.Org Server Extension, version 10.0
[    38.453] (==) Matched modesetting as autoconfigured driver 0
[    38.453] (==) Matched fbdev as autoconfigured driver 1
[    38.453] (==) Matched vesa as autoconfigured driver 2
[    38.453] (==) Assigned the driver to the xf86ConfigLayout
[    38.453] (II) LoadModule: "modesetting"
[    38.453] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    38.453] (II) Module modesetting: vendor="X.Org Foundation"
[    38.453]     compiled for 1.19.6, module version = 1.19.6
[    38.453]     Module class: X.Org Video Driver
[    38.453]     ABI class: X.Org Video Driver, version 23.0
[    38.453] (II) LoadModule: "fbdev"
[    38.453] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.453] (II) Module fbdev: vendor="X.Org Foundation"
[    38.453]     compiled for 1.19.3, module version = 0.4.4
[    38.453]     Module class: X.Org Video Driver
[    38.453]     ABI class: X.Org Video Driver, version 23.0
[    38.453] (II) LoadModule: "vesa"
[    38.453] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.453] (II) Module vesa: vendor="X.Org Foundation"
[    38.453]     compiled for 1.19.3, module version = 2.3.4
[    38.453]     Module class: X.Org Video Driver
[    38.453]     ABI class: X.Org Video Driver, version 23.0
[    38.453] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    38.453] (II) FBDEV: driver for framebuffer: fbdev
[    38.453] (II) VESA: driver for VESA chipsets: vesa
[    38.466] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[    38.479] (II) modeset(0): using drv /dev/dri/card0
[    38.479] (WW) Falling back to old probe method for fbdev
[    38.479] (II) Loading sub module "fbdevhw"
[    38.480] (II) LoadModule: "fbdevhw"
[    38.480] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.480] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.480]     compiled for 1.19.6, module version = 0.0.2
[    38.480]     ABI class: X.Org Video Driver, version 23.0
[    38.480] (WW) Falling back to old probe method for vesa
[    38.480] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    38.480] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    38.480] (==) modeset(0): RGB weight 888
[    38.480] (==) modeset(0): Default visual is TrueColor
[    38.480] (II) Loading sub module "glamoregl"
[    38.480] (II) LoadModule: "glamoregl"
[    38.480] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    38.645] (II) Module glamoregl: vendor="X.Org Foundation"
[    38.645]     compiled for 1.19.6, module version = 1.0.0
[    38.645]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.645] (II) glamor: OpenGL accelerated X.org driver based.
[    40.836] (II) glamor: EGL version 1.4 (DRI2):
[    40.855] (II) modeset(0): glamor initialized
[    40.856] (II) modeset(0): Output eDP-1 has no monitor section
[    41.224] (II) modeset(0): Output HDMI-1 has no monitor section
[    41.224] (II) modeset(0): Output DP-1 has no monitor section
[    41.225] (II) modeset(0): EDID for output eDP-1
[    41.225] (II) modeset(0): Manufacturer: LGD  Model: 58c  Serial#: 0
[    41.225] (II) modeset(0): Year: 2016  Week: 0
[    41.225] (II) modeset(0): EDID Version: 1.4
[    41.225] (II) modeset(0): Digital Display Input
[    41.225] (II) modeset(0): 6 bits per channel
[    41.225] (II) modeset(0): Digital interface is DisplayPort
[    41.225] (II) modeset(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    41.225] (II) modeset(0): Gamma: 2.20
[    41.225] (II) modeset(0): No DPMS capabilities specified
[    41.225] (II) modeset(0): Supported color encodings: RGB 4:4:4 
[    41.225] (II) modeset(0): First detailed timing is preferred mode
[    41.225] (II) modeset(0): Preferred mode is native pixel format and refresh rate
[    41.225] (II) modeset(0): Display is continuous-frequency
[    41.225] (II) modeset(0): redX: 0.580 redY: 0.350   greenX: 0.340 greenY: 0.560
[    41.225] (II) modeset(0): blueX: 0.155 blueY: 0.125   whiteX: 0.313 whiteY: 0.329
[    41.225] (II) modeset(0): Manufacturer's mask: 0
[    41.225] (II) modeset(0): Supported detailed timing:
[    41.225] (II) modeset(0): clock: 138.7 MHz   Image Size:  344 x 194 mm
[    41.225] (II) modeset(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    41.225] (II) modeset(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    41.225] (II) modeset(0): Supported detailed timing:
[    41.225] (II) modeset(0): clock: 92.5 MHz   Image Size:  344 x 194 mm
[    41.225] (II) modeset(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    41.226] (II) modeset(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    41.226] (II) modeset(0): Ranges: V min: 40 V max: 60 Hz, H min: 67 H max: 67 kHz, PixClock max 145 MHz
[    41.226] (II) modeset(0): Unknown vendor-specific block 2
[    41.226] (II) modeset(0): EDID (in hex):
[    41.226] (II) modeset(0):     00ffffffffffff0030e48c0500000000
[    41.226] (II) modeset(0):     001a01049522137803a1c59459578f27
[    41.226] (II) modeset(0):     20505400000001010101010101010101
[    41.226] (II) modeset(0):     0101010101012e3680a070381f403020
[    41.226] (II) modeset(0):     350058c210000019222480a070381f40
[    41.226] (II) modeset(0):     3020350058c210000019000000fd0028
[    41.226] (II) modeset(0):     3c43430e010a20202020202000000002
[    41.226] (II) modeset(0):     000c47ff0a3c6e1c151f6e00000000bb
[    41.226] (II) modeset(0): Printing probed modes for output eDP-1
[    41.226] (II) modeset(0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    41.226] (II) modeset(0): Modeline "1920x1080"x40.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz e)
[    41.468] (II) modeset(0): EDID for output HDMI-1
[    41.468] (II) modeset(0): EDID for output DP-1
[    41.468] (II) modeset(0): Output eDP-1 connected
[    41.468] (II) modeset(0): Output HDMI-1 disconnected
[    41.468] (II) modeset(0): Output DP-1 disconnected
[    41.468] (II) modeset(0): Using exact sizes for initial modes
[    41.468] (II) modeset(0): Output eDP-1 using initial mode 1920x1080 +0+0
[    41.468] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    41.468] (==) modeset(0): DPI set to (96, 96)
[    41.468] (II) Loading sub module "fb"
[    41.468] (II) LoadModule: "fb"
[    41.468] (II) Loading /usr/lib/xorg/modules/libfb.so
[    41.468] (II) Module fb: vendor="X.Org Foundation"
[    41.468]     compiled for 1.19.6, module version = 1.0.0
[    41.468]     ABI class: X.Org ANSI C Emulation, version 0.4
[    41.468] (II) UnloadModule: "fbdev"
[    41.468] (II) Unloading fbdev
[    41.468] (II) UnloadSubModule: "fbdevhw"
[    41.468] (II) Unloading fbdevhw
[    41.468] (II) UnloadModule: "vesa"
[    41.468] (II) Unloading vesa
[    41.468] (==) Depth 24 pixmap format is 32 bpp
[    42.200] (==) modeset(0): Backing store enabled
[    42.200] (==) modeset(0): Silken mouse enabled
[    42.200] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    42.262] (==) modeset(0): DPMS enabled
[    42.262] (II) modeset(0): [DRI2] Setup complete
[    42.262] (II) modeset(0): [DRI2]   DRI driver: i965
[    42.262] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    42.262] (--) RandR disabled
[    43.443] (II) SELinux: Disabled on system
[    43.467] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    43.467] (II) AIGLX: enabled GLX_ARB_create_context
[    43.467] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    43.467] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    43.467] (II) AIGLX: enabled GLX_INTEL_swap_event
[    43.467] (II) AIGLX: enabled GLX_SGI_swap_control
[    43.467] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    43.467] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    43.467] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    43.467] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    43.467] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    43.468] (II) AIGLX: Loaded and initialized i965
[    43.468] (II) GLX: Initialized DRI2 GL provider for screen 0
[    43.475] (II) modeset(0): Damage tracking initialized
[    43.475] (II) modeset(0): Setting screen physical size to 508 x 285
[    44.623] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    44.623] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    44.623] (II) LoadModule: "libinput"
[    44.623] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    44.900] (II) Module libinput: vendor="X.Org Foundation"
[    44.900]     compiled for 1.19.6, module version = 0.27.1
[    44.900]     Module class: X.Org XInput Driver
[    44.900]     ABI class: X.Org XInput driver, version 24.1
[    44.900] (II) Using input driver 'libinput' for 'Power Button'
[    44.900] (**) Power Button: always reports core events
[    44.900] (**) Option "Device" "/dev/input/event2"
[    44.900] (**) Option "_source" "server/udev"
[    44.901] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    44.901] (II) event2  - Power Button: device is a keyboard
[    44.902] (II) event2  - Power Button: device removed
[    44.928] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    44.928] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    44.928] (**) Option "xkb_model" "pc105"
[    44.928] (**) Option "xkb_layout" "no"
[    44.946] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    44.946] (II) event2  - Power Button: device is a keyboard
[    44.946] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    44.946] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    44.946] (II) Using input driver 'libinput' for 'Video Bus'
[    44.946] (**) Video Bus: always reports core events
[    44.946] (**) Option "Device" "/dev/input/event5"
[    44.946] (**) Option "_source" "server/udev"
[    44.946] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[    44.946] (II) event5  - Video Bus: device is a keyboard
[    44.946] (II) event5  - Video Bus: device removed
[    44.960] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event5"
[    44.960] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    44.960] (**) Option "xkb_model" "pc105"
[    44.960] (**) Option "xkb_layout" "no"
[    44.960] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[    44.960] (II) event5  - Video Bus: device is a keyboard
[    44.960] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    44.960] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    44.960] (II) Using input driver 'libinput' for 'Video Bus'
[    44.960] (**) Video Bus: always reports core events
[    44.960] (**) Option "Device" "/dev/input/event4"
[    44.960] (**) Option "_source" "server/udev"
[    44.961] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    44.961] (II) event4  - Video Bus: device is a keyboard
[    44.961] (II) event4  - Video Bus: device removed
[    44.976] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6/event4"
[    44.976] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    44.976] (**) Option "xkb_model" "pc105"
[    44.976] (**) Option "xkb_layout" "no"
[    44.976] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    44.976] (II) event4  - Video Bus: device is a keyboard
[    44.976] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    44.976] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    44.976] (II) Using input driver 'libinput' for 'Power Button'
[    44.977] (**) Power Button: always reports core events
[    44.977] (**) Option "Device" "/dev/input/event1"
[    44.977] (**) Option "_source" "server/udev"
[    44.977] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    44.977] (II) event1  - Power Button: device is a keyboard
[    44.977] (II) event1  - Power Button: device removed
[    44.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    44.992] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    44.992] (**) Option "xkb_model" "pc105"
[    44.992] (**) Option "xkb_layout" "no"
[    44.992] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    44.993] (II) event1  - Power Button: device is a keyboard
[    44.993] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    44.993] (II) No input driver specified, ignoring this device.
[    44.993] (II) This device may have been added with another device file.
[    44.994] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    44.994] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    44.994] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    44.994] (**) Logitech USB Receiver: always reports core events
[    44.994] (**) Option "Device" "/dev/input/event7"
[    44.994] (**) Option "_source" "server/udev"
[    44.995] (II) event7  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    44.995] (II) event7  - Logitech USB Receiver: device is a keyboard
[    44.995] (II) event7  - Logitech USB Receiver: device removed
[    45.016] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:046D:C534.0001/input/input8/event7"
[    45.016] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    45.016] (**) Option "xkb_model" "pc105"
[    45.016] (**) Option "xkb_layout" "no"
[    45.018] (II) event7  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    45.018] (II) event7  - Logitech USB Receiver: device is a keyboard
[    45.019] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[    45.019] (**) Logitech USB Receiver: Applying InputClass "libinput pointer catchall"
[    45.019] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    45.019] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    45.019] (**) Logitech USB Receiver: always reports core events
[    45.019] (**) Option "Device" "/dev/input/event8"
[    45.019] (**) Option "_source" "server/udev"
[    45.021] (II) event8  - Logitech USB Receiver: is tagged by udev as: Keyboard Mouse
[    45.021] (II) event8  - Logitech USB Receiver: device is a pointer
[    45.021] (II) event8  - Logitech USB Receiver: device is a keyboard
[    45.021] (II) event8  - Logitech USB Receiver: device removed
[    45.044] (II) libinput: Logitech USB Receiver: needs a virtual subdevice
[    45.044] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:046D:C534.0002/input/input9/event8"
[    45.044] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 11)
[    45.044] (**) Option "AccelerationScheme" "none"
[    45.044] (**) Logitech USB Receiver: (accel) selected scheme none/0
[    45.044] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    45.044] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    45.046] (II) event8  - Logitech USB Receiver: is tagged by udev as: Keyboard Mouse
[    45.046] (II) event8  - Logitech USB Receiver: device is a pointer
[    45.046] (II) event8  - Logitech USB Receiver: device is a keyboard
[    45.047] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    45.047] (II) No input driver specified, ignoring this device.
[    45.047] (II) This device may have been added with another device file.
[    45.048] (II) config/udev: Adding input device HP Wide Vision FHD Camera: HP W (/dev/input/event19)
[    45.048] (**) HP Wide Vision FHD Camera: HP W: Applying InputClass "libinput keyboard catchall"
[    45.048] (II) Using input driver 'libinput' for 'HP Wide Vision FHD Camera: HP W'
[    45.048] (**) HP Wide Vision FHD Camera: HP W: always reports core events
[    45.049] (**) Option "Device" "/dev/input/event19"
[    45.049] (**) Option "_source" "server/udev"
[    45.050] (II) event19 - HP Wide Vision FHD Camera: HP W: is tagged by udev as: Keyboard
[    45.050] (II) event19 - HP Wide Vision FHD Camera: HP W: device is a keyboard
[    45.050] (II) event19 - HP Wide Vision FHD Camera: HP W: device removed
[    45.084] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input20/event19"
[    45.084] (II) XINPUT: Adding extended input device "HP Wide Vision FHD Camera: HP W" (type: KEYBOARD, id 12)
[    45.084] (**) Option "xkb_model" "pc105"
[    45.084] (**) Option "xkb_layout" "no"
[    45.085] (II) event19 - HP Wide Vision FHD Camera: HP W: is tagged by udev as: Keyboard
[    45.085] (II) event19 - HP Wide Vision FHD Camera: HP W: device is a keyboard
[    45.087] (II) config/udev: Adding input device HP Wide Vision FHD Camera: HP I (/dev/input/event20)
[    45.087] (**) HP Wide Vision FHD Camera: HP I: Applying InputClass "libinput keyboard catchall"
[    45.087] (II) Using input driver 'libinput' for 'HP Wide Vision FHD Camera: HP I'
[    45.087] (**) HP Wide Vision FHD Camera: HP I: always reports core events
[    45.087] (**) Option "Device" "/dev/input/event20"
[    45.087] (**) Option "_source" "server/udev"
[    45.088] (II) event20 - HP Wide Vision FHD Camera: HP I: is tagged by udev as: Keyboard
[    45.088] (II) event20 - HP Wide Vision FHD Camera: HP I: device is a keyboard
[    45.088] (II) event20 - HP Wide Vision FHD Camera: HP I: device removed
[    45.132] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/input/input21/event20"
[    45.132] (II) XINPUT: Adding extended input device "HP Wide Vision FHD Camera: HP I" (type: KEYBOARD, id 13)
[    45.132] (**) Option "xkb_model" "pc105"
[    45.132] (**) Option "xkb_layout" "no"
[    45.133] (II) event20 - HP Wide Vision FHD Camera: HP I: is tagged by udev as: Keyboard
[    45.133] (II) event20 - HP Wide Vision FHD Camera: HP I: device is a keyboard
[    45.134] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    45.134] (II) No input driver specified, ignoring this device.
[    45.134] (II) This device may have been added with another device file.
[    45.135] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    45.135] (II) No input driver specified, ignoring this device.
[    45.135] (II) This device may have been added with another device file.
[    45.135] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event14)
[    45.135] (II) No input driver specified, ignoring this device.
[    45.135] (II) This device may have been added with another device file.
[    45.136] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event15)
[    45.136] (II) No input driver specified, ignoring this device.
[    45.136] (II) This device may have been added with another device file.
[    45.137] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event16)
[    45.137] (II) No input driver specified, ignoring this device.
[    45.137] (II) This device may have been added with another device file.
[    45.137] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=9 (/dev/input/event17)
[    45.137] (II) No input driver specified, ignoring this device.
[    45.137] (II) This device may have been added with another device file.
[    45.138] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=10 (/dev/input/event18)
[    45.138] (II) No input driver specified, ignoring this device.
[    45.138] (II) This device may have been added with another device file.
[    45.139] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    45.139] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    45.139] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    45.139] (**) AT Translated Set 2 keyboard: always reports core events
[    45.139] (**) Option "Device" "/dev/input/event3"
[    45.139] (**) Option "_source" "server/udev"
[    45.140] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    45.140] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    45.140] (II) event3  - AT Translated Set 2 keyboard: device removed
[    45.160] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    45.160] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    45.160] (**) Option "xkb_model" "pc105"
[    45.160] (**) Option "xkb_layout" "no"
[    45.161] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    45.161] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    45.162] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    45.162] (**) ETPS/2 Elantech Touchpad: Applying InputClass "libinput touchpad catchall"
[    45.162] (II) Using input driver 'libinput' for 'ETPS/2 Elantech Touchpad'
[    45.162] (**) ETPS/2 Elantech Touchpad: always reports core events
[    45.162] (**) Option "Device" "/dev/input/event6"
[    45.162] (**) Option "_source" "server/udev"
[    45.163] (II) event6  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[    45.163] (II) event6  - ETPS/2 Elantech Touchpad: device is a touchpad
[    45.163] (II) event6  - ETPS/2 Elantech Touchpad: device removed
[    45.192] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[    45.192] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[    45.192] (**) Option "AccelerationScheme" "none"
[    45.192] (**) ETPS/2 Elantech Touchpad: (accel) selected scheme none/0
[    45.192] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    45.192] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    45.193] (II) event6  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[    45.193] (II) event6  - ETPS/2 Elantech Touchpad: device is a touchpad
[    45.194] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    45.194] (II) No input driver specified, ignoring this device.
[    45.194] (II) This device may have been added with another device file.
[    45.195] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event10)
[    45.195] (II) No input driver specified, ignoring this device.
[    45.195] (II) This device may have been added with another device file.
[    45.195] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    45.195] (II) No input driver specified, ignoring this device.
[    45.195] (II) This device may have been added with another device file.
[    45.200] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event9)
[    45.200] (**) HP Wireless hotkeys: Applying InputClass "libinput keyboard catchall"
[    45.200] (II) Using input driver 'libinput' for 'HP Wireless hotkeys'
[    45.200] (**) HP Wireless hotkeys: always reports core events
[    45.200] (**) Option "Device" "/dev/input/event9"
[    45.200] (**) Option "_source" "server/udev"
[    45.200] (II) event9  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[    45.200] (II) event9  - HP Wireless hotkeys: device is a keyboard
[    45.201] (II) event9  - HP Wireless hotkeys: device removed
[    45.240] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    45.240] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 16)
[    45.240] (**) Option "xkb_model" "pc105"
[    45.240] (**) Option "xkb_layout" "no"
[    45.241] (II) event9  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[    45.241] (II) event9  - HP Wireless hotkeys: device is a keyboard
[    45.242] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event11)
[    45.242] (**) HP WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    45.242] (II) Using input driver 'libinput' for 'HP WMI hotkeys'
[    45.242] (**) HP WMI hotkeys: always reports core events
[    45.242] (**) Option "Device" "/dev/input/event11"
[    45.242] (**) Option "_source" "server/udev"
[    45.243] (II) event11 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[    45.243] (II) event11 - HP WMI hotkeys: device is a keyboard
[    45.243] (II) event11 - HP WMI hotkeys: device removed
[    45.256] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event11"
[    45.256] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 17)
[    45.256] (**) Option "xkb_model" "pc105"
[    45.256] (**) Option "xkb_layout" "no"
[    45.257] (II) event11 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[    45.257] (II) event11 - HP WMI hotkeys: device is a keyboard
[    45.278] (**) Logitech USB Receiver: Applying InputClass "libinput pointer catchall"
[    45.278] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    45.278] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    45.278] (**) Logitech USB Receiver: always reports core events
[    45.278] (**) Option "Device" "/dev/input/event8"
[    45.278] (**) Option "_source" "_driver/libinput"
[    45.278] (II) libinput: Logitech USB Receiver: is a virtual subdevice
[    45.278] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:046D:C534.0002/input/input9/event8"
[    45.278] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 18)
[    45.278] (**) Option "xkb_model" "pc105"
[    45.278] (**) Option "xkb_layout" "no"
[    63.763] (II) modeset(0): EDID vendor "LGD", prod id 1420
[    63.763] (II) modeset(0): Using EDID range info for horizontal sync
[    63.763] (II) modeset(0): Using EDID range info for vertical refresh
[    63.763] (II) modeset(0): Printing DDC gathered Modelines:
[    63.763] (II) modeset(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    63.763] (II) modeset(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz e)
[    64.011] (II) modeset(0): EDID vendor "LGD", prod id 1420
[    64.011] (II) modeset(0): Using hsync ranges from config file
[    64.011] (II) modeset(0): Using vrefresh ranges from config file
[    64.011] (II) modeset(0): Printing DDC gathered Modelines:
[    64.011] (II) modeset(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    64.012] (II) modeset(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz e)
[    64.303] (II) modeset(0): EDID vendor "LGD", prod id 1420
[    64.303] (II) modeset(0): Using hsync ranges from config file
[    64.303] (II) modeset(0): Using vrefresh ranges from config file
[    64.303] (II) modeset(0): Printing DDC gathered Modelines:
[    64.303] (II) modeset(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    64.303] (II) modeset(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz e)
[    65.489] (II) modeset(0): EDID vendor "LGD", prod id 1420
[    65.489] (II) modeset(0): Using hsync ranges from config file
[    65.489] (II) modeset(0): Using vrefresh ranges from config file
[    65.489] (II) modeset(0): Printing DDC gathered Modelines:
[    65.489] (II) modeset(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    65.489] (II) modeset(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz e)

The result of the second is:
> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-33-generic/updates/dkms
Found nvidia module: nvidia-modeset.ko
Looking for amdgpu modules in /lib/modules/4.15.0-33-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 0
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
The number of cards has changed!
Has the system changed? Yes
System configuration has changed
Single card detected
Nothing to do



---

### Post by RedChili on 2018-09-13
Bashing-om, do you have any idea how I can fix this?

---

### Post by Bashing-om on 2018-09-13
RedChili; well ..


> **RedChili said:**
> Bashing-om, do you have any idea how I can fix this?

Not really .. I can not keep up with what you are doing .. and again I do not know mate.

This now makes little sense:
> 
Is nvidia loaded? no
Is nvidia kernel module available? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
How many cards? 1
The number of cards has changed!
Has the system changed? Yes
System configuration has changed

is the nvidia card turned off now in bios ?

show us a new:
```

lspci -k|grep -iEA5 'vga|3d' 
lsmod | grep nvidia
dpkg -l | grep nvidia
sudo lshw -C display

```

[INDENT][INDENT]see what we can finger out here
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-13
When I ented the bios setup, I can't find any info about the video card at all. I don't know why.

The result of the first command:
> 00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
    Subsystem: Hewlett-Packard Company Device 836b
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 05)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
--
01:00.0 VGA compatible controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)
    Subsystem: Hewlett-Packard Company GP107M [GeForce GTX 1050 Mobile]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company RTS522A PCI Express Card Reader
    Kernel driver in use: rtsx_pci



The third command:
> ii  libnvidia-cfg1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                  396.54-0ubuntu0~gpu18.04.1            all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-396:amd64           396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386            396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64            396.54-0ubuntu0~gpu18.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386             396.54-0ubuntu0~gpu18.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                 396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386               396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-396                       396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-396                     396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-396              396.54-0ubuntu0~gpu18.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.8                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       396.54-0ubuntu0~gpu18.04.1            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396         396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary Xorg driver



The fourth:
>   *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107M [GeForce GTX 1050 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:131 memory:b2000000-b2ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff



---

### Post by Bashing-om on 2018-09-13
RedChili; Hummm ..

Still the Nvidia driver does not load .

what about that 2nd command " lsmod | grep nvidia" ?
Maybe we can get some useful info from 'modprobe' ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2018-09-13
RedChili; 'Nother thought :)

In addition to my last; "nomodeset" - is it still set ? As that will prevent the Nvidia driver loading.
What shows:
```

cat /proc/cmdline

```

[INDENT][INDENT]seek, and look - I guess
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-14
Nothing happens when I type "lsmod | grep nvidia"

When I seemingly managed to install Nvidia 396, I removed nomodeset. When I did that, I got a much clearer screen. Also, when I enter the Control Center and Monitor Preferences, I can now choose refresh rate of 60/40 Hz, and rotation. I wasn't able to choose those when I still had nomodeset. But I can't change the resolution. It's stuck at 1920x1080.

cat /proc/cmdline gives:
> BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=67f0ba97-2bf7-4ed3-b6e1-1ef5d697d946 ro quiet splash vt.handoff=1



---

### Post by RedChili on 2018-09-14
Result of the lsmod | grep nvidia:

> ~$ lsmod | grep nvidia
~$ 


---

### Post by RedChili on 2018-09-14
By the way, when searching the net, I found the following possible explanation for my problems:

> Purge lowlatency kernel and reboot

  Interestingly, several people have found that the upgrade process automatically installs a lowlatency kernel (a kernel variant that isn&#8217;t typically used on desktop systems). List these with the following apt command and look for ones that are installed: apt search '^linux-(headers|image)-.*-.*-lowlatency*'. Remove these with sudo apt autoremove {package-name-here} - or just sudo apt autoremove --purge '^linux-(headers|image)-.*-.*-lowlatency*'. Make sure that the latest generic kernel image and headers are installed instead.



When I did the search, I indeed found that I had lots of lowlatency kernels installed:

> Sorting... Done
Full Text Search... Done
linux-headers-4.15.0-20-lowlatency/bionic 4.15.0-20.21 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-22-lowlatency/bionic-updates,bionic-security 4.15.0-22.24 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-23-lowlatency/bionic-updates,bionic-security 4.15.0-23.25 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-24-lowlatency/bionic-updates,bionic-security 4.15.0-24.26 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-29-lowlatency/bionic-updates,bionic-security 4.15.0-29.31 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-30-lowlatency/bionic-updates,bionic-security 4.15.0-30.32 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-32-lowlatency/bionic-updates,bionic-security 4.15.0-32.35 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-33-lowlatency/bionic-updates,bionic-security 4.15.0-33.36 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-headers-4.15.0-34-lowlatency/bionic-updates,bionic-security 4.15.0-34.37 amd64
  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP

linux-image-4.15.0-20-lowlatency/bionic 4.15.0-20.21 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-22-lowlatency/bionic-updates,bionic-security 4.15.0-22.24 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-23-lowlatency/bionic-updates,bionic-security 4.15.0-23.25 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-24-lowlatency/bionic-updates,bionic-security 4.15.0-24.26 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-29-lowlatency/bionic-updates,bionic-security 4.15.0-29.31 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-30-lowlatency/bionic-updates,bionic-security 4.15.0-30.32 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-32-lowlatency/bionic-updates,bionic-security 4.15.0-32.35 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-33-lowlatency/bionic-updates,bionic-security 4.15.0-33.36 amd64
  Signed kernel image lowlatency

linux-image-4.15.0-34-lowlatency/bionic-updates,bionic-security 4.15.0-34.37 amd64
  Signed kernel image lowlatency

linux-image-unsigned-4.15.0-20-lowlatency/bionic 4.15.0-20.21 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-22-lowlatency/bionic-updates,bionic-security 4.15.0-22.24 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-23-lowlatency/bionic-updates,bionic-security 4.15.0-23.25 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-24-lowlatency/bionic-updates,bionic-security 4.15.0-24.26 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-29-lowlatency/bionic-updates,bionic-security 4.15.0-29.31 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-30-lowlatency/bionic-updates,bionic-security 4.15.0-30.32 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-32-lowlatency/bionic-updates,bionic-security 4.15.0-32.35 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-33-lowlatency/bionic-updates,bionic-security 4.15.0-33.36 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

linux-image-unsigned-4.15.0-34-lowlatency/bionic-updates,bionic-security 4.15.0-34.37 amd64
  Linux kernel image for version 4.15.0 on 64 bit x86 SMP

I also ran uname -mrs to find out which kernel I'm running, and the reply was:
> Linux 4.15.0-34-generic x86_64

So, would it be safe for me to purge these lowlatency kernels? Maybe that would solve my problem?

---

### Post by Bashing-om on 2018-09-14
RedChili; Humm ...

Sure looks likely that the lowlatency kernel is a factor.
Let's look at the broad picture of kernels :
```

dpkg -l | grep linux-

```

[INDENT][INDENT]lowlatency - as I live and learn
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-14
dpkg -l | grep linux- produces:

> ii  binutils-x86-64-linux-gnu             2.30-20ubuntu2~18.04                  amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                            all          Linux image base package
ii  linux-firmware                        1.173.1                               all          Firmware for Linux kernel drivers
ii  linux-generic                         4.15.0.34.36                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-33               4.15.0-33.36                          all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic       4.15.0-33.36                          amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-34               4.15.0-34.37                          all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-34-generic       4.15.0-34.37                          amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.34.36                          amd64        Generic Linux kernel headers
rc  linux-image-4.15.0-20-generic         4.15.0-20.21                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-29-generic         4.15.0-29.31                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-33-generic         4.15.0-33.36                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-34-generic         4.15.0-34.37                          amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.34.36                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-34.37                          amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-20-generic       4.15.0-20.21                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-29-generic       4.15.0-29.31                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-33-generic       4.15.0-33.36                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-34-generic       4.15.0-34.37                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-20-generic 4.15.0-20.21                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-29-generic 4.15.0-29.31                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-33-generic 4.15.0-33.36                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-34-generic 4.15.0-34.37                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                  4.15.0.34.36                          amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5                  all          base package for ALSA and OSS sound systems
ii  syslinux-common                       3:6.03+dfsg1-2                        all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu9                  amd64        Bootloader for Linux/i386 using MS-DOS floppies


---

### Post by Bashing-om on 2018-09-15
RedChili; hummmmm .....

That looks fairly sane .. but, :
> 
ii linux-libc-dev:amd64 4.15.0-34.37 amd64 Linux Kernel Headers for development

what in the world are you developing that you need this kernel set ?

And how about removing the cruft (marked rc ):
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed...

[INDENT][INDENT]see what we can do next
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-16
I have no idea why the development kernel is there. I just made a standard 18.04 Mate installation.

So, I applied the code that you instructed, and after restart the result of dpkg -l | grep linux- is:

> ii  binutils-x86-64-linux-gnu             2.30-20ubuntu2~18.04                  amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                            all          Linux image base package
ii  linux-firmware                        1.173.1                               all          Firmware for Linux kernel drivers
ii  linux-generic                         4.15.0.34.36                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-33               4.15.0-33.36                          all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic       4.15.0-33.36                          amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-34               4.15.0-34.37                          all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-34-generic       4.15.0-34.37                          amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.34.36                          amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-33-generic         4.15.0-33.36                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-34-generic         4.15.0-34.37                          amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.34.36                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-34.37                          amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-33-generic       4.15.0-33.36                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-34-generic       4.15.0-34.37                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-33-generic 4.15.0-33.36                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-34-generic 4.15.0-34.37                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                  4.15.0.34.36                          amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5                  all          base package for ALSA and OSS sound systems
ii  syslinux-common                       3:6.03+dfsg1-2                        all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu9                  amd64        Bootloader for Linux/i386 using MS-DOS floppies



---

### Post by Bashing-om on 2018-09-18
RedChili; Hey - hey .

What is the status ? I have not forgotten nor are you in ignore :)
Just that I am not certain how to proceed in this situation.

> 
sysop@x1810:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 710]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:26 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:c0000-dffff
sysop@x1810:~$ 

sysop@x1810:~$ ls -al /etc/X11/Xorg.conf
ls: cannot access '/etc/X11/Xorg.conf': No such file or directory
sysop@x1810:~$ 

sysop@x1810:~$ ls -al /usr/share/X11/xorg.conf.d/
total 40
drwxr-xr-x 2 root root 4096 Sep 18 11:34 .
drwxr-xr-x 5 root root 4096 Aug 28 19:05 ..
-rw-r--r-- 1 root root   92 May 23 01:55 10-amdgpu.conf
-rw-r--r-- 1 root root  206 Aug 28 01:49 10-nvidia.conf
-rw-r--r-- 1 root root 1350 Sep  5 06:13 10-quirks.conf
-rw-r--r-- 1 root root   92 Aug 20 02:19 10-radeon.conf
-rw-r--r-- 1 root root  945 Aug 17 07:04 40-libinput.conf
-rw-r--r-- 1 root root  590 Aug 24 06:29 51-synaptics-quirks.conf
-rw-r--r-- 1 root root 1751 Aug 24 06:29 70-synaptics.conf
-rw-r--r-- 1 root root 3025 Apr  3 02:39 70-wacom.conf
sysop@x1810:~$ 

sysop@x1810:~$ lsmod | grep nvidia
nvidia_uvm            786432  0
nvidia_drm             40960  2
nvidia_modeset       1110016  3 nvidia_drm
nvidia              14368768  84 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
drm                   458752  5 drm_kms_helper,nvidia_drm
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
sysop@x1810:~$ 

sysop@x1810:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                  390.87-0ubuntu1                       all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64           390.87-0ubuntu1                       amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386            390.87-0ubuntu1                       i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64            390.87-0ubuntu1                       amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386             390.87-0ubuntu1                       i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64            390.87-0ubuntu1                       amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386             390.87-0ubuntu1                       i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386               390.87-0ubuntu1                       i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                390.87-0ubuntu1                       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                 390.87-0ubuntu1                       i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386               390.87-0ubuntu1                       i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390              390.87-0ubuntu1                       amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                       390.87-0ubuntu1                       amd64        NVIDIA DKMS package
ii  nvidia-driver-390                     390.87-0ubuntu1                       amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390              390.87-0ubuntu1                       amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390              390.87-0ubuntu1                       amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.9                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       390.77-0ubuntu1                       amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                      390.87-0ubuntu1                       amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390         390.87-0ubuntu1                       amd64        NVIDIA binary Xorg driver
sysop@x1810:~$ 

sysop@x1810:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.18.0-7-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/4.18.0-7-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:128b
BusID "PCI:6@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do
sysop@x1810:~$ 

sysop@x1810:~$ sudo dkms status
nvidia, 390.87, 4.17.0-9-generic, x86_64: installed
nvidia, 390.87, 4.18.0-7-generic, x86_64: installed
sysop@x1810:~$ 


are your outputs similar ?


[INDENT][INDENT]find a way to proceed
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-18
The result of sudo lshw -C display is
>   *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107M [GeForce GTX 1050 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:131 memory:b2000000-b2ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff

ls -al /etc/X11/Xorg.conf is the same as yours.

ls -al /usr/share/X11/xorg.conf.d/:
> total 32
drwxr-xr-x 2 root root 4096 sep.   8 19:23 .
drwxr-xr-x 5 root root 4096 sep.   7 21:53 ..
-rw-r--r-- 1 root root   92 mars  20 13:02 10-amdgpu.conf
-rw-r--r-- 1 root root  206 aug.  21 20:16 10-nvidia.conf
-rw-r--r-- 1 root root 1350 april 13 17:31 10-quirks.conf
-rw-r--r-- 1 root root   92 mars  20 13:17 10-radeon.conf
-rw-r--r-- 1 root root  945 april 11 09:50 40-libinput.conf
-rw-r--r-- 1 root root 3025 april  3 09:39 70-wacom.conf

lsmod | grep nvidia returns nothing at all.

dpkg -l | grep -i nvidia:
> ii  libnvidia-cfg1-396:amd64                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                          396.54-0ubuntu0~gpu18.04.1            all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-396:amd64                   396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                    396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64                    396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386                     396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64                    396.54-0ubuntu0~gpu18.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386                     396.54-0ubuntu0~gpu18.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386                       396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                        396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                         396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386                       396.54-0ubuntu0~gpu18.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  mate-optimus                                  18.04.0-1                             all          MATE Desktop applet for controlling NVIDIA Optimus graphics cards
ii  nvidia-compute-utils-396                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-396                               396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-396                             396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-396                      396.54-0ubuntu0~gpu18.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396                      396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.8                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               396.54-0ubuntu0~gpu18.04.1            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                              396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396                 396.54-0ubuntu0~gpu18.04.1            amd64        NVIDIA binary Xorg driver

cat /var/log/gpu-manager.log:
> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-34-generic/updates/dkms
Found nvidia module: nvidia-modeset.ko
Looking for amdgpu modules in /lib/modules/4.15.0-34-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

sudo dkms status:
> nvidia, 396.54, 4.15.0-33-generic, x86_64: installed
nvidia, 396.54, 4.15.0-34-generic, x86_64: installed

---

### Post by Bashing-om on 2018-09-18
RedChili' Well - not .

we have no driver loaded ( as we knew ) - still :
> 
*-display UNCLAIMED >> product: GP107M [GeForce GTX 1050 Mobile]


And nouveau fails to be blacklisted:
> 
Is nouveau blacklisted? no

So, what are we looking at for blacklisting ?
show:
```

ls -al /etc/modprobe.d/
ls -al /lib/modprobe.d
cat /etc/modprobe.d/blacklist.conf
cat /proc/cmdline

```

As we try and figure out what is not going on.

[INDENT][INDENT]the system has a failure to communicate ? 
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-18
ls -al /etc/modprobe.d/:
> total 60
drwxr-xr-x   2 root root  4096 sep.   8 19:23 .
drwxr-xr-x 146 root root 12288 sep.  17 23:37 ..
-rw-r--r--   1 root root  2507 juli  31  2015 alsa-base.conf
-rw-r--r--   1 root root   154 mai   30 00:16 amd64-microcode-blacklist.conf
-rw-r--r--   1 root root   325 jan.  28  2018 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 jan.  28  2018 blacklist.conf
-rw-r--r--   1 root root   210 jan.  28  2018 blacklist-firewire.conf
-rw-r--r--   1 root root   697 jan.  28  2018 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 juli  31  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 juli  23 17:43 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 jan.  28  2018 blacklist-rare-network.conf
-rw-r--r--   1 root root   127 feb.   7  2017 dkms.conf
-rw-r--r--   1 root root   154 mai    3 21:45 intel-microcode-blacklist.conf
-rw-r--r--   1 root root   347 jan.  28  2018 iwlwifi.conf

ls -al /lib/modprobe.d:
> total 32
drwxr-xr-x  2 root root 4096 sep.  11 16:03 .
drwxr-xr-x 22 root root 4096 sep.   4 21:10 ..
-rw-r--r--  1 root root  655 jan.  28  2018 aliases.conf
-rw-r--r--  1 root root 1461 aug.  15 14:50 blacklist_linux_4.15.0-33-generic.conf
-rw-r--r--  1 root root 1461 aug.  27 16:45 blacklist_linux_4.15.0-34-generic.conf
-rw-r--r--  1 root root  390 juni  22 14:55 fbdev-blacklist.conf
-rw-r--r--  1 root root   81 aug.  21 20:16 nvidia-graphics-drivers.conf
-rw-r--r--  1 root root  765 jan.  28  2018 systemd.conf

cat /etc/modprobe.d/blacklist.conf:
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

cat /proc/cmdline:
> BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=67f0ba97-2bf7-4ed3-b6e1-1ef5d697d946 ro quiet splash vt.handoff=1

---

### Post by Bashing-om on 2018-09-18
RedChili; Hummmm ...

I see nothing obvious in those - but, let me get a few irons out of the fire and boot back into the Nvidia install bare metal, See what differences there may be. Find where nouveau is blacklisted.


[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-18
Okay, what do you mean "boot back into the Nvidia install bare metal"?

---

### Post by Bashing-om on 2018-09-18
RedChili; --

Presently I am booting 18.04 and nouveau is the driver, I do have the proprietary driver installed to 18.10 .. and rather than change root to 18.10 ..in this case I prefer  to boot into 18.10 (bare metal vice a virtual machine ) .

We need to know why nouveau in your case is not blacklisted .

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2018-09-19
RedChili;Welp //

Just a bit smarter this morning :)
There are differences between 18.04 and 18.10 - that I do not see in your 18.04 install - , however, I do think this is doable.
Follow this tutorial to blacklist nouveau:
[https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux)

Reboot and see what happens ... If you boot to a usable GUI now let's try and re-install the nvidia driver:
```

sudo apt update
sudo apt upgrade
sudo apt install --reinstall nvidia-driver-396

```

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-19
So, I followed the tutorial and got the required results.

I also followed your instructions, with the exception of reinstalling "nvidia-driver-396" (singular, not plural).

But the problem still persists.

---

### Post by Bashing-om on 2018-09-19
RedChili; Yuk -


Any errors or advisements reported in any of the steps ?
Formerly we had:
> 
lsmod | grep nvidia returns nothing at all.

where we know the driver is available .. so what we want to do is complete the nvidia driver install. I had anticipated that " sudo apt install --reinstall nvidia-driver-396" would complete that install, and that with nouveau blacklisted there then would be no driver conflict.

[INDENT][INDENT]I still just do not know
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-19
I had some errors for sudo apt update:

```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [3&#8239;302 B]                 
Hit:3 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:4 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:5 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83,2 kB]    
Get:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1&#8239;189 B]           
Hit:8 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease    
Ign:9 [http://ppa.launchpad.net/hplip-isv/ppa/ubuntu](http://ppa.launchpad.net/hplip-isv/ppa/ubuntu) bionic InRelease           
Get:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]        
Err:11 [http://ppa.launchpad.net/hplip-isv/ppa/ubuntu](http://ppa.launchpad.net/hplip-isv/ppa/ubuntu) bionic Release            
  404  Not Found [IP: 91.189.95.83 80]
Err:2 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
Get:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1&#8239;400 B]
Reading package lists... Done                                       
E: The repository 'http://ppa.launchpad.net/hplip-isv/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
E: The repository 'http://repository.spotify.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by oldos2er on 2018-09-19
[http://ppa.launchpad.net/hplip-isv/ppa/ubuntu](http://ppa.launchpad.net/hplip-isv/ppa/ubuntu) hasn't been maintained since 2011, time to remove it.

You can get your missing PUBKEY with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A87FF9DF48BF1C90
```

---

### Post by RedChili on 2018-09-20
Done and done.

---

### Post by oldos2er on 2018-09-20
Great!  Would you please mark your thread 'Solved' under Thread Tools at the top of the page?  Thanks.

---

### Post by RedChili on 2018-09-20
Well, it's not solved yet. I still have the same problem.

---

### Post by Bashing-om on 2018-09-20
RedChili; Yukkie on me -

> **RedChili said:**
> Well, it's not solved yet. I still have the same problem.

Sorry, I am out of ideas to address your issue . It is above my skill set to know why the modules do not install.

[INDENT][INDENT]A know-it-all I am not
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-20
Bashing-om, thank you very much for all your help. I'll just continue to search the net to see if I can find some solution that will help me.

---

### Post by Bashing-om on 2018-09-20
RedChili; K -

I will be very interested in learning. please keep us updated on what you find.

[INDENT][INDENT]there has to be a reason
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-20
By the way, do you think that everything would be sorted out if I installed the regular Ubuntu instead of Mate? I really need to get this to work, so I want to find the simplest solution to the problem.

---

### Post by Bashing-om on 2018-09-20
RedChili; Uh Huh ..

A re-install stands the chance of being the fastest resolution .
Be aware that in optimus there is a lot of work that has been done .. and Alberto has a call out for help.
[http://albertomilone.com/blog/?p=670](http://albertomilone.com/blog/?p=670)

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by RedChili on 2018-09-21
I'll try to install the regular Ubuntu then. Could I install it alongside Mate, or do I have to format the hard drive before installing regular Ubuntu?

---

### Post by Bashing-om on 2018-09-21
RedChilil Sure !

One can easily dual boot ...

My current multu-boot - 3 drives are not connected:
> 
sysop@x1804mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="x1604" UUID="d9c2a8e6-d014-42a6-846f-7e7892f4aef5" TYPE="ext4" PARTUUID="b6a9f0ca-01"
/dev/sda5: UUID="8d4743bc-8e47-4650-b5fd-1ea904d4ecda" TYPE="swap" PARTUUID="b6a9f0ca-05"
/dev/sda6: LABEL="x1810" UUID="49de038e-9807-469b-9009-540f2989f913" TYPE="ext4" PARTUUID="b6a9f0ca-06"
/dev/sdb1: LABEL="x1804root" UUID="1460de17-30e4-4566-b181-18c17b62887a" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sdb2: LABEL="x1804home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sdb3: LABEL="x1804var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sdb5: LABEL="u1804" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sdb6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sdb7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" TYPE="ext4" PARTUUID="c6c4079f-07"
sysop@x1804mini:~$ sudo fdisk -lu
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb6a9f0ca

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 290818047 290816000 138.7G 83 Linux
/dev/sda2       290820094 488396799 197576706  94.2G  5 Extended
/dev/sda5       290820096 300036095   9216000   4.4G 82 Linux swap / S
/dev/sda6       300038144 488396799 188358656  89.8G 83 Linux


Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc6c4079f

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048  16386047  16384000  7.8G 83 Linux
/dev/sdb2        16386048  36866047  20480000  9.8G 83 Linux
/dev/sdb3        36866048  49154047  12288000  5.9G 83 Linux
/dev/sdb4        49154048 172034047 122880000 58.6G  5 Extended
/dev/sdb5        49156096 110596095  61440000 29.3G 83 Linux
/dev/sdb6       110598144 131078143  20480000  9.8G 83 Linux
/dev/sdb7       131080192 151560191  20480000  9.8G 83 Linux
sysop@x1804mini:~$ 


A bit of thought is in order here - the easiest method is to choose "install along side" and let the installer do it's thing.

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

