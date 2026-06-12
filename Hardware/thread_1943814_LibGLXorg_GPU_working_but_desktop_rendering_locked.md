---
title: "LibGL/Xorg: GPU working but desktop rendering locked to &quot;Software Rasterizer&quot;"
date: 2012-03-20
forum: Hardware
---

### Post by aps2012 on 2012-03-20
Hi all, 

My basic problem is that GPU acceleration is not working for the desktop environment in Ubuntu 10.10. Dragging windows is sluggish and you can physically see the screen redraws occurring during any kind of fast movement or animation. However, GPU acceleration is working for other OpenGL applications (confirmed: glxgears, OpenGL screensavers, Adobe Flash) and there are **no errors** in any log files; all systems seem to be initialising, although not optimally it would appear. 

There are two different symptoms I am seeing here but I seriously suspect that both are being caused by one and the same problem: 

[LIST=1]
[*]LibGL is choosing to select the "Software Rasterizer" for rendering, even though I have the DRI module for my graphics chipset installed and available on my system.
[*]Xorg server thinks that a DRI module isn't available and that direct rendering isn't available, even though the driver for my graphics chipset can be seen in the kernel and Xorg logs successfully allocating and initialising all the flip buffers, frame buffers, tiling surfaces, etc.
[/LIST]
There are two things that I would be eternally grateful for if anybody could help with: 

[LIST=1]
[*]How do I get LibGL to choose the hardware renderer that has been installed for my chipset instead of the sluggish "Software Rasterizer"?
[*]How do I configure the Xorg server so that it knows hardware rendering has been initialised and setup and can accelerate desktop drawing operations?
[/LIST]
All the details (so far) of the problem are laid out below. I know that this problem does not occur in 11.10 on the same hardware. So the big question is, can anybody shed any light on how LibGL or Xorg are behaving in 11.10 that is different (or missing) in 10.10?

Any help would be much appreciated.

Thanks in advance.


[B]Environment 
[/B]
The hardware is the brand new _[Asus U24E (Intel core-i5)]("http://www.asus.co.jp/Notebooks/Superior_Mobility/U24E/")_ laptop. The reason I chose Ubuntu with this laptop is because I saw a video of it working  in two online reviews. In the reviews, the OS was a vanilla  Ubuntu 11.10 with a few configuration file changes (fixes for suspend/resume and HD spin up/down under ACPI). The problem is that I hate the UI for v11.x, and prefer the UI for v10.x. As I have  physically seen a version of Ubuntu working with the  machine I know that, as a last resort, I could use 11.10. However, if  possible, I really would like to get it going on 10.10. 

The environment as it currently stands was prepared as follows: 

[LIST=1]
[*]Ubuntu 10.10 (amd64, alternate installation) was installed from ISO CD image.
[*]Kernel was fast-forwarded from 2.6.35 to 3.2.12-030212, the current kernel for Oneiric. This was done to get kernel support for all the peripherals and Intel Sandy Bridge HD3000 graphics chipset.
[*]Package [FONT=Courier New]mesa-utils[/FONT] was installed using *apt-get* so I could run the [FONT=Courier New]glxinfo[/FONT] and [FONT=Courier New]glxgears[/FONT] tools.
[/LIST]
And that's all. Apart from steps (2) and (3) above, it is a **completely vanilla** system. There are no externally-connected displays, and the onboard LCD is 1366*768, 24bpp.

No post-installation software updates have been performed. This is the second time I've built this system. The first time I did run all the post-installation updates. After the second clean install I noticed the logs and symptoms were identical in every way without the updates, so the system currently doesn't have them.

That said, the environment works very well and is completely stable (I'm composing this post on it), and all laptop-specific features (Wi-Fi, Bluetooth, WebCAM, touchpad, LAN, hotkeys) all work perfectly. 


[B]glxinfo Symptom
[/B]
The [FONT=Courier New]glxinfo[/FONT] problem is a simple one: LibGL refuses to load any other DRI module except the "Software Rasterizer" (module [FONT=Courier New]swrast_dri.so[/FONT]). The default behaviour of Xorg is to fallback onto this module when there is no other support in the system. However, in my case, LibGL is choosing to ignore all the other drivers in my system and choose the software emulation module, as can be seen in the following [FONT=Courier New]glxinfo[/FONT] output:

```

~/Downloads$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
...

```I have been searching for days regarding this problem; nobody has had the same experience. In every other case, an error has been seen in the log just before "OpenDriver" causing Xorg to choose the fallback software rasterise module. In my case, there is no error. However, the DRI module for Intel Sandy Bridge HD3000 chipset ([FONT=Courier New]i915_dri.so[/FONT]) is installed as this directory listing shows:

```

~/Downloads$ ls -la /usr/lib/dri
total 42392
drwxr-xr-x   2 root root    4096 2012-03-20 15:55 .
drwxr-xr-x 192 root root   53248 2012-03-20 16:52 ..
-rw-r--r--   1 root root 3388456 2010-10-01 02:19 i915_dri.so
-rw-r--r--   1 root root 3504872 2010-10-01 02:19 i965_dri.so
-rw-r--r--   1 root root 3343112 2010-10-01 02:19 mga_dri.so
-rw-r--r--   1 root root 3228264 2010-10-01 02:19 r128_dri.so
-rw-r--r--   1 root root 3428008 2010-10-01 02:19 r200_dri.so
-rw-r--r--   1 root root 3443360 2010-10-01 02:19 r300_dri.so
-rw-r--r--   1 root root 3463208 2010-10-01 02:19 r600_dri.so
-rw-r--r--   1 root root 3386896 2010-10-01 02:19 radeon_dri.so
-rw-r--r--   1 root root 3282160 2010-10-01 02:19 savage_dri.so
-rw-r--r--   1 root root 3318504 2010-10-01 02:19 sis_dri.so
-rw-r--r--   1 root root 3018800 2010-10-01 02:19 swrast_dri.so
-rw-r--r--   1 root root 3281608 2010-10-01 02:19 tdfx_dri.so
-rw-r--r--   1 root root 3228368 2010-10-01 02:19 unichrome_dri.so

```LibGL needs to be told that my Intel DRI module is present so it can load it. At the moment, it isn't even bothering to look for another rasterisation module.


[B]Xorg Symptom
[/B]
The problem with Xorg can be seen in the log [FONT=Courier New]/var/log/Xorg.0.log[/FONT] (see attachment). The lines in the log that drew my attention were as follows:

```

...
[  4259.580] (II) intel(0): Using exact sizes for initial modes
[  4259.580] (II) intel(0): Output LVDS1 using initial mode 1366x768
[  4259.580] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  4259.580] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[  4259.580] (**) intel(0): Display dimensions: (260, 140) mm
[  4259.580] (**) intel(0): DPI set to (133, 139)
[  4259.580] (II) Loading sub module "fb"
[  4259.580] (II) LoadModule: "fb"
[  4259.580] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4259.581] (II) Module fb: vendor="X.Org Foundation"
[  4259.581]     compiled for 1.9.0, module version = 1.0.0
[  4259.581]     ABI class: X.Org ANSI C Emulation, version 0.4
[  4259.581] (==) Depth 24 pixmap format is 32 bpp
[  4259.581] (**) intel(0): Tiling enabled
[  4259.581] (**) intel(0): SwapBuffers wait enabled
[  4259.581] (==) intel(0): VideoRam: 262144 KB
[  4259.581] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  4259.590] (II) UXA(0): Driver registered support for the following operations:
[  4259.590] (II)         solid
[  4259.590] (II)         copy
[  4259.590] (II)         composite (RENDER acceleration)
[  4259.590] (II)         put_image
[  4259.590] (II)         get_image
[  4259.590] (==) intel(0): Backing store disabled
[  4259.590] (==) intel(0): Silken mouse enabled
[  4259.590] (II) intel(0): Initializing HW Cursor
[  4259.648] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  4259.650] (==) intel(0): DPMS enabled
[  4259.650] (==) intel(0): Intel XvMC decoder enabled
[  4259.651] (II) intel(0): Set up textured video
[  4259.651] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[  4259.651] (II) intel(0): direct rendering: Disabled
[  4259.651] (--) RandR disabled
[  4259.651] (II) Initializing built-in extension Generic Event Extension
[  4259.651] (II) Initializing built-in extension SHAPE
[  4259.651] (II) Initializing built-in extension MIT-SHM
[  4259.651] (II) Initializing built-in extension XInputExtension
[  4259.651] (II) Initializing built-in extension XTEST
[  4259.651] (II) Initializing built-in extension BIG-REQUESTS
[  4259.651] (II) Initializing built-in extension SYNC
[  4259.651] (II) Initializing built-in extension XKEYBOARD
[  4259.651] (II) Initializing built-in extension XC-MISC
[  4259.651] (II) Initializing built-in extension SECURITY
[  4259.651] (II) Initializing built-in extension XINERAMA
[  4259.651] (II) Initializing built-in extension XFIXES
[  4259.651] (II) Initializing built-in extension RENDER
[  4259.651] (II) Initializing built-in extension RANDR
[  4259.651] (II) Initializing built-in extension COMPOSITE
[  4259.651] (II) Initializing built-in extension DAMAGE
[  4259.651] (II) Initializing built-in extension GESTURE
[  4259.661] (II) AIGLX: Screen 0 is not DRI2 capable
[  4259.661] (II) AIGLX: Screen 0 is not DRI capable
[  4259.663] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
...

```Firstly, the intel driver doesn't enable direct rendering, and (possibly) because of this, AIGLX decides to use the software renderer.

I do have an [FONT=Courier New]xorg.conf[/FONT] file although the behaviour of the system is exactly the same with or without the file. The file was automatically generated with [FONT=Courier New]Xorg -configure[/FONT] and looks as follows:

```

Section "Device"
    ### Available Driver options are:-
    ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
    ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
    ### <percent>: "<f>%"
    ### [arg]: arg optional
    #Option     "NoAccel"                # [<bool>]
    #Option     "SWcursor"               # [<bool>]
    #Option     "ColorKey"               # <i>
    #Option     "CacheLines"             # <i>
    #Option     "Dac6Bit"                # [<bool>]
    #Option     "DRI"                    # [<bool>]
    #Option     "NoDDC"                  # [<bool>]
    #Option     "ShowCache"              # [<bool>]
    #Option     "XvMCSurfaces"           # <i>
    #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

```I removed all other sections to do with the layout of single display, mouse and keyboard, etc. so that Xorg uses the defaults. Xorg still finds the correct device and uses the same parameters to initialise it, whether the file is there or not as the file contains only default settings.


[B]Attempts At Fixing The Problem(s)
[/B] 
There are a number of tests I tried on the first installation attempt (in no particular order),  which resulted eventually in my Xorg server hanging my PC on startup.

[LIST]
[*] Uninstall/reinstall [FONT=Courier New]libgl1-mesa-dri[/FONT] and [FONT=Courier New]libgl1-mesa-glx[/FONT] packages (no effect)
[*] Uninstall/reinstall [FONT=Courier New]libglu1-mesa[/FONT] package (no effect)
[*] Attempted to fast-forward [FONT=Courier New]xserver-xorg-video-intel[/FONT] package to the version used in 11.10 (Oneiric) (update failed)
[*] Attempted to fast-forward [FONT=Courier New]xserver-xorg[/FONT] and [FONT=Courier New]xserver-xorg-core[/FONT] packages to version used in 11.10 (update failed)
[*] Attempted to uninstall and reinstall [FONT=Courier New]xserver-xorg[/FONT] package (no effect).
[*]Tried adding [FONT=Courier New]i915.modeset=1[/FONT] to [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT[/FONT] in [FONT=Courier New]/etc/default/grub[/FONT] (no effect)
[*]Tried adding [FONT=Courier New]i915 modeset=1[/FONT] to [FONT=Courier New]/etc/modules[/FONT] (no effect)
[/LIST]
[B]
Attached Files[/B]

[LIST]
[*]Archive of all log files (_[[FONT=Courier New]Problem-001.tar[/FONT]]("http://ubuntuforums.org/attachment.php?attachmentid=214606&stc=1&d=1332239294")_)
[/LIST]
[B]
Results of Standard Tests
[/B]
Here are the results of all the usual checks and tests:

1) [FONT=Courier New]uname -a[/FONT]

```

Linux ubuntu-pegasus 3.2.12-030212-generic #201203191306 SMP Mon Mar 19 17:07:26 UTC 2012 x86_64 GNU/Linux

```2) [FONT=Courier New]lspci | grep VGA[/FONT]

```

00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)

```3) [FONT=Courier New]lshw -C video[/FONT]

```

  *-display               
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:53 memory:f4800000-f4bfffff memory:e0000000-efffffff ioport:e000(size=64)

```4) [FONT=Courier New]glxinfo | grep -i render
[/FONT]
```

direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program,

```5) [FONT=Courier New]glxgears[/FONT]

```

4613 frames in 5.0 seconds = 922.526 FPS
4586 frames in 5.0 seconds = 917.108 FPS
4499 frames in 5.0 seconds = 899.645 FPS
4566 frames in 5.0 seconds = 913.147 FPS
4427 frames in 5.0 seconds = 885.350 FPS
4529 frames in 5.0 seconds = 905.699 FPS
4299 frames in 5.0 seconds = 859.631 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 64614 requests (41 known processed) with 0 events remaining.

```The three gears display correctly and animate completely smoothly even when window is being violently dragged around the desktop.

6)  [FONT=Courier New]dmesg | grep drm[/FONT]

```

[   13.631127] [drm] Initialized drm 1.1.0 20060810
[   13.778076] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.778077] [drm] Driver supports precise vblank timestamp query.
[   14.316692] fbcon: inteldrmfb (fb0) is primary device
[   14.532240] fb0: inteldrmfb frame buffer device
[   14.532242] drm: registered panic notifier
[   14.536434] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

```7) [FONT=Courier New]dpkg -l '*mesa*'[/FONT]

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  libgl1-mesa-dri             7.9~git20100924-0ubuntu2    A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx             7.9~git20100924-0ubuntu2    A free implementation of the OpenGL API -- GLX runtime
ii  libglu1-mesa                7.9~git20100924-0ubuntu2    The OpenGL utility library (GLU)
ii  mesa-utils                  8.0.1-0ubuntu1              Miscellaneous Mesa GL utilities
un  mesag3                      <none>                      (no description available)
un  xlibmesa-dri                <none>                      (no description available)
un  xlibmesa3                   <none>                      (no description available)

```8. [FONT=Courier New]dpkg -l '*libgl1*'[/FONT]

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  libgl1                      <none>                      (no description available)
ii  libgl1-mesa-dri             7.9~git20100924-0ubuntu2    A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx             7.9~git20100924-0ubuntu2    A free implementation of the OpenGL API -- GLX runtime

```9) [FONT=Courier New]dpkg -l '*intel*'[/FONT]

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  intel-gpu-tools             1.0.2+git20100324-0ubuntu1  tools for debugging the Intel graphics driver
ii  libdrm-intel1               2.4.21-1ubuntu2             Userspace interface to intel-specific kernel DRM services -- runtime
ii  xserver-xorg-video-intel    2:2.12.0-1ubuntu5           X.Org X server -- Intel i8xx, i9xx display driver
un  xserver-xorg-video-intel-mo <none>                      (no description available)

```

---

### Post by ALLurGroceries on 2012-03-22
Hey bud, I replied to you over at NBR: [http://forum.notebookreview.com/asus-reviews-owners-lounges/624121-asus-u24e-review-owners-lounge-24.html#post8395286](http://forum.notebookreview.com/asus-reviews-owners-lounges/624121-asus-u24e-review-owners-lounge-24.html#post8395286)

In a nutshell, your kernel and driver stack are too old. So you need a new distro, like 11.10 for decent sandy bridge support.

---

### Post by aps2012 on 2012-04-03
Hi ALLurGroceries,

Apologies for the late reply. I've replied to you down at Laptop Forums.

Thanks for your assistance.

---

### Post by aps2012 on 2012-04-03
Well, thanks to some helpful pointers from people, I have successfully diagnosed the source of the problems and now my system is fully operational and completely stable.

I can confirm that the Asus UE24 (Core i5) PX-2430 Netbook works with Ubuntu 10.10 and I have my beloved Gnome-2 back.

The problem was missing X Server support for the Intel Sandy Bridge HD3000 chipset. I updated the kernel, XOrg Intel driver, and 78 other dependent and surrounding packages, effectively fast-forwarding the entire [FONT=Courier New]xserver-xorg[/FONT] through two distributions from 10.10 to 11.10 (final).

Here is how my system behaves now:

First, uname -a:
```

Linux ubuntu-pegasus 3.2.12-030212-generic #201203191306 SMP Mon Mar 19 17:07:26 UTC 2012 x86_64 GNU/Linux

```Next, [FONT=Courier New]glxinfo[/FONT]:
```

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render,

```And [FONT=Courier New]glxgears[/FONT] now produces the following:

```

$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.230 FPS
301 frames in 5.0 seconds = 60.061 FPS
301 frames in 5.0 seconds = 60.060 FPS
301 frames in 5.0 seconds = 60.059 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2599 requests (2598 known processed) with 0 events remaining.
```Desktop updates are now much, much quicker and no matter how much I drag windows around, redrawing doesn't seem to slow performance at all. To summarise, here are the important details of my working system:
[LIST]
[*]Ubuntu 10.10 (alternate CD installation)
[*]Kernel 3.2.12-030212 (from Oneiric)
[*][FONT=Courier New]xserver-xorg[/FONT] 1:7.6+7ubuntu7 (from Oneiric)
[*][FONT=Courier New]xserver-xorg-video-intel[/FONT] 2:2.15.901-1ubuntu2.1 (from Oneiric)
[*][FONT=Courier New]libdrm-intel1 [FONT=Verdana]2.46-1ubuntu1[/FONT][/FONT] (from Oneiric, includes Sandy Bridge)
[/LIST]
I now have a script that performs the necessary installs, removals, and dependency fixups automatically, and Update Manager and Synaptic Package Manager are both happy and are downloading new updates.

Thanks to all who took an interest.

---

### Post by aps2012 on 2012-04-03
Marked as solved \\:D/

---

