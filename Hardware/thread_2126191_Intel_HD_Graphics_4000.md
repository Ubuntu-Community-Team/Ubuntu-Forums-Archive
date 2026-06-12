---
title: "Intel HD Graphics 4000"
date: 2013-03-16
forum: Hardware
---

### Post by Vind on 2013-03-16
Hi there,

After quite a bit of searching the net, and not finding a satisfying answer, I'm posting here to see if anyone can shed a bit of light on the matter for me.

I've currently installed Ubuntu 12.10 64-bit on an HP pavilion dv-7 laptop. All is well, but I only seem to be able to run the desktop in 2D. The laptop has 2 GPU's: an integrated Intel HD graphics 4000 and a Nvidia Geforce 630M GT. When I installed Ubuntu I gave up trying to install the Nvidia drivers as it seemed to conflict with the integrated GPU, giving me all kinds of problems. Is it possible to run 3D desktop using the Intel GPU or is it only capable of running the 2D invironment? I've read about Bumblebee project, which enables the choice of GPU to use but I don't want to install it as I am not the only user of the PC (other users are even newbier to this OS than I am :) ) and I would like to see if it is possible to get a 3D environment permanently using the Intel GPU or if there is a work-around for the double GPU conflicts.

Thank you very much for your time and for any information you might be able to share on the matter.

---

### Post by sudodus on 2013-03-16
I think Bumblebee is the right track. Until you can install it, you have to bear with the free drivers, that come with the kernel. One possibility is to install dual (or triple if you have Windows) boot, one standard Ubuntu for your everyday tasks and for the other users, and one experimental Ubuntu, where you tweak your system until you get the full power of the graphics.

---

### Post by Vind on 2013-03-17
Hi again,

Thanks for your reply. As i thought it seems that I will have to keep the 2D environment for a while at least untill both GPU's can operate without conflicts. My doubt still remains though, can an Intel HD graphics 4000 run a 3D desktop environment? or os it necessary to have an NVIDIA or AMD GPU for the 3D environment to work?

Thanks again.

---

### Post by sudodus on 2013-03-18
> **Vind said:**
> Hi again,

Thanks for your reply. As i thought it seems that I will have to keep the 2D environment for a while at least untill both GPU's can operate without conflicts. My doubt still remains though, can an Intel HD graphics 4000 run a 3D desktop environment? or os it necessary to have an NVIDIA or AMD GPU for the 3D environment to work?

Thanks again.

I cannot check that now, but I'll be back later, when I get an opportunity to run a computer with intel graphics.

*Edit*: Sorry, the computer that I thought has intel graphics, actually has ATI graphics but uses the built-in free drivers. So I cannot test it with a reasonably modern intel graphics chip. I hope someone else can answer your question :-)

---

### Post by sudodus on 2013-03-18
I tested Intel graphics with an old IBM Thinkcentre with intel 82865G integrated graphics. Knoppix 7.04 runs Compiz and you can see the 3D cube in the attached photo of the screen with a window showing the hardinfo report.

---

### Post by Yellow Pasque on 2013-03-18
> All is well, but I only seem to be able to run the desktop in 2D
Intel HD4000 can run 3D/Unity/Compiz just fine. If you're stuck without 3D, that means you borked the 3D when you tried to install nvidia drivers and you didn't completely remove them.

Try this first:
```
sudo apt-get purge nvidia-current
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```
Reboot. If it doesn't work, post /var/log/Xorg.0.log

---

### Post by Vind on 2013-03-18
Thanks to both of you for your reply.

I can't get onto the laptop at the moment as it is currently being used. I'll try it out later and I'll keep you updated.

I appreciate the time you guys are spending, thanks a bunch :D

---

### Post by Vind on 2013-03-18
Hi again,

I've tried the comands above with no luck. 

```
sudo rm /etc/X11/xorg.conf
```

returns

```
rm: no se puede borrar «/etc/X11/xorg.conf»: No existe el archivo o el directorio
```

Meaning can't remove etc/X11... the file does not exist.

After running:

```
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
``` and restarting all reamians the same.

Now posting /var/log/Xorg.0.log 

```

[    16.308] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    16.308] X Protocol Version 11, Revision 0
[    16.308] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    16.308] Current Operating System: Linux ana-HP-Pavilion-dv7-Notebook-PC 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64
[    16.308] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=2d6d74e7-5db4-4fd0-9b7c-0a2973352bab ro quiet splash vt.handoff=7
[    16.308] Build Date: 27 November 2012  07:44:35AM
[    16.308] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    16.308] Current version of pixman: 0.26.0
[    16.308] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.308] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.308] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 18 21:06:53 2013
[    16.320] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.320] (==) No Layout section.  Using the first Screen section.
[    16.320] (==) No screen section available. Using defaults.
[    16.320] (**) |-->Screen "Default Screen Section" (0)
[    16.320] (**) |   |-->Monitor "<default monitor>"
[    16.320] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.320] (==) Automatically adding devices
[    16.320] (==) Automatically enabling devices
[    16.320] (==) Automatically adding GPU devices
[    16.320] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.320] 	Entry deleted from font path.
[    16.320] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    16.320] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.320] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.320] (II) Loader magic: 0x7f79460eec40
[    16.320] (II) Module ABI versions:
[    16.320] 	X.Org ANSI C Emulation: 0.4
[    16.320] 	X.Org Video Driver: 13.0
[    16.320] 	X.Org XInput driver : 18.0
[    16.320] 	X.Org Server Extension : 7.0
[    16.321] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.497] (--) PCI:*(0:0:2:0) 8086:0166:103c:181d rev 9, Mem @ 0xd4000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    16.497] (--) PCI: (0:1:0:0) 10de:0de9:103c:181d rev 161, Mem @ 0xd2000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    16.497] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.497] Initializing built-in extension Generic Event Extension
[    16.497] Initializing built-in extension SHAPE
[    16.497] Initializing built-in extension MIT-SHM
[    16.497] Initializing built-in extension XInputExtension
[    16.497] Initializing built-in extension XTEST
[    16.497] Initializing built-in extension BIG-REQUESTS
[    16.497] Initializing built-in extension SYNC
[    16.497] Initializing built-in extension XKEYBOARD
[    16.497] Initializing built-in extension XC-MISC
[    16.497] Initializing built-in extension SECURITY
[    16.497] Initializing built-in extension XINERAMA
[    16.497] Initializing built-in extension XFIXES
[    16.497] Initializing built-in extension RENDER
[    16.497] Initializing built-in extension RANDR
[    16.497] Initializing built-in extension COMPOSITE
[    16.497] Initializing built-in extension DAMAGE
[    16.497] Initializing built-in extension MIT-SCREEN-SAVER
[    16.497] Initializing built-in extension DOUBLE-BUFFER
[    16.497] Initializing built-in extension RECORD
[    16.497] Initializing built-in extension DPMS
[    16.497] Initializing built-in extension X-Resource
[    16.497] Initializing built-in extension XVideo
[    16.497] Initializing built-in extension XVideo-MotionCompensation
[    16.497] Initializing built-in extension XFree86-VidModeExtension
[    16.497] Initializing built-in extension XFree86-DGA
[    16.497] Initializing built-in extension XFree86-DRI
[    16.497] Initializing built-in extension DRI2
[    16.497] (II) LoadModule: "glx"
[    16.507] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.508] (II) Module glx: vendor="X.Org Foundation"
[    16.508] 	compiled for 1.13.0, module version = 1.0.0
[    16.508] 	ABI class: X.Org Server Extension, version 7.0
[    16.508] (==) AIGLX enabled
[    16.508] Loading extension GLX
[    16.508] (==) Matched intel as autoconfigured driver 0
[    16.508] (==) Matched intel as autoconfigured driver 1
[    16.508] (==) Matched vesa as autoconfigured driver 2
[    16.508] (==) Matched modesetting as autoconfigured driver 3
[    16.508] (==) Matched fbdev as autoconfigured driver 4
[    16.508] (==) Assigned the driver to the xf86ConfigLayout
[    16.508] (II) LoadModule: "intel"
[    16.508] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.508] (II) Module intel: vendor="X.Org Foundation"
[    16.508] 	compiled for 1.13.0, module version = 2.20.9
[    16.508] 	Module class: X.Org Video Driver
[    16.508] 	ABI class: X.Org Video Driver, version 13.0
[    16.508] (II) LoadModule: "vesa"
[    16.508] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.508] (II) Module vesa: vendor="X.Org Foundation"
[    16.508] 	compiled for 1.12.99.902, module version = 2.3.2
[    16.508] 	Module class: X.Org Video Driver
[    16.508] 	ABI class: X.Org Video Driver, version 13.0
[    16.508] (II) LoadModule: "modesetting"
[    16.508] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.508] (II) Module modesetting: vendor="X.Org Foundation"
[    16.508] 	compiled for 1.13.0, module version = 0.5.0
[    16.508] 	Module class: X.Org Video Driver
[    16.508] 	ABI class: X.Org Video Driver, version 13.0
[    16.508] (II) LoadModule: "fbdev"
[    16.509] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.509] (II) Module fbdev: vendor="X.Org Foundation"
[    16.509] 	compiled for 1.12.99.902, module version = 0.4.3
[    16.509] 	Module class: X.Org Video Driver
[    16.509] 	ABI class: X.Org Video Driver, version 13.0
[    16.509] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
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
[    16.509] (II) VESA: driver for VESA chipsets: vesa
[    16.509] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.509] (II) FBDEV: driver for framebuffer: fbdev
[    16.509] (++) using VT number 7

[    16.509] (II) intel(0): using device path '/dev/dri/card0'
[    16.509] (WW) Falling back to old probe method for vesa
[    16.509] (WW) Falling back to old probe method for modesetting
[    16.509] (WW) Falling back to old probe method for fbdev
[    16.509] (II) Loading sub module "fbdevhw"
[    16.509] (II) LoadModule: "fbdevhw"
[    16.510] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.510] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.510] 	compiled for 1.13.0, module version = 0.0.2
[    16.510] 	ABI class: X.Org Video Driver, version 13.0
[    16.510] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.510] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.510] (==) intel(0): RGB weight 888
[    16.510] (==) intel(0): Default visual is TrueColor
[    16.510] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    16.510] (**) intel(0): Relaxed fencing enabled
[    16.510] (**) intel(0): Wait on SwapBuffers? enabled
[    16.510] (**) intel(0): Triple buffering? enabled
[    16.510] (**) intel(0): Framebuffer tiled
[    16.510] (**) intel(0): Pixmaps tiled
[    16.510] (**) intel(0): 3D buffers tiled
[    16.510] (**) intel(0): SwapBuffers wait enabled
[    16.510] (==) intel(0): video overlay key set to 0x101fe
[    16.510] (II) intel(0): Output LVDS1 has no monitor section
[    16.540] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    16.540] (II) intel(0): Output VGA1 has no monitor section
[    16.556] (II) intel(0): Output HDMI1 has no monitor section
[    16.604] (II) intel(0): Output DP1 has no monitor section
[    16.604] (II) intel(0): EDID for output LVDS1
[    16.604] (II) intel(0): Manufacturer: SEC  Model: 3454  Serial#: 0
[    16.604] (II) intel(0): Year: 2011  Week: 0
[    16.604] (II) intel(0): EDID Version: 1.3
[    16.604] (II) intel(0): Digital Display Input
[    16.604] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    16.604] (II) intel(0): Gamma: 2.20
[    16.604] (II) intel(0): No DPMS capabilities specified
[    16.604] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.604] (II) intel(0): First detailed timing is preferred mode
[    16.604] (II) intel(0): redX: 0.615 redY: 0.362   greenX: 0.348 greenY: 0.624
[    16.604] (II) intel(0): blueX: 0.146 blueY: 0.075   whiteX: 0.313 whiteY: 0.329
[    16.604] (II) intel(0): Manufacturer's mask: 0
[    16.604] (II) intel(0): Supported detailed timing:
[    16.604] (II) intel(0): clock: 107.8 MHz   Image Size:  382 x 215 mm
[    16.604] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1932 h_border: 0
[    16.604] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 907 v_blanking: 930 v_border: 0
[    16.604] (II) intel(0): Unknown vendor-specific block f
[    16.604] (II) intel(0):  SAMSUNG
[    16.604] (II) intel(0):  173KT02-H01
[    16.604] (II) intel(0): EDID (in hex):
[    16.604] (II) intel(0): 	00ffffffffffff004ca3543400000000
[    16.604] (II) intel(0): 	00150103802615780ab3959d5c599f25
[    16.604] (II) intel(0): 	13505400000001010101010101010101
[    16.604] (II) intel(0): 	0101010101011c2a404c61841e303020
[    16.604] (II) intel(0): 	25007ed7100000190000000f00000000
[    16.604] (II) intel(0): 	00000000002efa067800000000fe0053
[    16.604] (II) intel(0): 	414d53554e470a2020202020000000fe
[    16.604] (II) intel(0): 	003137334b5430322d4830310a200007
[    16.604] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    16.604] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    16.604] (II) intel(0): Printing probed modes for output LVDS1
[    16.604] (II) intel(0): Modeline "1600x900"x60.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    16.604] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    16.604] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    16.604] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    16.604] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    16.604] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    16.604] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    16.604] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    16.604] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    16.604] (II) intel(0): EDID for output VGA1
[    16.620] (II) intel(0): EDID for output HDMI1
[    16.668] (II) intel(0): EDID for output DP1
[    16.668] (II) intel(0): Output LVDS1 connected
[    16.668] (II) intel(0): Output VGA1 disconnected
[    16.668] (II) intel(0): Output HDMI1 disconnected
[    16.668] (II) intel(0): Output DP1 disconnected
[    16.668] (II) intel(0): Using exact sizes for initial modes
[    16.668] (II) intel(0): Output LVDS1 using initial mode 1600x900
[    16.668] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.668] (II) intel(0): Kernel page flipping support detected, enabling
[    16.668] (==) intel(0): DPI set to (96, 96)
[    16.668] (II) Loading sub module "fb"
[    16.668] (II) LoadModule: "fb"
[    16.668] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.668] (II) Module fb: vendor="X.Org Foundation"
[    16.668] 	compiled for 1.13.0, module version = 1.0.0
[    16.668] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.668] (II) Loading sub module "dri2"
[    16.668] (II) LoadModule: "dri2"
[    16.668] (II) Module "dri2" already built-in
[    16.668] (II) UnloadModule: "vesa"
[    16.668] (II) Unloading vesa
[    16.668] (II) UnloadModule: "modesetting"
[    16.668] (II) Unloading modesetting
[    16.668] (II) UnloadModule: "fbdev"
[    16.668] (II) Unloading fbdev
[    16.668] (II) UnloadSubModule: "fbdevhw"
[    16.668] (II) Unloading fbdevhw
[    16.668] (==) Depth 24 pixmap format is 32 bpp
[    16.668] (II) intel(0): [DRI2] Setup complete
[    16.668] (II) intel(0): [DRI2]   DRI driver: i965
[    16.668] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[    16.669] (II) UXA(0): Driver registered support for the following operations:
[    16.669] (II)         solid
[    16.669] (II)         copy
[    16.669] (II)         composite (RENDER acceleration)
[    16.669] (II)         put_image
[    16.669] (II)         get_image
[    16.669] (==) intel(0): Backing store disabled
[    16.669] (==) intel(0): Silken mouse enabled
[    16.669] (II) intel(0): Initializing HW Cursor
[    16.669] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.840] (==) intel(0): DPMS enabled
[    16.840] (==) intel(0): Intel XvMC decoder enabled
[    16.840] (II) intel(0): Set up textured video
[    16.840] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    16.840] (II) intel(0): direct rendering: DRI2 Enabled
[    16.840] (==) intel(0): hotplug detection: "enabled"
[    16.860] (--) RandR disabled
[    16.865] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.865] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.865] (II) AIGLX: enabled GLX_ARB_create_context
[    16.865] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.865] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.865] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.865] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.865] (II) AIGLX: Loaded and initialized i965
[    16.865] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.865] (II) intel(0): Setting screen physical size to 423 x 238
[    16.869] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.871] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.871] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.871] (II) LoadModule: "evdev"
[    16.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.871] (II) Module evdev: vendor="X.Org Foundation"
[    16.871] 	compiled for 1.13.0, module version = 2.7.3
[    16.871] 	Module class: X.Org XInput Driver
[    16.871] 	ABI class: X.Org XInput driver, version 18.0
[    16.871] (II) Using input driver 'evdev' for 'Power Button'
[    16.871] (**) Power Button: always reports core events
[    16.871] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.871] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.871] (--) evdev: Power Button: Found keys
[    16.871] (II) evdev: Power Button: Configuring as keyboard
[    16.871] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.871] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.871] (**) Option "xkb_rules" "evdev"
[    16.871] (**) Option "xkb_model" "pc105"
[    16.871] (**) Option "xkb_layout" "es"
[    16.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    16.872] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    16.872] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.872] (II) Using input driver 'evdev' for 'Video Bus'
[    16.872] (**) Video Bus: always reports core events
[    16.872] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    16.872] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.872] (--) evdev: Video Bus: Found keys
[    16.872] (II) evdev: Video Bus: Configuring as keyboard
[    16.873] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    16.873] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.873] (**) Option "xkb_rules" "evdev"
[    16.873] (**) Option "xkb_model" "pc105"
[    16.873] (**) Option "xkb_layout" "es"
[    16.873] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    16.873] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.873] (II) Using input driver 'evdev' for 'Video Bus'
[    16.873] (**) Video Bus: always reports core events
[    16.873] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    16.873] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.873] (--) evdev: Video Bus: Found keys
[    16.873] (II) evdev: Video Bus: Configuring as keyboard
[    16.873] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input7/event7"
[    16.873] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    16.873] (**) Option "xkb_rules" "evdev"
[    16.873] (**) Option "xkb_model" "pc105"
[    16.873] (**) Option "xkb_layout" "es"
[    16.873] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.873] (II) No input driver specified, ignoring this device.
[    16.873] (II) This device may have been added with another device file.
[    16.873] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.873] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event3)
[    16.873] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    16.873] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    16.873] (**) HP Truevision HD: always reports core events
[    16.873] (**) evdev: HP Truevision HD: Device: "/dev/input/event3"
[    16.874] (--) evdev: HP Truevision HD: Vendor 0xbda Product 0x58d8
[    16.874] (--) evdev: HP Truevision HD: Found keys
[    16.874] (II) evdev: HP Truevision HD: Configuring as keyboard
[    16.874] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    16.874] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 9)
[    16.874] (**) Option "xkb_rules" "evdev"
[    16.874] (**) Option "xkb_model" "pc105"
[    16.874] (**) Option "xkb_layout" "es"
[    16.874] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    16.874] (II) No input driver specified, ignoring this device.
[    16.874] (II) This device may have been added with another device file.
[    16.874] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    16.874] (II) No input driver specified, ignoring this device.
[    16.874] (II) This device may have been added with another device file.
[    16.874] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    16.874] (II) No input driver specified, ignoring this device.
[    16.874] (II) This device may have been added with another device file.
[    16.874] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    16.874] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.874] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.874] (**) AT Translated Set 2 keyboard: always reports core events
[    16.874] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    16.874] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.874] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.874] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.874] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    16.874] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    16.874] (**) Option "xkb_rules" "evdev"
[    16.874] (**) Option "xkb_model" "pc105"
[    16.874] (**) Option "xkb_layout" "es"
[    16.875] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    16.875] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.875] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.875] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    16.875] (II) LoadModule: "synaptics"
[    16.875] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.875] (II) Module synaptics: vendor="X.Org Foundation"
[    16.875] 	compiled for 1.12.99.905, module version = 1.6.2
[    16.875] 	Module class: X.Org XInput Driver
[    16.875] 	ABI class: X.Org XInput driver, version 18.0
[    16.875] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.875] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.875] (**) Option "Device" "/dev/input/event6"
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5666
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4772
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    16.875] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.875] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.875] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    16.875] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    16.875] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.875] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    16.875] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    16.875] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.875] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.876] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.876] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.876] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.876] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.876] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.876] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event4)
[    16.876] (II) No input driver specified, ignoring this device.
[    16.876] (II) This device may have been added with another device file.
[    16.876] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    16.876] (II) No input driver specified, ignoring this device.
[    16.876] (II) This device may have been added with another device file.
[    16.877] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    16.877] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    16.877] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    16.877] (**) HP WMI hotkeys: always reports core events
[    16.877] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event5"
[    16.877] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    16.877] (--) evdev: HP WMI hotkeys: Found keys
[    16.877] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    16.877] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    16.877] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    16.877] (**) Option "xkb_rules" "evdev"
[    16.877] (**) Option "xkb_model" "pc105"
[    16.877] (**) Option "xkb_layout" "es"
[    16.880] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    16.880] (II) No input driver specified, ignoring this device.
[    16.880] (II) This device may have been added with another device file.
[    16.880] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    16.880] (II) No input driver specified, ignoring this device.
[    16.880] (II) This device may have been added with another device file.
[    16.880] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    16.880] (II) No input driver specified, ignoring this device.
[    16.880] (II) This device may have been added with another device file.
[    16.882] (II) intel(0): EDID vendor "SEC", prod id 13396
[    16.882] (II) intel(0): Printing DDC gathered Modelines:
[    16.882] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    17.465] (II) intel(0): EDID vendor "SEC", prod id 13396
[    17.465] (II) intel(0): Printing DDC gathered Modelines:
[    17.465] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    18.301] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    21.927] (II) XKB: reuse xkmfile /var/lib/xkb/server-1EEA8A8B5282F1A1C5B4CDBD09D3AB33A69761C2.xkm
[    36.642] (II) intel(0): EDID vendor "SEC", prod id 13396
[    36.642] (II) intel(0): Printing DDC gathered Modelines:
[    36.642] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    36.887] (II) intel(0): EDID vendor "SEC", prod id 13396
[    36.887] (II) intel(0): Printing DDC gathered Modelines:
[    36.887] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    36.978] (II) intel(0): EDID vendor "SEC", prod id 13396
[    36.978] (II) intel(0): Printing DDC gathered Modelines:
[    36.978] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    37.636] (II) intel(0): EDID vendor "SEC", prod id 13396
[    37.636] (II) intel(0): Printing DDC gathered Modelines:
[    37.636] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    37.946] (II) XKB: reuse xkmfile /var/lib/xkb/server-1EEA8A8B5282F1A1C5B4CDBD09D3AB33A69761C2.xkm
[    57.275] (II) intel(0): EDID vendor "SEC", prod id 13396
[    57.275] (II) intel(0): Printing DDC gathered Modelines:
[    57.275] (II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)

```

Thanks again.

---

### Post by Vind on 2013-03-19
Hi,

This is quite embarrasing... It turned out to be quite a simple solution and there I was trying all sorts of technical stuff, well you live and learn.

It was just a case of downloading CCSM. In the past I would have sworn that CCSM came with effects like wobbly windows, cube etc. It turns out I thought I was in 2D mode because the 3D environment felt that way due to the limitted tweaks CCSM installed itself initially. Once downloaded the extra effects for compiz things worked as I am used to.

Thank you both for your time and effort.

---

