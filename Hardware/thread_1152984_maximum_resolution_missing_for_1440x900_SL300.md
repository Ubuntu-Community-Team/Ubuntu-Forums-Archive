---
title: "maximum resolution missing for 1440x900 SL300"
date: 2009-05-08
forum: Hardware
---

### Post by uiberto on 2009-05-08
Hi,

I recently bought a new Thinkpad SL300 with a 1440x900 resolution. Ubuntu is only detecting a 1280x800 resolution. I've been searching the forums for ideas on how to fix this. I was surprised how many people have had similar problems. I've had no luck. I even went so far as to call Lenovo to make sure the unit was shipped with a 1440x900 LCD.

I've attached my lshw, lspci, glxinfo, and Intel driver versions.

If anyone can help, I'd appreciate it!


lshw -c display
```
$ sudo lshw -c display  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

lspci
```

$ lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Int
egrated Graphics Controller (rev 07)
	Subsystem: Lenovo Device 20e4
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	Memory at fdc00000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5c00 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable+
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated
 Graphics Controller (rev 07)
	Subsystem: Lenovo Device 20e4
	Flags: bus master, fast devsel, latency 0
	Memory at fdb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

```

intel drivers
```

$ sudo dpkg --list | grep -i intel
ii  libdrm-intel1                              2.4.5-0ubuntu4                     Userspace interface to intel-specific kernel
ii  whois                                      4.7.30                             an intelligent whois client
rc  xserver-xorg-video-intel                   2:2.6.3-0ubuntu9                   X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-intel-2.4               2:2.4.1-1ubuntu11~ppa1             X.Org X server -- Intel i8xx, i9xx display d

```

/etc/X11/xorg.conf
```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "intel"
EndSection

Section "Monitor"
	Identifier	      "SyncMaster"
	Option		"DPMS"
	Modeline 	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection

Section "Screen"
	Identifier	      "Default Screen"
	Device	      "Screen"
	DefaultDepth	24
       SubSection            "Display"
	Depth		24
	Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection

```

glxinfo
```

$ glxinfo | grep -i renderer
Failed to initialize GEM.  Falling back to classic.
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20090326 2009Q1 RC2 x86/MMX/SSE2

```

---

### Post by unutbu on 2009-05-08
Have you tried this: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) ?

---

### Post by uiberto on 2009-05-08
Hi,

Thanks for the quick reply. I tried using xrandr before with no success. Here are my results:

```

$ sudo xrandr --newmode "1440x900_60.00" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+   50.0  
HDMI-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
  1440x900_60.00 (0xaf)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz

$ sudo xrandr --addmode LVDS "1440x900_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  27
  Current serial number in output stream:  28


```

---

### Post by uiberto on 2009-05-08
Here's my /var/log/Xorg.0.log:

```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux payaso 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May  8 08:33:47 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xfdc00000/4194304, 0xd0000000/268435456, I/O @ 0x00005c00/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Mobile Intel® GM45 Express Chipset
(--) intel(0): Chipset: "Mobile Intel® GM45 Express Chipset"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFDC00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32704 kB
(II) intel(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA has no monitor section
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): Output HDMI-1 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_B" initialized.
(II) intel(0): HDMI output 1 detected
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output HDMI-1 disconnected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 32764 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0x80000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, not ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x00000120 to 0x38000120
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x18000400
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000206 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000206 to 0x00000206
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x100000d0 to 0x000c0010
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0xa9028c00 to 0x21001900
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 482816 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1931260 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
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
(II) intel(0): [drm] Registers = 0xfdc00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0100000, handle = 0xd0100000
(II) intel(0): [drm] mapped back buffer at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] mapped depth buffer at 0xd2640000, handle = 0xd2640000
(II) intel(0): [drm] mapped classic textures at 0xd2c80000, handle = 0xd2c80000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fff000 (pgoffset 8191)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02640000 (pgoffset 9792)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x02c80000 (pgoffset 11392)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00083fff: compressed frame buffer (400 kB, 0x000000007e020000 physical
)
(II) intel(0): 0x00084000-0x0008dfff: HW cursors (40 kB)
(II) intel(0): 0x0008e000-0x00095fff: logical 3D context (32 kB)
(II) intel(0): 0x00096000-0x000a7fff: exa G965 state buffer (72 kB)
(II) intel(0): 0x000a8000-0x000a8fff: power context (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x01fff000:            end of stolen memory
(II) intel(0): 0x01fff000-0x01ffffff: HW status (4 kB)
(II) intel(0): 0x02000000-0x0263ffff: back buffer (6400 kB) X tiled
(II) intel(0): 0x02640000-0x02c7ffff: depth buffer (6400 kB) Y tiled
(II) intel(0): 0x02c80000-0x04c7ffff: classic textures (32768 kB)
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
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 2296
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: Enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 286 x 179
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AlpsPS/2 ALPS DualPoint TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
(II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
(II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
(II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS DualPoint TouchPad. Applying customised settings...
(--) AlpsPS/2 ALPS DualPoint TouchPad touchpad found
(**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS DualPoint TouchPad touchpad found
(II) config/hal: Adding input device DualPoint Stick
(**) DualPoint Stick: always reports core events
(**) DualPoint Stick: Device: "/dev/input/event6"
(II) DualPoint Stick: Found 3 mouse buttons
(II) DualPoint Stick: Found x and y relative axes
(II) DualPoint Stick: Configuring as mouse
(**) DualPoint Stick: YAxisMapping: buttons 4 and 5
(**) DualPoint Stick: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
(**) DualPoint Stick: (accel) keeping acceleration scheme 1
(**) DualPoint Stick: (accel) filter chain progression: 2.00
(**) DualPoint Stick: (accel) filter stage 0: 20.00 ms
(**) DualPoint Stick: (accel) set acceleration profile 0
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): EDID vendor "LEN", prod id 16497
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.50  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x0.0   62.14  1280 1328 1360 1510  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16497

```

---

### Post by unutbu on 2009-05-08
Sorry uiberto, I don't know the answer to this.
Do you think it might be a bug somewhere in Ubuntu? Your situation sounds somewhat similar to this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/365973](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/365973)

---

### Post by uiberto on 2009-05-08
Thanks, I will look at that bug.

Here is my get-edid output (installed from the read-edid package):

```

$ sudo get-edid
get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;q@&#65533;x&#65533;&#65533;&#1366;YV&#65533;&PT&#65533;P 00 6&#65533;F&#65533;P 00 6&#65533;&#65533;
2&#65533;
(	2

```

Yuck, it pukes at the end of the output.

---

### Post by unutbu on 2009-05-08
My get-edid output looks even worse than yours:

```
% sudo get-edid
get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
[B]	Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.[/B]

```

Somehow my monitor's resolution is detected correctly anyway.

---

### Post by unutbu on 2009-05-08
I don't know if this will fix the problem, but this line in your xorg.conf is wrong:
```

	DisplaySize 	1440 900
```

DisplaySize sets the width and height of the physical screen in units of mm.

So at 96 dpi, your DisplaySize line should read
```

	DisplaySize 	381 238
```

See [http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

---

