---
title: "Slow 2D on Dell E6500 (Intel GMA 4500HD)"
date: 2008-12-15
forum: Hardware
---

### Post by mathias_sundman on 2008-12-15
I just got a new laptop, a Dell E6500 with Intel GMA 4500HD graphics and the 1920x1280 display and have installed Ubuntu 8.10 on it.

It worked fine out of the box, got the full 1920x1280 resolution and glx rendering seems to enabled.

However the video performance is horrible. I've searched the archives and found a lot of threads about bad 3D performance. Of cource, getting good 3D performance would be nice aswell, however, right now I'm more concerned with getting basic 2D graphics working well.

For example switching between virtual desktops takes about 1-2 seconds to redraw the other desktop, and if I'm listening to mp3 music at the same time, it sometimes gets interrupted while redrawing the screen!

Even moving windows on the desktop takes time to redraw.

On my 4 years old laptop, a Dell C610, tasks like that were done INSTANT, without a glitch. So it's very annoying getting a brand new laptop and the experience is like going to a 10 years old one!

I've tried installing the latest intel drivers 2.5.1 and installed the latest libdrm/libdrm2, mesa-dri, mesa-glx GIT packages from 20081014 without getting any better performance.

I'm currently stuck, where should I continue looking?

My Xorg.conf is the default:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

And here is sniplet of the Xorg log:
```

Current Operating System: Linux mathias-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
...
(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6c00000/0, 0xe0000000/0, I/O @ 0x0000ef98/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6b00000/0
...
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.5.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Mobile Intel® GM45 Express Chipset
(--) intel(0): Chipset: "Mobile Intel® GM45 Express Chipset"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF6C00000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 21571
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video1
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): Output HDMI-1 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_B" initialized.
(II) intel(0): HDMI output 1 detected
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output HDMI-2 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_C" initialized.
(II) intel(0): HDMI output 2 detected
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "SEC", prod id 21571
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output HDMI-1 disconnected
(II) intel(0): Output HDMI-2 disconnected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1920x1200
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 32764 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.4.0
        ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Kernel reported 865536 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 3462140 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xf6c00000
(II) intel(0): [drm] ring buffer = 0xe0000000
(II) intel(0): [drm] mapped front buffer at 0xe0300000, handle = 0xe0300000
(II) intel(0): [drm] mapped back buffer at 0xe3b41000, handle = 0xe3b41000
(II) intel(0): [drm] mapped depth buffer at 0xe4951000, handle = 0xe4951000
(II) intel(0): [drm] mapped classic textures at 0xe5761000, handle = 0xe5761000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Disable render standby.
(II) EXA(0): Offscreen pixmap area of 44236800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fff000 (pgoffset 8191)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x03b40000 (pgoffset 15168)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x03b41000 (pgoffset 15169)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x04951000 (pgoffset 18769)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x05761000 (pgoffset 22369)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00100fff: compressed frame buffer (900 kB, 0x00000000de020000 physical
(II) intel(0): 0x00101000-0x0010afff: HW cursors (40 kB)
(II) intel(0): 0x0010b000-0x00112fff: logical 3D context (32 kB)
(II) intel(0): 0x00113000-0x00212fff: fake bufmgr (1024 kB)
(II) intel(0): 0x00213000-0x00228fff: exa G965 state buffer (88 kB)
(II) intel(0): 0x00229000-0x00229fff: power context (4 kB)
(II) intel(0): 0x00300000-0x0110ffff: front buffer (14400 kB) X tiled
(II) intel(0): 0x01110000-0x03b3ffff: exa offscreen (43200 kB)
(II) intel(0): 0x01fff000:            end of stolen memory
(II) intel(0): 0x03b40000-0x03b40fff: HW status (4 kB)
(II) intel(0): 0x03b41000-0x04950fff: back buffer (14400 kB) X tiled
(II) intel(0): 0x04951000-0x05760fff: depth buffer (14400 kB) Y tiled
(II) intel(0): 0x05761000-0x07760fff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output HDMI-1 is connected to pipe none
(II) intel(0):   Output HDMI-2 is connected to pipe none
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207


```

```

root@mathias-laptop:/home/mathias# glxinfo | grep rend
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2


```

glxgears gives about 200 FPS.

Any pointers?

---

### Post by mathias_sundman on 2008-12-15
I just found out that changing AccelMethod i Xorg.conf from EAX to XAA gave me much better 2D performance.

With EAX:

```

x11perf --aa10text
Sync time adjustment is 0.2607 msecs.

 160000 reps @   0.0473 msec ( 21100.0/sec): Char in 80-char aa line (Charter 10)
 160000 reps @   0.0457 msec ( 21900.0/sec): Char in 80-char aa line (Charter 10)

```

With XAA:

```

x11perf --aa10text
Sync time adjustment is 0.1854 msecs.

1600000 reps @   0.0052 msec (191000.0/sec): Char in 80-char aa line (Charter 10)
1600000 reps @   0.0049 msec (204000.0/sec): Char in 80-char aa line (Charter 10)

```

It's about a 10 times boost. Desktop switching and moving windows is now much smoother.

The Audio interruption problem persists though.

I'll now try installing Jaunty-Alpha1 and Fedora Core 10 to see if that gives any better performance. Some posts indicate that these distributions include a 2.6.28 kernel which should have some improvments on this area.

Damn, seems like the audio interuption problem has accually gotten worse :( It's interupting all the time now while I'm just typing.

---

### Post by mathias_sundman on 2008-12-15
I installed Jaunty Alpha-1, but got the same results as above. However alot of xorg related packages were kept back from beeing upgraded with apt-get upgrade. After a forced update of all kept back packages I was unable to get X running at all. Didn't spend more time investigating it, instead I moved on and tried installing Fedora Core 10.

Guess what? Out of the box it worked great!

x11perf --aa10text gave about 150000/sec with EAX Accel, which only gave me about 22000/sec on my ubuntu system.

But the big surprise what that 3D also worked much better. glxgears gave 1200 FPS!

And this was with a default Fedora Core 10 system running a 2.6.27 kernel. There should be a 2.6.28 kernel available for Fedora but I wasn't able to just yum install it. I'll continue investigate that tomorrow.

The big question now is what is it with the Fedora system running Linux kernel 2.6.27 and xf86-video-intel 2.5.0 that makes it work so much better than my ubuntu system running the same kernel and even the intel v2.5.1 driver.

---

### Post by mathias_sundman on 2008-12-16
Okay, I give up! I've just spent half a day trying out the latest and greatest libdrm, libdrm2, libdrm-intel1, libdl1-mesa-dri, libgl1-mesa-glx,  xserver-xorg-video-intel git-packages from xorg-edgers, but I was unable to get any of the newer builds running at all on my ubuntu 8.10 system. I assume they depend on a 2.6.28 kernel with GEM and modesetting support or something.

Anyway I ended up reverting to:

xserver-xorg-video-intel_2.5.1~git20081113_i386.deb
libdrm2_2.4.0~git20081014.d9c2f65d-0ubuntu0tormod1_i386.deb
libdrm-dev_2.4.0~git20081014.d9c2f65d-0ubuntu0tormod1_i386.deb
libgl1-mesa-dri_7.2~git20081014+mesa-7-2-branch.ecab8131-0ubuntu0tormod_i386.deb
libgl1-mesa-glx_7.2~git20081014+mesa-7-2-branch.ecab8131-0ubuntu0tormod_i386.deb

They were the latest packages I was able to get up and running. With these packages installed and AccelMethod XAA, I atleast have decent 2D graphics. However the sound interruptions still persist, and 3D graphics is still horrible.

I feel kinda stuck now.

My theory is that that the kernel part of DRI is not accually talking to the 3D GPU, so libmesa is emulating the 3D functions in software instead. When running in VESA mode I get simular results, which would support that no hardware acceleration is being done at all.

How do I determine if DRI is accualy using the hardware GPU or if MESA is taking care of the rendering?

---

### Post by PiCkAjEw on 2009-01-12
First of all, thank you for doing all the investigative work. I'll give Fedora a try.

There is a bug report related to this on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)  The report was file in July, 2008. So I'm speculating if this issue was going to get resolved, it would have by now. In the bug report, many have tried different ways or workaround to this issue, but no success. 

Now apparently because Bryce Harrington has felt the report is too general and vague, he declined it with a long, "detailed" reply. Please have a read and get a cliff-notes about it if possible. So to continue with that tradition of being long-winded and inability to assist, I'm here responding to you and basically saying that stick with the distros that work for you. And maybe switch back to Ubuntu when the time is right, when all the bug reports have been filed according to the "standards" and when the people who troubleshoot issues related to the built-in INTEL cards can actually install 8.10 on it and test it. But we should not hold our breath and should not demand so much from all these good people. We have to understand that the INTEL built-in video card is tremendously difficult to come by in the year 2009. So what then?

Well, it may be a pain in the... to transfer all of your own files to another distro... And you know what? Performance from the Intel GMA 4500HD is very smooth and its response time is mighty fast in MS Windows. :p


> **mathias_sundman said:**
> Okay, I give up! I've just spent half a day trying out the latest and greatest libdrm, libdrm2, libdrm-intel1, libdl1-mesa-dri, libgl1-mesa-glx,  xserver-xorg-video-intel git-packages from xorg-edgers, but I was unable to get any of the newer builds running at all on my ubuntu 8.10 system. I assume they depend on a 2.6.28 kernel with GEM and modesetting support or something.

Anyway I ended up reverting to:

xserver-xorg-video-intel_2.5.1~git20081113_i386.deb
libdrm2_2.4.0~git20081014.d9c2f65d-0ubuntu0tormod1_i386.deb
libdrm-dev_2.4.0~git20081014.d9c2f65d-0ubuntu0tormod1_i386.deb
libgl1-mesa-dri_7.2~git20081014+mesa-7-2-branch.ecab8131-0ubuntu0tormod_i386.deb
libgl1-mesa-glx_7.2~git20081014+mesa-7-2-branch.ecab8131-0ubuntu0tormod_i386.deb

They were the latest packages I was able to get up and running. With these packages installed and AccelMethod XAA, I atleast have decent 2D graphics. However the sound interruptions still persist, and 3D graphics is still horrible.

I feel kinda stuck now.

My theory is that that the kernel part of DRI is not accually talking to the 3D GPU, so libmesa is emulating the 3D functions in software instead. When running in VESA mode I get simular results, which would support that no hardware acceleration is being done at all.

How do I determine if DRI is accualy using the hardware GPU or if MESA is taking care of the rendering?

---

### Post by renierviljoen on 2009-01-14
Hi 

I'm not to sure if this is the place to post my problem, but I need to start somewhere :-). 

I've got a Dell E6500 with Ubuntu 8.04-1 on it. Every time I play a video the system halt on me. First the screen go all scrambled and then it seems like the system just die on me. No other screens are available to me to do a shutdown and are forced to manually power it down. 

The xserver-xorg-video-intel (2:2.2.1-1ubuntu13.4) driver are installed. The resolution is fine on 1920x1200. Trying to change the driver degrade the resolution to 1600x1200 and this is not working for me. I can't upgrade to 8.10 for varies reasons although doing so everything works. 

My question I suppose would be: How would I be able to use the drivers from 8.10 on 8.04-1?

Renier

---

### Post by PiCkAjEw on 2009-01-14
Try

[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)

---

### Post by litmus_persuasion on 2009-11-05
> **mathias_sundman said:**
> I installed Jaunty Alpha-1, but got the same results as above. However alot of xorg related packages were kept back from beeing upgraded with apt-get upgrade. After a forced update of all kept back packages I was unable to get X running at all. Didn't spend more time investigating it, instead I moved on and tried installing Fedora Core 10.

Guess what? Out of the box it worked great!

x11perf --aa10text gave about 150000/sec with EAX Accel, which only gave me about 22000/sec on my ubuntu system.

But the big surprise what that 3D also worked much better. glxgears gave 1200 FPS!

And this was with a default Fedora Core 10 system running a 2.6.27 kernel. There should be a 2.6.28 kernel available for Fedora but I wasn't able to just yum install it. I'll continue investigate that tomorrow.

The big question now is what is it with the Fedora system running Linux kernel 2.6.27 and xf86-video-intel 2.5.0 that makes it work so much better than my ubuntu system running the same kernel and even the intel v2.5.1 driver.

Sadly, I concur with Mathias' results.  I have a Dell E6500 laptop, P9600 Core 2 Duo, running the Mobile Intel GM45 chipset, 4Gb of RAM, and installed in 64 bit mode.  

I eagerly replaced my Ubuntu 9.04 with 9.10 (not an upgrade), on the promise that Ubuntu engineers fixed the Intel problems.  I'd been around the EXA/UXA changeover and the Hal fiasco, and I was ready to finally get a usable system.  I ran glxgears and got 296 FPS.  I ran x11perf --aa10text and got 82,000/sec.  I also visited a flash-encrusted site, and did a simple scroll-drag test - the screen was a bit choppy trying to scroll.

I tried a Fedora 11 live CD, and repeated glxgears - it gave me 625 FPS.  Amazing!  I then installed it completely and repeated the test (getting the same results), went through package hell to obtain and compile x11perf, and x11perf showed 210,000/sec.  It's almost a 3-times difference in speed.  The flash-encrusted scroll test worked perfectly.

After moving (back) to Fedora, I also noticed other things that I wasn't able to run on Ubuntu **on my specific setup**.  I am able to use Compiz, my PDF files update instantaneously, and my 10Mpix photo thumbnails show up instantaneously.

What I'm giving up in usability and package management awesomeness, and just generally a warm, friendly community with Ubuntu, I'm gaining back three times over in video performance with Fedora.  Once again, this is for my specific setup.

If you have my specific setup - Dell E6500, P9600 Core 2 Duo, running the Intel video card - and you are using Ubuntu 9.10 or 9.04, try Fedora.  The experience is revolutionary.  For those of you on Ubuntu 9.10 on other platforms, you cannot begin to know how slow this was for us Dell users.

Not convinced?  The slow video made some other interesting problems for me: PDF files wouldn't render right away - took 0.5 seconds for each page-down.  This meant that TeXmaker wouldn't compile all that fast.  In fact, I got a delayed keyboard reaction in a long TeXmaker document AND in Open Office.  I even went to Open Office and disabled Java and lots of other things to make the keyboard more responsive.  The display was always 3 characters behind where I was typing.  Because the video was slow, I also incurred a hotter CPU and shorter battery life.  Trying to watch a movie sapped all the system resources.  Photo icons wouldn't appear - and one time, I tried showing an animation in a Power Point slide show (via OpenOffice Impress), and the animations that normally snapped on took 3 seconds EACH to appear.

The video was so slow, I just convinced myself that this was the moral price I paid for not running the Redmond Infectious Adware Alternative (RIAA) operating system.

I don't know how, or why, but somehow the Fedora people have figured out the G45 video in a way that Ubuntu continues to struggle with.  So, while my heart is still with the Ubuntu crowd, for now, I my CPU has to be with Fedora.  I'll check back and try a live CD when the next version comes out.

---

