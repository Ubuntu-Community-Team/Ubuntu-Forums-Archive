---
title: "Screen resolution stuck at 800x600"
date: 2009-07-05
forum: Hardware
---

### Post by Cams on 2009-07-05
I just installed Ubuntu 9.04 on an old laptop and it has installed well and even the wireless pcmcia card works! However the display is stuck at 800x600 and there is no option to go to 1024x768, which is the display's native resolution.

It has a Trident Microsystems CyberBlade i1 graphics cards. System > Preferences > Display says Monitor: Unknown.

How can I fix this to get it to 1024x768? 

I've looked through the forum and found one [potentially useful thread]("http://ubuntuforums.org/showthread.php?t=1181069&highlight=Screen+resolution+stuck+800x600") but I can't replicate the solution.

---

### Post by ivanvajar on 2009-07-05
Did you enable proprietary drivers? System/Administration/Hardware drivers

---

### Post by influanza99 on 2009-07-05
I have same problem. I tried  System/Administration/Hardware drivers but didn't change anything.
if anyone knows solution pls reply.

---

### Post by Cams on 2009-07-05
> **ivanvajar said:**
> Did you enable proprietary drivers? System/Administration/Hardware drivers

Thanks for the reply. I just had a look at that and it says no proprietary drivers are in use on this system. There is one available to activate, the alternate atheros "madwifi" driver, but that's for the LAN card and it's working all right so no need to mess. 

Any other ideas?

---

### Post by HavocXphere on 2009-07-05
Please provide some info e.g.What type of monitor (CRT or LCD)? What type of connection is used to connect the monitor and the PC?

Also, it would help if you post the contents of your /etc/X11/xorg.conf file.

You can try to force it to a certain resolution & refresh rate: [[Like this]("http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401")]. Note that this is considered an inelegant hack..so use at own risk.;) And of course, change the values to ones appropriate to your situation.

@influanza99: I'd suggest starting your own thread since the cause & solution might be different in your case.

---

### Post by Zimmer on 2009-07-05
According to this xfree supports your card usinfg the 'trident' driver.
[http://www.xfree86.org/4.3.0/Status34.html](http://www.xfree86.org/4.3.0/Status34.html)

I guess this means you may need to edit xorg.conf to refer to Driver as 'trident' in the Device section.....

(remember to back up the xorg.conf just in case :)  )

---

### Post by Cams on 2009-07-05
I'm afraid I don't know how to post contents of things or edit things or do backups. Is there a walk through anywhere?

I did say in my original post that it's an old laptop, so it's a laptop monitor, native resolution of 1024x768 with a Trident video card.

---

### Post by Cams on 2009-07-06
I just reinstalled from scratch in the vain hope that the problem would go away, but of course it hasn't. I've done some more searching on the problem, but any potential solutions become unworkable at the point where posters post logs and edit config files and such like. I have no clue how to do that and feel like I'm stumbling around with the light out. I really could use a little help with this as I can't do it on my own. If anyone would care to work with me on this, I'd be most grateful. 

Cheers
Cams

---

### Post by Cams on 2009-07-07
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux tiny-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  6 23:23:43 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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

(--) PCI:*(0@1:0:0) Trident Microsystems CyberBlade i1 rev 106, Mem @ 0xf5000000/8388608, 0xf4100000/131072, 0xf4800000/8388608, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched trident from file name trident.ids
(==) Matched trident for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for trident
(--) Assigning device section with no busID to primary device
(--) Chipset cyberbladei1d found
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
(II) Setting vga for screen 0.
(II) TRIDENT(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xF5000000
(--) TRIDENT(0): IO registers at 0xF4100000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): VESA BIOS detected
(II) TRIDENT(0): VESA VBE Version 1.2
(II) TRIDENT(0): VESA VBE Total Mem: 8192 kB
(II) TRIDENT(0): VESA VBE OEM: Copyright 1998 TRIDENT MICROSYSTEMS INC.
(--) TRIDENT(0): Revision is 106
(--) TRIDENT(0): Found CyberBlade/DSTN/i1 chip
(--) TRIDENT(0): RAM type is SDRAM
(--) TRIDENT(0): Using SW cursor
(--) TRIDENT(0): VideoRAM: 8192 kByte
(--) TRIDENT(0): TFT Panel 800x600 found
(--) TRIDENT(0): Memory Clock is 57.27 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) TRIDENT(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) TRIDENT(0): Unable to estimate virtual size
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "320x240" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x960) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1280x960" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x1024) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1280x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (896x672) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "896x672" (unknown reason)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (928x696) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "928x696" (unknown reason)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (832x624) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "832x624" (unknown reason)
(II) TRIDENT(0): Not using default mode "416x312" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Removing mode (1440x900) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1440x900" (unknown reason)
(II) TRIDENT(0): Not using default mode "720x450" (hsync out of range)
(II) TRIDENT(0): Removing mode (1600x1024) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1600x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "800x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (960x540) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "960x540" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (960x600) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "960x600" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) TRIDENT(0): Virtual size is 800x600 (pitch 800)
(**) TRIDENT(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TRIDENT(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) TRIDENT(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TRIDENT(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) TRIDENT(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow off
(II) TRIDENT(0): H-timing shadow registers: 0x7f           0x00 0x69 0x7f
(II) TRIDENT(0): H-timing registers:        0x7f 0x63 0x63 0x00 0x69 0x7f
(II) TRIDENT(0): V-timing shadow registers: 0x72 0xf0 0x59 0x0d           0x00 (0x08)
(II) TRIDENT(0): V-timing registers:        0x72 0xf0 0x59 0x0d 0x57 0x00 0x00
(II) TRIDENT(0): Setting BIOS Mode: 6d for: 800x600
(II) TRIDENT(0): Found Clock  80.00 n=249 m=21 k=1
(II) TRIDENT(0): Using 1447 scanlines of offscreen memory for area's 
(II) TRIDENT(0): Using 1838208 bytes of offscreen memory for linear (offset=0x63f380)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		8 256x256 slots
(==) TRIDENT(0): Backing store disabled
(II) TRIDENT(0): DPMS enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV VID_ZOOM_MINI  
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
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
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
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
(**) Option "xkb_layout" "gb"
(**) Video Bus: xkb_layout: "gb"
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
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0

```

---

### Post by nielsek on 2009-07-07
go to your terminal and type in:
```
sudo gedit /etc/X11/xorg.conf
```

Then paste this
```
DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
```
between Device "Configured Video Device" and EndSection.
Then save and reboot.

---

### Post by Cams on 2009-07-07
I just did what you suggested and now have this message on the screen:

Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) Problem parsing the config file
(EE) Error parsing the config file

I did a review and found this

Parse error on line 23 of section Device in file /etc/X11/xorg.conf
"DefaultDepth" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file
Fatal server error:
no screens found

---

### Post by Zimmer on 2009-07-07
> (--) TRIDENT(0): TFT Panel 800x600 found
(--) TRIDENT(0): Memory Clock is 57.27 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) TRIDENT(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) TRIDENT(0): Unable to estimate virtual size
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
Ok, so the log reckons your screen is 800x600 tft and is using default ranges to configure and use it, hence no higher resolutions available.

To pursue this safely and tweak the config we need to establish the capabilities of your screen and create a custom modeline for it...
I'll get cracking on it..

EDIT:
What make and model laptop is it??

Oh, and keep an eye on these threads, could be the modelines we are looking for...
[http://ubuntuforums.org/showthread.php?p=7577426#post7577426](http://ubuntuforums.org/showthread.php?p=7577426#post7577426)
[http://ubuntuforums.org/showthread.php?t=1098092&highlight=trident+laptop](http://ubuntuforums.org/showthread.php?t=1098092&highlight=trident+laptop)

---

### Post by Cams on 2009-07-07
All I know is that it's a Tiny Notebook with an Intel Celeron 1Ghz chip. According to the text on the underside, it's an A440. This post seems to describe it perfectly and looks like the chip is upgradable to a PIII as well!

[http://sillydog.org/forum/sdt_11735.php](http://sillydog.org/forum/sdt_11735.php)

Thanks so much for taking the time with me on this. I'm very grateful.

---

### Post by Zimmer on 2009-07-08
You could try the solution at
[http://ubuntuforums.org/showthread.php?t=1098092&highlight=trident+laptop](http://ubuntuforums.org/showthread.php?t=1098092&highlight=trident+laptop)

I am unable to find the specs for your screen so it is a gamble that the refresh rates etc. for the Toshiba portege will be in the same range as yours.

If you are sure that the native res is 1024 768 then give it a go with just the change to the Screen section to start with..

> Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection


If that does not work (error may be hsynch out of range) then try using the  altered Monitor section as well.
> Section "Monitor" 
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

---

### Post by Cams on 2009-07-08
None of those worked. When I added the first lot of text, nothing changed. When I added the second part, it gave me an error. I looked at the log and it seemed to be because there was no Identifier so I added Identifier "Configured Monitor" and then it booted fine and had added a few more resolution options than before, but nothing higher than 800x600. 

The default resolutions are:

800x600
640x480
400x300
320x240

After editing the config file, the following additional options are available:

720x450
680x384
576x432
512x384


None of the other solutions that you linked to worked and I have posted to the threads so that I will know which ones I've tried and maybe to help anyone else that is in the same boat.

Could installing this help?

[http://manpages.ubuntu.com/manpages/jaunty/man4/trident.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/trident.4.html)

If so, how does one go about doing that? 

I do hope I can get this resolved. Thanks once again for sticking with me on this.

---

### Post by Zimmer on 2009-07-08
If you have a look at the log I expect you will see why it did not work. We definitely need either a custom modeline statement or to disable the EDID lookup for the screen.

---

### Post by Cams on 2009-07-08
Here is the current log with the config file edited:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux tiny-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  8 22:43:12 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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

(--) PCI:*(0@1:0:0) Trident Microsystems CyberBlade i1 rev 106, Mem @ 0xf5000000/8388608, 0xf4100000/131072, 0xf4800000/8388608, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched trident from file name trident.ids
(==) Matched trident for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for trident
(--) Assigning device section with no busID to primary device
(--) Chipset cyberbladei1d found
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
(II) Setting vga for screen 0.
(**) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xF5000000
(--) TRIDENT(0): IO registers at 0xF4100000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): VESA BIOS detected
(II) TRIDENT(0): VESA VBE Version 1.2
(II) TRIDENT(0): VESA VBE Total Mem: 8192 kB
(II) TRIDENT(0): VESA VBE OEM: Copyright 1998 TRIDENT MICROSYSTEMS INC.
(--) TRIDENT(0): Revision is 106
(--) TRIDENT(0): Found CyberBlade/DSTN/i1 chip
(--) TRIDENT(0): RAM type is SDRAM
(--) TRIDENT(0): Using SW cursor
(--) TRIDENT(0): VideoRAM: 8192 kByte
(--) TRIDENT(0): TFT Panel 800x600 found
(--) TRIDENT(0): Memory Clock is 57.27 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): Configured Monitor: Using hsync range of 30.00-60.00 kHz
(II) TRIDENT(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "800x600" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "400x300" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "800x600" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "400x300" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "800x600" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "400x300" (vrefresh out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1024x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x960) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1280x960" (unknown reason)
(II) TRIDENT(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x1024) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1280x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (896x672) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "896x672" (unknown reason)
(II) TRIDENT(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (928x696) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "928x696" (unknown reason)
(II) TRIDENT(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (832x624) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "832x624" (unknown reason)
(II) TRIDENT(0): Not using default mode "416x312" (vrefresh out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Removing mode (1440x900) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1440x900" (unknown reason)
(II) TRIDENT(0): Removing mode (1600x1024) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "1600x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "800x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (840x525) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "840x525" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Removing mode (960x540) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "960x540" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(0): Removing mode (960x600) larger than the LCD panel (800x600)
(II) TRIDENT(0): Not using default mode "960x600" (unknown reason)
(II) TRIDENT(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using mode "1024x768" (no mode of this name)
(--) TRIDENT(0): Virtual size is 800x600 (pitch 800)
(**) TRIDENT(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TRIDENT(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TRIDENT(0):  Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) TRIDENT(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) TRIDENT(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) TRIDENT(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) TRIDENT(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TRIDENT(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) TRIDENT(0):  Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) TRIDENT(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) TRIDENT(0):  Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) TRIDENT(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) TRIDENT(0):  Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) TRIDENT(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) TRIDENT(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) TRIDENT(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) TRIDENT(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) TRIDENT(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) TRIDENT(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) TRIDENT(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) TRIDENT(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TRIDENT(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) TRIDENT(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow off
(II) TRIDENT(0): H-timing shadow registers: 0x7f           0x00 0x69 0x7f
(II) TRIDENT(0): H-timing registers:        0x7f 0x63 0x63 0x00 0x69 0x7f
(II) TRIDENT(0): V-timing shadow registers: 0x72 0xf0 0x59 0x0d           0x00 (0x08)
(II) TRIDENT(0): V-timing registers:        0x72 0xf0 0x59 0x0d 0x57 0x00 0x00
(II) TRIDENT(0): Setting BIOS Mode: 6d for: 800x600
(II) TRIDENT(0): Found Clock  80.00 n=249 m=21 k=1
(II) TRIDENT(0): Using 1447 scanlines of offscreen memory for area's 
(II) TRIDENT(0): Using 1838208 bytes of offscreen memory for linear (offset=0x63f380)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		8 256x256 slots
(==) TRIDENT(0): Backing store disabled
(**) Option "dpms" "true"
(**) TRIDENT(0): DPMS enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV VID_ZOOM_MINI  
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
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
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
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
(**) Option "xkb_layout" "gb"
(**) Video Bus: xkb_layout: "gb"
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
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow on
(II) TRIDENT(0): H-timing shadow registers: 0x7f           0x00 0x69 0x7f
(II) TRIDENT(0): H-timing registers:        0x5a 0x47 0x47 0x80 0x4c 0x13
(II) TRIDENT(0): V-timing shadow registers: 0x72 0xfa 0x59 0x0d           0x00 (0x08)
(II) TRIDENT(0): V-timing registers:        0x7c 0xff 0x60 0x24 0x5f 0x00 0x7c
(II) TRIDENT(0): Setting BIOS Mode: 6c for: 576x432
(II) TRIDENT(0): Found Clock  80.00 n=249 m=21 k=1
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow off
(II) TRIDENT(0): H-timing shadow registers: 0x7f           0x00 0x69 0x7f
(II) TRIDENT(0): H-timing registers:        0x7f 0x63 0x63 0x00 0x69 0x7f
(II) TRIDENT(0): V-timing shadow registers: 0x72 0xf0 0x59 0x0d           0x00 (0x08)
(II) TRIDENT(0): V-timing registers:        0x72 0xf0 0x59 0x0d 0x57 0x00 0x00
(II) TRIDENT(0): Setting BIOS Mode: 6d for: 800x600
(II) TRIDENT(0): Found Clock  80.00 n=249 m=21 k=1

```

---

### Post by Zimmer on 2009-07-08
Open a terminal and type
xrandr --verbose

let us see the output..

Or.. This might help, it is in the repositories so install via Synaptic.
[http://john.fremlin.de/programs/linux/read-edid/](http://john.fremlin.de/programs/linux/read-edid/)

Did not work on my laptop (probably because I am using NVIDIA drivers, who knows,) but it is worth a shot to try to get info from the screen..

call with
sudo get-edid | parse edid

---

### Post by Cams on 2009-07-09
```
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 (0x103) normal (normal) 0mm x 0mm
	Identifier: 0x102
	Timestamp:  670212
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0
	Panning:    0x0+0+0
	Tracking:   0x0+0+0
	Border:     0/0/0/0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  800x600 (0x103)   28.8MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  800x600 (0x104)   26.9MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   33.6KHz
        v: height  600 start    0 end    0 total  600           clock   56.0Hz
  720x450 (0x105)   19.4MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   27.0KHz
        v: height  450 start    0 end    0 total  450           clock   60.0Hz
  640x480 (0x106)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  680x384 (0x107)   15.7MHz
        h: width   680 start    0 end    0 total  680 skew    0 clock   23.0KHz
        v: height  384 start    0 end    0 total  384           clock   60.0Hz
  576x432 (0x108)   14.9MHz
        h: width   576 start    0 end    0 total  576 skew    0 clock   25.9KHz
        v: height  432 start    0 end    0 total  432           clock   60.0Hz
  512x384 (0x109)   13.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   26.9KHz
        v: height  384 start    0 end    0 total  384           clock   70.0Hz
  512x384 (0x10a)   11.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   23.0KHz
        v: height  384 start    0 end    0 total  384           clock   60.0Hz
  400x300 (0x10b)    7.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   18.0KHz
        v: height  300 start    0 end    0 total  300           clock   60.0Hz
  400x300 (0x10c)    6.7MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   16.8KHz
        v: height  300 start    0 end    0 total  300           clock   56.0Hz
  320x240 (0x10d)    4.6MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   14.4KHz
        v: height  240 start    0 end    0 total  240           clock   60.0Hz

```

Here is what edid did:

```
	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 102
	VBE string at 0xc0056 "Copyright 1998 TRIDENT MICROSYSTEMS INC."

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
bash: parse: command not found

```

---

### Post by Zimmer on 2009-07-09
From
 [http://www.edugeek.net/forums/nix/32431-omg-xorg-trident-video-4hours-wasted-time.html](http://www.edugeek.net/forums/nix/32431-omg-xorg-trident-video-4hours-wasted-time.html)

> After a bunch of trial and error, the change that got it working was simple: I added the following 2 lines to the "Monitor" section of the default xorg.conf, and restarted X (CTRL+ALT+Backspace):
HorizSync 28-50
VertRefresh 43-75
Maybe you should try these synch values....
There are quite a few posts out there for the Trident card with similar solutions, but not specific to your  laptop..

Make sure you get the xorg.conf correct (and read the log...) 
Some more to try (this one changes the default depth to 16 , could be significant)
[http://forums.debian.net/viewtopic.php?t=38293](http://forums.debian.net/viewtopic.php?t=38293)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/209018](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/209018)
led me to 
[http://launchpadlibrarian.net/24703488/xorg.conf](http://launchpadlibrarian.net/24703488/xorg.conf)
and
[http://www.uluga.ubuntuforums.org/showpost.php?p=6135903&postcount=48](http://www.uluga.ubuntuforums.org/showpost.php?p=6135903&postcount=48)
and
[http://kimharding.net/dual_boot/](http://kimharding.net/dual_boot/)

---

### Post by Cams on 2009-07-09
Hey Zimmer, I tried all of those solutions without any joy. I'm beginning to get an uncomfortable, niggling feeling that the monitor actually is 800x600. I can't find any specs on the computer at all and never thought to check before wiping the HDD. Trouble is, surfing the web at 800x600 is a real pain <sigh>

Thank you so much Zimmer for all your time on this. I owe you a few pints at the very least! It's heartening to know that these forums are so helpful. 

Cams

---

### Post by Zimmer on 2009-07-09
Last throw of the dice....


Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
  Option "UseEDID" "False"
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection 

and try putting the Default depth down to 16.

Always have a look at the log after to make sure the failure is not down to incorrect xorg.conf statements!

---

