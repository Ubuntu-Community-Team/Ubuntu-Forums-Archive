---
title: "averaging 175fps in glxgears on Radeon Xpress 200M"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-07-20
I've got a crappy hp zv60000 laptop with an ATI radeon xpress 200M graphics card.  (32MB, but the 128MB version has the exact same results for me)

I had to download and install the driver from ATI because the one I get from apt-get xorg-driver-fglrx doesn't support my 200M.

The open GL drivers are now:
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
which seems to be a step down.  Could this be the issue?

**xorg.conf**
```


Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI0"
	Driver		"fglrx"
#	Option	"NoAccel"	"yes"
	Option	"VideoOverlay"	"on"
	Option	"OpenGLOverlay"	"off"
	Option	"UseInternalAGPGART"	"no"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"ATI0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection


```

---

### Post by s_p_a_r_k_y on 2005-07-20
[QUOTE=OneSeventeen]
```

Section "Device"
	Identifier	"ATI0"
	Driver		"fglrx"
#	Option	"NoAccel"	"yes"
	Option	"VideoOverlay"	"on"
	Option	"OpenGLOverlay"	"off"
	Option	"UseInternalAGPGART"	"no"
	BusID		"PCI:1:5:0"
EndSection



```[/QUOTE]
You need to forcebly tell fglrx that it should use accelleration by the
option "NoAccel" "no"

below will be my fglrx section

```

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 0"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###

```
the rest I don't think is important as its just my dual monitor setup...where I have 2 monitors with two different sets of windows... good stuff.

Also make sure you aren't turning on the composite extension. I think that causes dri to be turned off

---

### Post by OneSeventeen on 2005-07-20
```

Section "Device"
	Identifier	"ATI0"
	Driver		"fglrx"

	Option "no_accel"	"no"
	Option "no_dri"	"no"
	Option "mtrr"	"off"

	BusID		"PCI:1:5:0"
EndSection

```

Still same results :(
**EDIT:**
Actually that knocked me down to 40FPS

---

### Post by OneSeventeen on 2005-07-20
Okay, after trying to reinstall the drivers, when I try to run glxgears I get:
> glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Any ideas what I did?

(I actually tried to install the fglx control pannel, and got an error, assumed it was because I downloaded the driver from ati, so I uninstalled the control pannel and it said it never installed, then I quit X and reinstalled the .deb file using --force-overwrite and restearted X and still no glxgears)

---

### Post by s_p_a_r_k_y on 2005-07-20
[QUOTE=OneSeventeen]Okay, after trying to reinstall the drivers, when I try to run glxgears I get:


Any ideas what I did?

(I actually tried to install the fglx control pannel, and got an error, assumed it was because I downloaded the driver from ati, so I uninstalled the control pannel and it said it never installed, then I quit X and reinstalled the .deb file using --force-overwrite and restearted X and still no glxgears)[/QUOTE]

ummm are you loading the fglrx  kernel module on boot? check /etc/modules and see if its in there? Without it, no accelleration. Also check out /var/log/Xorg.0.log and look for lines like
```
(WW) fglrx(0): Cannot read colourmap from VGA.  Will restore with default
(II) fglrx(0): UMM area:     0xf05e9000 (size=0x07a17000)
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
I'm getting it bc I have the composite extension enabled...disabling that will make dri work for me, but I use the composite extension currently...you should just turn if off.


 You can always add it after boot, but might as well add it on boot. ```
sudo modprobe fglrx
``` after boot, or edit ```
 sudo nano /etc/modules
```

Not sure how you got the missing file.  I checked debian.org's package list and the file is referenced in
 ```

usr/X11R6/lib/debug/libGL.so.1				    libdevel/xlibmesa-gl-dbg
usr/X11R6/lib/libGL.so.1				    libs/xlibmesa-gl
usr/lib/dbg/i686/mmx/cmov/libGL.so.1			    libs/libgl1-mesa-dbg
usr/lib/dbg/libGL.so.1					    libs/libgl1-mesa-dbg
usr/lib/debug/libGL.so.1				    libdevel/xlibmesa-gl-dbg
usr/lib/i686/mmx/cmov/libGL.so.1	  libs/libgl1-mesa-glide3,libs/mesag3
usr/lib/libGL.so.1				libs/libgl1-mesa-glide3

```
So maybe try reinstlaling xlibmesa with gnome off sudo /etc/init.d/gdm stop

Hope it helps...
I keep a few xorg.conf files around like xorg.conf_composite and xorg.conf_dri and xorg.cong_ati_dual_monitor in my /etc/X11/ folder so if I want something like dual monitors (at work) I just copy that over the xorg.conf file and restart gdm sudo /etc/init.d/gdm restart. (never move the file always copy so you retain the originals)

---

### Post by OneSeventeen on 2005-07-21
> 
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko): No such device


I think I really fglrx'd things up on this laptop... I may just reinstall everything...

Should I be patching a kernel or anything when installing the fglrx drivers from ati's website?

**EDIT:** Some Xorg.0.log goodness:
```

(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

### Post by s_p_a_r_k_y on 2005-07-21
why from the ati site?
```

 apt-cache search fglrx
fglrx-control - Control panel for the ATI graphics accelerators
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.10-5-386 - Non-free Linux 2.6.10 modules on 386
linux-restricted-modules-2.6.10-5-686 - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.10-5-686-smp - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules-2.6.10-5-k7 - Non-free Linux 2.6.10 modules on AMD K7
linux-restricted-modules-2.6.10-5-k7-smp - Non-free Linux 2.6.10 modules on AMD K7 SMP
xorg-driver-fglrx - Video driver for ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for ATI graphics accelerators (devel files)
xfree86-driver-fglrx - Video driver for the ATI graphics accelerators
xfree86-driver-fglrx-dev - Video driver for ATI graphics accelerators (devel files)

```
Just download them from the hoary repositories.

```

sudo apt-get intsall xorg-driver-fglrx linux-restricted-modules-2.6.10-5-PLATFORM
```
where you put in either 386 or 686 or k7....depending on what you are using
```
 uname -a
```
will tell you what kernel you are using right now.
Then make sure that you have the fglrx module loaded on boot and give it another try

---

### Post by OneSeventeen on 2005-07-22
The first thing I did was ran:
```
sudo apt-get install linux-restricted-modules-2.6.10-5-386 xorg-driver-fglrx
```

It installed happily and I configured xorg.conf to use "fglrx" instead of "ati"

GDM wouldn't start.

modified xorg.conf about 20 more times

GDM still wouldn't start.


Uninstalled fglrx and downloaded ati's fglrx specifically for the ATI Radeon Xpress 200M and it worked first try.  (just poor/no 3d accelleration)

I just formatted and reinstalled the OS and downloaded the ATI drivers again, and it is working, but still with no more than 200fps in glxgears.  (and modprobe fglrx still gives me a "no such device")

**EDIT:**
I've been poking around and found that there is an fglrx folder in the /lib/modules directory that contains .sh scripts to make the fglrx module, and when I ran the scripts, it gave me a few errors because I didn't have the kernel source, so I'm downloading the kernel source now.

One of the .sh files I ran did give instructions stating that there is no 3d accelleration available until I run /lib/modules/fglrx/build_mod/make.sh then run /lib/modules/fglrx/make_install.sh

running make.sh threw back an error stating kernel includes not found in /usr/src/linux/include so I'm downloading the linux kernel from synaptic now.  I'll post back with updated progress later.

---

### Post by OneSeventeen on 2005-07-22
okay I installed/unpacked the kernel source, or what I thought was the kernel source anyway, and I still get:
> 
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h


And, I must admit, there is no include/linux/version.h in the directory structure.

There's all sorts of other stuff, just no version.h :(

---

### Post by OneSeventeen on 2005-07-22
Okay, I realized I was getting the kernel-headers not the linux-headers and linux-source

I've gotten everything sorted, replaced pci_find_class to pci_get_class in one of the .c files and finally have a working fglrx.ko

I now average 330 FPS... what else can I do to boost performance?

---

### Post by OneSeventeen on 2005-07-28
After upgrading my laptop, and doing a more clean install, I've gotten up to 583FPS in glxgears and 97FPS in fgl-glxgears.

I still see other people with the same model laptop as me getting over 1000FPS in glxgears, anyone know why I'm still half what I should be?  (using the same driver settings in xorg.conf as I listed previously)

---

### Post by s_p_a_r_k_y on 2005-07-28
what resolution are you running at?  I don't know if it matters, but maybe try running it at a lower res? Also check the log file to ensure that DRI is infact on. It seems that its only doing software rendering, not hardware.

---

### Post by OneSeventeen on 2005-07-28
here's a bit from my Xorg.0.log
```

	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(==) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON XPRESS 200M (RS480 5955)" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3085)
(--) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x01
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
*****************************cut*****************************

(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(II) fglrx(0): Panel ID string: SEC                     
(II) fglrx(0): Panel Size from BIOS: 1280x800
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Overlay disabled
(==) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Valid mode using on-chip RMX: 1280x800
(II) fglrx(0): Total 1 valid mode(s) found.
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816
(==) fglrx(0): DPI set to (75, 75)
***************************cut*************************

(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.13.4
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000003e3
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```

And a more useful looking area of the log:
```


(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0cfd000
(II) fglrx(0): [drm] mapped SAREA 0xe0cfd000 to 0xb7da1000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.13.4
(II) fglrx(0):     Date: Jun 21 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xb0100000
(II) fglrx(0): [agp] Mode=0x0f000217 bridge: 0x1002/0x5950
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] It's RS400/RS480 family! Don't enable agp!
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xe8f81000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): FBADPhys: 0x20000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
Symbol R200_MMREADULONG_INDEX from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol R200_MMREADULONG_INDEX from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!

```

I don't like the unresolved thing....

And should I be specifying somewhere that it has 128MB of video RAM?

unfortunately 1280x800 is the only way this looks halfway decent, so I'll put up with lower FPS if I have to, but the others I mentioned getting over 1k were at the same resolution as me.

---

### Post by Jiilik on 2005-07-28
Since you have the RS480 chipset, it could be that your system is not using DMA for hardware access with kernel 2.6.10 -- 2.6.11 significantly speeds things up for me (especially disk access, but everything gets faster as a result).

Since you are building fglrx manually anyway, you can grab 2.6.11 from Hoary/universe - grab the sources as well so you can rebuild the fglrx.ko

---

### Post by OneSeventeen on 2005-07-28
[QUOTE=Jiilik]Since you have the RS480 chipset, it could be that your system is not using DMA for hardware access with kernel 2.6.10 -- 2.6.11 significantly speeds things up for me (especially disk access, but everything gets faster as a result).

Since you are building fglrx manually anyway, you can grab 2.6.11 from Hoary/universe - grab the sources as well so you can rebuild the fglrx.ko[/QUOTE]
 Now, after upgrading to 2.6.11, how would that affect ndiswrapper and my wireless setup?

I've heard of many people downgrading specifically for this purpose.

Ironically, ever since getting the module working, OpenGL works better, but not great, so blender3d is actually slower now, whereas all my screen savers and overall window management is faster.

---

### Post by locutus42 on 2006-03-01
For those who might find this thread, the issues here were this:
1) the default 2.6.10 kernel in Hoary did not support DMA disk access
2) The default 2.6.10 kernel in Hoary didn't handly a BIOS flaw causing the CPU to work 2x harder
3) Only one ATI driver I found would work with 3D and that required a small change in its cource file

All this is/was handled with this script:
[http://ubuntuforums.org/showthread.php?t=65089](http://ubuntuforums.org/showthread.php?t=65089)

I still use it today on test partitions. Of note though, one should upgrade the system before running the script( sudo apt-get update; sudo apt-get upgrade ).

Over the holidays, I tried Breezy and the latest ATI driver and still couldn't get 3D working. With these fixes in place, IIRC, expect glxgears number around 1200FPS and fglxgears numbers around 200FPS

---

