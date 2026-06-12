---
title: "Highest monitor resolution not available"
date: 2019-10-14
forum: Hardware
---

### Post by Lucretia on 2019-10-14
After a number of years away from Ubuntu, I'm back to using it again, and it's overall an enjoyable experience so far! However, I'm having an issue with setting my monitor resolution. I'm using a [Prism+]("https://prismplus.sg/collections/gaming-monitors/products/prism-x315-pro?gclid=EAIaIQobChMI57Lflpid5QIVixePCh12oQ38EAAYASABEgI_efD_BwE"), which claims to support resolutions up to 2560x1440. My graphics card is a GeForce RTX 2060 and the monitor is connected via the display port. I'm using the Nvidia driver on Ubuntu 18.04.

The highest resolution available in the X Server settings is 1920x1080. I tried following [this guide]("http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/") to enable the 2560x1440 resolution, but it didn't work (also it's for an older version of Ubuntu). Some of the comments seem to indicate that the Nvidia driver has to be disabled.

Has anyone been able to fix this issue?

---

### Post by cruzer001 on 2019-10-14
Nvidia site tells me the 430.34 driver is needed for your 2060 card.  Is that what your running?

---

### Post by CatKiller on 2019-10-15
The log file is at /var/log/Xorg.0.log. That might tell you why it's not picking the mode that you're interested in. You don't need to muck about with custom modelines if your monitor is properly advertising its capabilities through EDID.

---

### Post by Autodave on 2019-10-15
What driver are you using and where did you get it from?

---

### Post by Lucretia on 2019-10-16
It's the Nvidia driver, version 430.50. This is a work computer and everything was set up before I started using the machine, so I don't know the details of how it was set up. It's a tiny company, so no IT department or anything! I think they just installed the Nvidia driver and left it at that. I heard that I might have more luck with an open source driver.

---

### Post by cruzer001 on 2019-10-16
Please post the output of xrandr.

---

### Post by Lucretia on 2019-10-16
> **CatKiller said:**
> The log file is at /var/log/Xorg.0.log. That might tell you why it's not picking the mode that you're interested in. You don't need to muck about with custom modelines if your monitor is properly advertising its capabilities through EDID.

I'm looking at the log file, but I'm not really sure what I'm looking for. I don't normally delve into these things.

I'm trying access what is being picked up through EDID.

```
~$ sudo get-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
1 potential busses found: 0
```

How do I interpret this?

Then I ran "sudo parse-edid", but the terminal just hangs. Is there another tool for this? Or is this a sign that the monitor isn't actually reporting its capabilities at all?

---

### Post by Lucretia on 2019-10-16
> **cruzer001 said:**
> Please post the output of xrandr.

This is what I get, which matches what I see as options in the Nvidia X server settings:

```
~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 700mm x 400mm
   1920x1080     60.00 + 144.00   119.88*   59.94    50.00  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x720     119.88   100.00    60.00    59.94    50.00  
   1152x864      59.96  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by cruzer001 on 2019-10-16
Its bedtime here, have to chime back in tomorrow when I can do a better job of thinking :)

---

### Post by CatKiller on 2019-10-16
> **Lucretia said:**
> I'm looking at the log file, but I'm not really sure what I'm looking for. I don't normally delve into these things.

Well, you can always post it here.

What you'd expect to see is a section where the driver queries the monitor for the resolutions that it advertises, then compares the result with its own checks to create a list of modes and timings that they both agree on, and then picks the one that it thinks is best.

I suspect that your monitor is not properly advertising the modes that it can do, although it's possible that the driver is rejecting the mode for some other reason. The log file will probably say either way. Your attempts to probe the monitor's EDID seem to support the idea that the monitor isn't responding as helpfully as it might. 

If it *does* turn out that your monitor isn't advertising properly, you can specify enough information in xorg.conf to allow the driver to pick the right resolution. HorizSync and VertRefresh are usually sufficient, which you can generally get from the monitor's specs.

But it's best to establish that is what the issue is before you start poking at the config files. It's also generally a good idea to make sure that you're comfortable copying or editing text files from the command line before you poke it; misconfiguration means that you might temporarily end up with no graphical environment at all.

---

### Post by cruzer001 on 2019-10-16
@CatKiller
I don't see why xrandr did not work for setting resolution so guess I'm on the side till xorg log is posted.

---

### Post by Autodave on 2019-10-16
Do not use the drivers from the 'net.  You are only asking for trouble if you do that.

You said that the monitor is connected to the display port, but are there any adapters being used?  Like display port to VGA, etc?

---

### Post by TheFu on 2019-10-16
> **cruzer001 said:**
> @CatKiller
I don't see why xrandr did not work for setting resolution so guess I'm on the side till xorg log is posted.

The EDID info is missing. That's what tells xorg and xrandr which resolutions are possible.  Without correct EDID, you'll need to get correct EDID from somewhere and tell the nvidia driver to use it.  I've had to do this due to an Display Port -to- VGA adaptor failing to pass through the monitor EDID.

In the xorg.conf, I added :
```
    Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"
```
to the "device" section for the GPU.
which was pulled from my dell monitor using a different computer which had no problem getting the raw EDID dumped and put it into that file above. The filename can be anything, but it must contain the binary EDID for the monitor.

BTW, I don't have the same nvidia GPU that you have.

---

### Post by cruzer001 on 2019-10-16
@TheFu
Thanks for the explanation.  I have not crossed paths with EDID, guess I lead a bless life.

---

### Post by Lucretia on 2019-10-16
> **CatKiller said:**
> Well, you can always post it here.

What you'd expect to see is a section where the driver queries the monitor for the resolutions that it advertises, then compares the result with its own checks to create a list of modes and timings that they both agree on, and then picks the one that it thinks is best.

I suspect that your monitor is not properly advertising the modes that it can do, although it's possible that the driver is rejecting the mode for some other reason. The log file will probably say either way. Your attempts to probe the monitor's EDID seem to support the idea that the monitor isn't responding as helpfully as it might. 

If it *does* turn out that your monitor isn't advertising properly, you can specify enough information in xorg.conf to allow the driver to pick the right resolution. HorizSync and VertRefresh are usually sufficient, which you can generally get from the monitor's specs.

But it's best to establish that is what the issue is before you start poking at the config files. It's also generally a good idea to make sure that you're comfortable copying or editing text files from the command line before you poke it; misconfiguration means that you might temporarily end up with no graphical environment at all.

Here is the log file in its entirety:

```
[    34.060] (--) Log file renamed from "/var/log/Xorg.pid-1235.log" to "/var/log/Xorg.0.log"
[    34.061] 
X.Org X Server 1.20.4
X Protocol Version 11, Revision 0
[    34.061] Build Operating System: Linux 4.4.0-148-generic x86_64 Ubuntu
[    34.061] Current Operating System: Linux atomionics-MS-7C08 5.0.0-31-generic #33~18.04.1-Ubuntu SMP Tue Oct 1 10:20:39 UTC 2019 x86_64
[    34.061] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=b8ebf575-c6b9-4dc1-83ca-1c77437399fc ro quiet splash vt.handoff=1
[    34.061] Build Date: 02 May 2019  08:06:54AM
[    34.061] xorg-server-hwe-18.04 2:1.20.4-1ubuntu3~18.04.1 (For technical support please see http://www.ubuntu.com/support) 
[    34.061] Current version of pixman: 0.34.0
[    34.061] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    34.061] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.061] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 15 11:51:50 2019
[    34.086] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.086] (==) No Layout section.  Using the first Screen section.
[    34.086] (==) No screen section available. Using defaults.
[    34.086] (**) |-->Screen "Default Screen Section" (0)
[    34.086] (**) |   |-->Monitor "<default monitor>"
[    34.086] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    34.086] (==) Automatically adding devices
[    34.086] (==) Automatically enabling devices
[    34.086] (==) Automatically adding GPU devices
[    34.086] (==) Automatically binding GPU devices
[    34.086] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    34.118] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.118] 	Entry deleted from font path.
[    34.118] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.118] 	Entry deleted from font path.
[    34.118] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.118] 	Entry deleted from font path.
[    34.130] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.130] 	Entry deleted from font path.
[    34.130] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.130] 	Entry deleted from font path.
[    34.130] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    34.130] (==) ModulePath set to "/usr/lib/xorg/modules"
[    34.130] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.130] (II) Loader magic: 0x5605ffd12020
[    34.130] (II) Module ABI versions:
[    34.130] 	X.Org ANSI C Emulation: 0.4
[    34.130] 	X.Org Video Driver: 24.0
[    34.130] 	X.Org XInput driver : 24.1
[    34.130] 	X.Org Server Extension : 10.0
[    34.130] (++) using VT number 1

[    34.132] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[    34.132] (II) xfree86: Adding drm device (/dev/dri/card0)
[    34.132] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
[    34.133] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia-430/xorg,/usr/lib/xorg/modules"
[    34.133] (--) PCI:*(1@0:0:0) 10de:1f08:10de:12fd rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
[    34.134] (II) LoadModule: "glx"
[    34.134] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.134] (II) Module glx: vendor="X.Org Foundation"
[    34.134] 	compiled for 1.20.4, module version = 1.0.0
[    34.134] 	ABI class: X.Org Server Extension, version 10.0
[    34.134] (II) Applying OutputClass "nvidia" to /dev/dri/card0
[    34.134] 	loading driver: nvidia
[    34.353] (==) Matched nvidia as autoconfigured driver 0
[    34.353] (==) Matched nouveau as autoconfigured driver 1
[    34.353] (==) Matched modesetting as autoconfigured driver 2
[    34.353] (==) Matched fbdev as autoconfigured driver 3
[    34.353] (==) Matched vesa as autoconfigured driver 4
[    34.353] (==) Assigned the driver to the xf86ConfigLayout
[    34.353] (II) LoadModule: "nvidia"
[    34.353] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia-430/xorg/nvidia_drv.so
[    34.353] (II) Module nvidia: vendor="NVIDIA Corporation"
[    34.353] 	compiled for 1.6.99.901, module version = 1.0.0
[    34.353] 	Module class: X.Org Video Driver
[    34.353] (II) LoadModule: "nouveau"
[    34.353] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    34.365] (II) Module nouveau: vendor="X.Org Foundation"
[    34.365] 	compiled for 1.20.4, module version = 1.0.16
[    34.365] 	Module class: X.Org Video Driver
[    34.365] 	ABI class: X.Org Video Driver, version 24.0
[    34.365] (II) LoadModule: "modesetting"
[    34.365] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.365] (II) Module modesetting: vendor="X.Org Foundation"
[    34.365] 	compiled for 1.20.4, module version = 1.20.4
[    34.365] 	Module class: X.Org Video Driver
[    34.365] 	ABI class: X.Org Video Driver, version 24.0
[    34.365] (II) LoadModule: "fbdev"
[    34.365] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.365] (II) Module fbdev: vendor="X.Org Foundation"
[    34.365] 	compiled for 1.20.1, module version = 0.5.0
[    34.365] 	Module class: X.Org Video Driver
[    34.365] 	ABI class: X.Org Video Driver, version 24.0
[    34.365] (II) LoadModule: "vesa"
[    34.365] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.365] (II) Module vesa: vendor="X.Org Foundation"
[    34.365] 	compiled for 1.20.1, module version = 2.4.0
[    34.365] 	Module class: X.Org Video Driver
[    34.365] 	ABI class: X.Org Video Driver, version 24.0
[    34.365] (II) NVIDIA dlloader X Driver  430.50  Thu Sep  5 22:43:53 CDT 2019
[    34.365] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    34.365] (II) NOUVEAU driver Date:   Mon Jan 28 23:25:58 2019 -0500
[    34.365] (II) NOUVEAU driver for NVIDIA chipset families :
[    34.365] 	RIVA TNT            (NV04)
[    34.365] 	RIVA TNT2           (NV05)
[    34.365] 	GeForce 256         (NV10)
[    34.365] 	GeForce 2           (NV11, NV15)
[    34.365] 	GeForce 4MX         (NV17, NV18)
[    34.365] 	GeForce 3           (NV20)
[    34.365] 	GeForce 4Ti         (NV25, NV28)
[    34.365] 	GeForce FX          (NV3x)
[    34.365] 	GeForce 6           (NV4x)
[    34.365] 	GeForce 7           (G7x)
[    34.365] 	GeForce 8           (G8x)
[    34.365] 	GeForce 9           (G9x)
[    34.365] 	GeForce GTX 2xx/3xx (GT2xx)
[    34.365] 	GeForce GTX 4xx/5xx (GFxxx)
[    34.365] 	GeForce GTX 6xx/7xx (GKxxx)
[    34.365] 	GeForce GTX 9xx     (GMxxx)
[    34.365] 	GeForce GTX 10xx    (GPxxx)
[    34.365] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    34.365] (II) FBDEV: driver for framebuffer: fbdev
[    34.365] (II) VESA: driver for VESA chipsets: vesa
[    34.365] (II) systemd-logind: releasing fd for 226:0
[    34.366] (II) Loading sub module "fb"
[    34.366] (II) LoadModule: "fb"
[    34.366] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.366] (II) Module fb: vendor="X.Org Foundation"
[    34.366] 	compiled for 1.20.4, module version = 1.0.0
[    34.366] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    34.366] (II) Loading sub module "wfb"
[    34.366] (II) LoadModule: "wfb"
[    34.366] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    34.366] (II) Module wfb: vendor="X.Org Foundation"
[    34.366] 	compiled for 1.20.4, module version = 1.0.0
[    34.366] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    34.366] (II) Loading sub module "ramdac"
[    34.366] (II) LoadModule: "ramdac"
[    34.366] (II) Module "ramdac" already built-in
[    34.366] (WW) Falling back to old probe method for modesetting
[    34.366] (WW) Falling back to old probe method for fbdev
[    34.367] (II) Loading sub module "fbdevhw"
[    34.367] (II) LoadModule: "fbdevhw"
[    34.385] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.385] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.385] 	compiled for 1.20.4, module version = 0.0.2
[    34.385] 	ABI class: X.Org Video Driver, version 24.0
[    34.385] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    34.385] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    34.385] (==) NVIDIA(0): RGB weight 888
[    34.385] (==) NVIDIA(0): Default visual is TrueColor
[    34.385] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    34.385] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[    34.385] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[    34.385] (**) NVIDIA(0): Enabling 2D acceleration
[    34.385] (II) Loading sub module "glxserver_nvidia"
[    34.385] (II) LoadModule: "glxserver_nvidia"
[    34.385] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia-430/xorg/libglxserver_nvidia.so
[    34.970] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[    34.970] 	compiled for 1.6.99.901, module version = 1.0.0
[    34.970] 	Module class: X.Org Server Extension
[    34.971] (II) NVIDIA GLX Module  430.50  Thu Sep  5 22:41:46 CDT 2019
[    35.550] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    35.550] (--) NVIDIA(0):     DFP-0
[    35.550] (--) NVIDIA(0):     DFP-1
[    35.550] (--) NVIDIA(0):     DFP-2 (boot)
[    35.550] (--) NVIDIA(0):     DFP-3
[    35.551] (II) NVIDIA(0): NVIDIA GPU GeForce RTX 2060 (TU106-A) at PCI:1:0:0 (GPU-0)
[    35.551] (--) NVIDIA(0): Memory: 6291456 kBytes
[    35.551] (--) NVIDIA(0): VideoBIOS: 90.06.30.00.ad
[    35.551] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    35.551] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    35.551] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    35.551] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    35.551] (--) NVIDIA(GPU-0): 
[    35.551] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    35.551] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    35.551] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    35.551] (--) NVIDIA(GPU-0): 
[    35.551] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[    35.551] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[    35.551] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[    35.551] (--) NVIDIA(GPU-0): 
[    35.552] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    35.552] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    35.552] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    35.552] (--) NVIDIA(GPU-0): 
[    35.588] (==) NVIDIA(0): 
[    35.588] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    35.588] (==) NVIDIA(0):     will be used as the requested mode.
[    35.588] (==) NVIDIA(0): 
[    35.589] (II) NVIDIA(0): Validated MetaModes:
[    35.589] (II) NVIDIA(0):     "DFP-2:nvidia-auto-select"
[    35.589] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    35.621] (--) NVIDIA(0): DPI set to (69, 68); computed from "UseEdidDpi" X config
[    35.621] (--) NVIDIA(0):     option
[    35.621] (II) UnloadModule: "nouveau"
[    35.621] (II) Unloading nouveau
[    35.621] (II) UnloadModule: "modesetting"
[    35.621] (II) Unloading modesetting
[    35.621] (II) UnloadModule: "fbdev"
[    35.621] (II) Unloading fbdev
[    35.621] (II) UnloadSubModule: "fbdevhw"
[    35.621] (II) Unloading fbdevhw
[    35.621] (II) UnloadModule: "vesa"
[    35.621] (II) Unloading vesa
[    35.622] (II) NVIDIA: Using 24576.00 MB of virtual memory for indirect memory
[    35.622] (II) NVIDIA:     access.
[    35.636] (II) NVIDIA(0): Setting mode "DFP-2:nvidia-auto-select"
[    35.745] (==) NVIDIA(0): Disabling shared memory pixmaps
[    35.745] (==) NVIDIA(0): Backing store enabled
[    35.745] (==) NVIDIA(0): Silken mouse enabled
[    35.745] (==) NVIDIA(0): DPMS enabled
[    35.759] (II) Loading sub module "dri2"
[    35.759] (II) LoadModule: "dri2"
[    35.759] (II) Module "dri2" already built-in
[    35.759] (II) NVIDIA(0): [DRI2] Setup complete
[    35.759] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    35.759] (II) Initializing extension Generic Event Extension
[    35.759] (II) Initializing extension SHAPE
[    35.759] (II) Initializing extension MIT-SHM
[    35.759] (II) Initializing extension XInputExtension
[    35.759] (II) Initializing extension XTEST
[    35.760] (II) Initializing extension BIG-REQUESTS
[    35.760] (II) Initializing extension SYNC
[    35.760] (II) Initializing extension XKEYBOARD
[    35.760] (II) Initializing extension XC-MISC
[    35.760] (II) Initializing extension SECURITY
[    35.760] (II) Initializing extension XFIXES
[    35.760] (II) Initializing extension RENDER
[    35.760] (II) Initializing extension RANDR
[    35.760] (II) Initializing extension COMPOSITE
[    35.760] (II) Initializing extension DAMAGE
[    35.760] (II) Initializing extension MIT-SCREEN-SAVER
[    35.760] (II) Initializing extension DOUBLE-BUFFER
[    35.761] (II) Initializing extension RECORD
[    35.761] (II) Initializing extension DPMS
[    35.761] (II) Initializing extension Present
[    35.761] (II) Initializing extension DRI3
[    35.761] (II) Initializing extension X-Resource
[    35.761] (II) Initializing extension XVideo
[    35.761] (II) Initializing extension XVideo-MotionCompensation
[    35.761] (II) Initializing extension SELinux
[    35.761] (II) SELinux: Disabled on system
[    35.761] (II) Initializing extension GLX
[    35.761] (II) Initializing extension GLX
[    35.761] (II) Indirect GLX disabled.
[    35.761] (II) GLX: Another vendor is already registered for screen 0
[    35.761] (II) Initializing extension XFree86-VidModeExtension
[    35.761] (II) Initializing extension XFree86-DGA
[    35.761] (II) Initializing extension XFree86-DRI
[    35.761] (II) Initializing extension DRI2
[    35.761] (II) Initializing extension NV-GLX
[    35.761] (II) Initializing extension NV-CONTROL
[    35.761] (II) Initializing extension XINERAMA
[    35.863] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.863] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    35.863] (II) LoadModule: "libinput"
[    35.863] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    35.881] (II) Module libinput: vendor="X.Org Foundation"
[    35.881] 	compiled for 1.20.1, module version = 0.28.1
[    35.881] 	Module class: X.Org XInput Driver
[    35.881] 	ABI class: X.Org XInput driver, version 24.1
[    35.881] (II) Using input driver 'libinput' for 'Power Button'
[    35.882] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 39 paused 0
[    35.882] (**) Power Button: always reports core events
[    35.882] (**) Option "Device" "/dev/input/event2"
[    35.882] (**) Option "_source" "server/udev"
[    35.882] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    35.882] (II) event2  - Power Button: device is a keyboard
[    35.882] (II) event2  - Power Button: device removed
[    35.882] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    35.882] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.882] (**) Option "xkb_model" "pc105"
[    35.882] (**) Option "xkb_layout" "us"
[    35.883] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    35.883] (II) event2  - Power Button: device is a keyboard
[    35.883] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    35.883] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    35.883] (II) Using input driver 'libinput' for 'Power Button'
[    35.884] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 42 paused 0
[    35.884] (**) Power Button: always reports core events
[    35.884] (**) Option "Device" "/dev/input/event1"
[    35.884] (**) Option "_source" "server/udev"
[    35.884] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    35.884] (II) event1  - Power Button: device is a keyboard
[    35.884] (II) event1  - Power Button: device removed
[    35.884] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    35.884] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    35.884] (**) Option "xkb_model" "pc105"
[    35.884] (**) Option "xkb_layout" "us"
[    35.884] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    35.884] (II) event1  - Power Button: device is a keyboard
[    35.885] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    35.885] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    35.885] (II) Using input driver 'libinput' for 'Sleep Button'
[    35.885] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 43 paused 0
[    35.885] (**) Sleep Button: always reports core events
[    35.885] (**) Option "Device" "/dev/input/event0"
[    35.885] (**) Option "_source" "server/udev"
[    35.885] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    35.885] (II) event0  - Sleep Button: device is a keyboard
[    35.885] (II) event0  - Sleep Button: device removed
[    35.885] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    35.885] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    35.885] (**) Option "xkb_model" "pc105"
[    35.886] (**) Option "xkb_layout" "us"
[    35.886] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    35.886] (II) event0  - Sleep Button: device is a keyboard
[    35.886] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[    35.886] (II) No input driver specified, ignoring this device.
[    35.886] (II) This device may have been added with another device file.
[    35.886] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[    35.886] (II) No input driver specified, ignoring this device.
[    35.887] (II) This device may have been added with another device file.
[    35.887] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[    35.887] (II) No input driver specified, ignoring this device.
[    35.887] (II) This device may have been added with another device file.
[    35.887] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    35.887] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    35.887] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    35.888] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 44 paused 0
[    35.888] (**) Logitech USB Receiver: always reports core events
[    35.888] (**) Option "Device" "/dev/input/event3"
[    35.888] (**) Option "_source" "server/udev"
[    35.888] (II) event3  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    35.888] (II) event3  - Logitech USB Receiver: device is a keyboard
[    35.888] (II) event3  - Logitech USB Receiver: device removed
[    35.888] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:046D:C534.0001/input/input3/event3"
[    35.888] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    35.888] (**) Option "xkb_model" "pc105"
[    35.888] (**) Option "xkb_layout" "us"
[    35.889] (II) event3  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    35.889] (II) event3  - Logitech USB Receiver: device is a keyboard
[    35.889] (II) config/udev: Adding input device Logitech USB Receiver Mouse (/dev/input/event4)
[    35.889] (**) Logitech USB Receiver Mouse: Applying InputClass "libinput pointer catchall"
[    35.889] (II) Using input driver 'libinput' for 'Logitech USB Receiver Mouse'
[    35.889] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 45 paused 0
[    35.889] (**) Logitech USB Receiver Mouse: always reports core events
[    35.889] (**) Option "Device" "/dev/input/event4"
[    35.889] (**) Option "_source" "server/udev"
[    35.890] (II) event4  - Logitech USB Receiver Mouse: is tagged by udev as: Mouse
[    35.890] (II) event4  - Logitech USB Receiver Mouse: device is a pointer
[    35.890] (II) event4  - Logitech USB Receiver Mouse: device removed
[    35.890] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C534.0002/input/input4/event4"
[    35.890] (II) XINPUT: Adding extended input device "Logitech USB Receiver Mouse" (type: MOUSE, id 10)
[    35.890] (**) Option "AccelerationScheme" "none"
[    35.890] (**) Logitech USB Receiver Mouse: (accel) selected scheme none/0
[    35.890] (**) Logitech USB Receiver Mouse: (accel) acceleration factor: 2.000
[    35.890] (**) Logitech USB Receiver Mouse: (accel) acceleration threshold: 4
[    35.890] (II) event4  - Logitech USB Receiver Mouse: is tagged by udev as: Mouse
[    35.890] (II) event4  - Logitech USB Receiver Mouse: device is a pointer
[    35.891] (II) config/udev: Adding input device Logitech USB Receiver Mouse (/dev/input/mouse0)
[    35.891] (II) No input driver specified, ignoring this device.
[    35.891] (II) This device may have been added with another device file.
[    35.891] (II) config/udev: Adding input device Logitech USB Receiver Consumer Control (/dev/input/event5)
[    35.891] (**) Logitech USB Receiver Consumer Control: Applying InputClass "libinput keyboard catchall"
[    35.891] (II) Using input driver 'libinput' for 'Logitech USB Receiver Consumer Control'
[    35.892] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 46 paused 0
[    35.892] (**) Logitech USB Receiver Consumer Control: always reports core events
[    35.892] (**) Option "Device" "/dev/input/event5"
[    35.892] (**) Option "_source" "server/udev"
[    35.892] (II) event5  - Logitech USB Receiver Consumer Control: is tagged by udev as: Keyboard
[    35.892] (II) event5  - Logitech USB Receiver Consumer Control: device is a keyboard
[    35.892] (II) event5  - Logitech USB Receiver Consumer Control: device removed
[    35.892] (II) libinput: Logitech USB Receiver Consumer Control: needs a virtual subdevice
[    35.892] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C534.0002/input/input5/event5"
[    35.892] (II) XINPUT: Adding extended input device "Logitech USB Receiver Consumer Control" (type: MOUSE, id 11)
[    35.892] (**) Option "AccelerationScheme" "none"
[    35.892] (**) Logitech USB Receiver Consumer Control: (accel) selected scheme none/0
[    35.892] (**) Logitech USB Receiver Consumer Control: (accel) acceleration factor: 2.000
[    35.892] (**) Logitech USB Receiver Consumer Control: (accel) acceleration threshold: 4
[    35.893] (II) event5  - Logitech USB Receiver Consumer Control: is tagged by udev as: Keyboard
[    35.893] (II) event5  - Logitech USB Receiver Consumer Control: device is a keyboard
[    35.893] (II) config/udev: Adding input device Logitech USB Receiver System Control (/dev/input/event6)
[    35.893] (**) Logitech USB Receiver System Control: Applying InputClass "libinput keyboard catchall"
[    35.893] (II) Using input driver 'libinput' for 'Logitech USB Receiver System Control'
[    35.893] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 47 paused 0
[    35.893] (**) Logitech USB Receiver System Control: always reports core events
[    35.893] (**) Option "Device" "/dev/input/event6"
[    35.893] (**) Option "_source" "server/udev"
[    35.894] (II) event6  - Logitech USB Receiver System Control: is tagged by udev as: Keyboard
[    35.894] (II) event6  - Logitech USB Receiver System Control: device is a keyboard
[    35.894] (II) event6  - Logitech USB Receiver System Control: device removed
[    35.894] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C534.0002/input/input6/event6"
[    35.894] (II) XINPUT: Adding extended input device "Logitech USB Receiver System Control" (type: KEYBOARD, id 12)
[    35.894] (**) Option "xkb_model" "pc105"
[    35.894] (**) Option "xkb_layout" "us"
[    35.894] (II) event6  - Logitech USB Receiver System Control: is tagged by udev as: Keyboard
[    35.894] (II) event6  - Logitech USB Receiver System Control: device is a keyboard
[    35.895] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[    35.895] (II) No input driver specified, ignoring this device.
[    35.895] (II) This device may have been added with another device file.
[    35.895] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[    35.895] (II) No input driver specified, ignoring this device.
[    35.895] (II) This device may have been added with another device file.
[    35.895] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[    35.895] (II) No input driver specified, ignoring this device.
[    35.895] (II) This device may have been added with another device file.
[    35.895] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[    35.895] (II) No input driver specified, ignoring this device.
[    35.895] (II) This device may have been added with another device file.
[    35.895] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[    35.895] (II) No input driver specified, ignoring this device.
[    35.895] (II) This device may have been added with another device file.
[    35.899] (**) Logitech USB Receiver Consumer Control: Applying InputClass "libinput keyboard catchall"
[    35.899] (II) Using input driver 'libinput' for 'Logitech USB Receiver Consumer Control'
[    35.899] (II) systemd-logind: returning pre-existing fd for /dev/input/event5 13:69
[    35.899] (**) Logitech USB Receiver Consumer Control: always reports core events
[    35.899] (**) Option "Device" "/dev/input/event5"
[    35.899] (**) Option "_source" "_driver/libinput"
[    35.899] (II) libinput: Logitech USB Receiver Consumer Control: is a virtual subdevice
[    35.899] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C534.0002/input/input5/event5"
[    35.899] (II) XINPUT: Adding extended input device "Logitech USB Receiver Consumer Control" (type: KEYBOARD, id 13)
[    35.899] (**) Option "xkb_model" "pc105"
[    35.899] (**) Option "xkb_layout" "us"
[    35.900] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[    35.900] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[    35.900] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[    35.900] (--) NVIDIA(GPU-0): 
[    37.188] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    37.188] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    37.188] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    37.188] (--) NVIDIA(GPU-0): 
[    37.188] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    37.188] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    37.188] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    37.188] (--) NVIDIA(GPU-0): 
[    37.188] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[    37.188] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[    37.188] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[    37.188] (--) NVIDIA(GPU-0): 
[    37.189] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    37.189] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    37.189] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    37.189] (--) NVIDIA(GPU-0): 
[    37.262] (II) NVIDIA(0): Setting mode "DP-0: 1920x1080_120 @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[    43.150] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    43.150] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    43.150] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    43.150] (--) NVIDIA(GPU-0): 
[    43.150] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    43.150] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    43.150] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    43.150] (--) NVIDIA(GPU-0): 
[    43.150] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[    43.150] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[    43.150] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[    43.150] (--) NVIDIA(GPU-0): 
[    43.151] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    43.151] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    43.151] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    43.151] (--) NVIDIA(GPU-0): 
[ 88786.712] (--) NVIDIA(GPU-0): DFP-0: disconnected
[ 88786.712] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[ 88786.712] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[ 88786.712] (--) NVIDIA(GPU-0): 
[ 88786.712] (--) NVIDIA(GPU-0): DFP-1: disconnected
[ 88786.713] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[ 88786.713] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[ 88786.713] (--) NVIDIA(GPU-0): 
[ 88786.713] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[ 88786.713] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[ 88786.713] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[ 88786.713] (--) NVIDIA(GPU-0): 
[ 88786.715] (--) NVIDIA(GPU-0): DFP-3: disconnected
[ 88786.715] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[ 88786.715] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[ 88786.715] (--) NVIDIA(GPU-0): 
[ 90063.870] (--) NVIDIA(GPU-0): DFP-0: disconnected
[ 90063.870] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[ 90063.870] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[ 90063.870] (--) NVIDIA(GPU-0): 
[ 90063.870] (--) NVIDIA(GPU-0): DFP-1: disconnected
[ 90063.870] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[ 90063.870] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[ 90063.870] (--) NVIDIA(GPU-0): 
[ 90063.871] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[ 90063.871] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[ 90063.871] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[ 90063.871] (--) NVIDIA(GPU-0): 
[ 90063.873] (--) NVIDIA(GPU-0): DFP-3: disconnected
[ 90063.873] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[ 90063.873] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[ 90063.873] (--) NVIDIA(GPU-0): 
[106786.964] (--) NVIDIA(GPU-0): DFP-0: disconnected
[106786.964] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[106786.964] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[106786.964] (--) NVIDIA(GPU-0): 
[106786.964] (--) NVIDIA(GPU-0): DFP-1: disconnected
[106786.964] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[106786.964] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[106786.964] (--) NVIDIA(GPU-0): 
[106786.964] (--) NVIDIA(GPU-0): INN X315 (DFP-2): connected
[106786.964] (--) NVIDIA(GPU-0): INN X315 (DFP-2): Internal DisplayPort
[106786.964] (--) NVIDIA(GPU-0): INN X315 (DFP-2): 2660.0 MHz maximum pixel clock
[106786.964] (--) NVIDIA(GPU-0): 
[106786.965] (--) NVIDIA(GPU-0): DFP-3: disconnected
[106786.965] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[106786.965] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[106786.965] (--) NVIDIA(GPU-0): 
```

The monitor is the INN X315. It says 'No modes were requested; the default mode "nvidia-auto-select"', so does that mean that the monitor is not stating its modes?

---

### Post by Lucretia on 2019-10-16
> **Autodave said:**
> Do not use the drivers from the 'net.  You are only asking for trouble if you do that.

You said that the monitor is connected to the display port, but are there any adapters being used?  Like display port to VGA, etc?

There are no adapters. Just the display port cable. And it's definitely connected to the graphics card!

---

### Post by CatKiller on 2019-10-17
OK, this part is unusual; the install scripts blacklist the nouveau module so that it never gets loaded in the first place. It's *probably* unrelated, but it could indicate that the driver didn't install as cleanly as it might have.

```
 [    34.353] (==) Matched nouveau as autoconfigured driver 1
...
[    34.353] (II) LoadModule: "nouveau"
[    34.353] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    34.365] (II) Module nouveau: vendor="X.Org Foundation"
[    34.365]     compiled for 1.20.4, module version = 1.0.16
[    34.365]     Module class: X.Org Video Driver
[    34.365]     ABI class: X.Org Video Driver, version 24.0
...
[    34.365] (II) NOUVEAU driver Date:   Mon Jan 28 23:25:58 2019 -0500
[    34.365] (II) NOUVEAU driver for NVIDIA chipset families :
[    34.365]     RIVA TNT            (NV04)
[    34.365]     RIVA TNT2           (NV05)
[    34.365]     GeForce 256         (NV10)
[    34.365]     GeForce 2           (NV11, NV15)
[    34.365]     GeForce 4MX         (NV17, NV18)
[    34.365]     GeForce 3           (NV20)
[    34.365]     GeForce 4Ti         (NV25, NV28)
[    34.365]     GeForce FX          (NV3x)
[    34.365]     GeForce 6           (NV4x)
[    34.365]     GeForce 7           (G7x)
[    34.365]     GeForce 8           (G8x)
[    34.365]     GeForce 9           (G9x)
[    34.365]     GeForce GTX 2xx/3xx (GT2xx)
[    34.365]     GeForce GTX 4xx/5xx (GFxxx)
[    34.365]     GeForce GTX 6xx/7xx (GKxxx)
[    34.365]     GeForce GTX 9xx     (GMxxx)
[    34.365]     GeForce GTX 10xx    (GPxxx)
```

I *think* that because that module gets unloaded again before mode validation, it doesn't affect things - nouveau by itself seems to be pretty bad at detecting resolutions - but it did strike me as out of place, particularly with this line:

```
[    35.761] (II) GLX: Another vendor is already registered for screen 0
```

Actually, strike that: the nouveau module doesn't get unloaded until *after* the modesetting happens; it could be affecting things.

```
[    35.588] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    35.588] (==) NVIDIA(0):     will be used as the requested mode.
[    35.588] (==) NVIDIA(0): 
[    35.589] (II) NVIDIA(0): Validated MetaModes:
[    35.589] (II) NVIDIA(0):     "DFP-2:nvidia-auto-select"
[    35.589] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    35.621] (--) NVIDIA(0): DPI set to (69, 68); computed from "UseEdidDpi" X config
[    35.621] (--) NVIDIA(0):     option
[    35.621] (II) UnloadModule: "nouveau"
[    35.621] (II) Unloading nouveau
```

> **Lucretia said:**
> The monitor is the INN X315. It says 'No modes were requested; the default mode "nvidia-auto-select"', so does that mean that the monitor is not stating its modes?

It's certainly not quite as helpful as it might have been. There is an xorg.conf option, ModeDebug, that makes the mode validation section of the log much more verbose. That will probably specify which modes come from where, and why they're accepted or rejected.

The order of things that I would take in your situation is to first purge and reinstall the nvidia driver to give the install scripts a chance to blacklist all the right things. If the nouveau and vesa modules are messing up the mode detection, that might fix it without having to do anything else.

If that doesn't do it, the next thing is to find out why the mode you want isn't being used. I *think* that you'll only need a snippet in /etc/X11/xorg.conf.d/ to do it, rather than a full-blown xorg.conf, but the last time I needed to play with these things that wasn't an option. So you can create a file, let's call it **/etc/X11/xorg.conf.d/20-nvidia.conf**. In that, put 
```

Section "Device"
    Option  "ModeDebug"     "True"
EndSection

```

and restart X or reboot.

That should, hopefully, point to where the problem is in the log.

There are lots of options to selectively use or ignore the information provided by EDID, in the case that it's *mostly* accurate. I had a monitor that just flat-out lied in its EDID when I was first starting out with Linux; that was fun. Your monitor manufacturer doesn't seem to be terribly forthcoming with the specifications of your monitor. The easy option is to specify HorizSync and VertRefresh and let everything else happen automatically, but the manufacturer doesn't provide those for your monitor on their website as far as I can find. It might be in your manual, or they might tell you if you ask them, or you might need to just make something up based on the specifications of similar monitors.

Bear in mind what I said earlier about if it goes pear-shaped: from the command line (you can often get a virtual TTY with Ctrl-Alt-F2 when you've killed your graphical environment; the graphical environment is probably on Ctrl-Alt-F1, although it might be on -F7), **rm** will delete (remove) a file, and **nano** is an easy-ish command-line text editor. Booting from the install image is also a good way of fixing things when one's fiddling has removed the usual graphical environment.

---

### Post by Lucretia on 2019-10-22
So interestingly, I booted up in Windows to double-check the resolution, and it also maxes out at 1920x1080 with no higher resolution options available. Now that I've looked at the specs more carefully, it looks like there is a Pro version with almost the same part number and a non-pro version, with both monitors being the same size. The non-pro only goes up to 1920x1080, which is what I guess I've got. There's nothing obviously written on the monitor other than the "PRISM+" logo. To make things more confusing, on my first day on the job here, my workmate specifically told me there might be a driver problem because the monitor can't do its max resolution in Ubuntu.

I very much appreciate everyone's help here! Sorry it ended up being a waste of time :-(
When I buy my own hardware, I know what I'm getting!! It's so silly having a huge screen and then being stuck with a low resolution. My monitor at home is 22" and has the same resolution.

---

### Post by CatKiller on 2019-10-23
> **Lucretia said:**
> I very much appreciate everyone's help here! Sorry it ended up being a waste of time :-(

Troubleshooting is good practice, and someone with a similar issue may come across the thread in the future and find the information helpful.

I'm glad to hear you got your issue resolved, although it's a shame you didn't get the outcome you were hoping for.

---

