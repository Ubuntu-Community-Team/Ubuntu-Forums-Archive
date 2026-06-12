---
title: "Display messed up after updating"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by gtccswsv on 2009-04-13
I've installed 9.04 and updated some applications, when I started up, the display mess up... Any key except fro the DEL+ALT+CTRL won't work, how could I reconfigure xserver-xorg, it seems dpkg reconfigure xserver-xorg is not working after booting up with CD.

---

### Post by MaindotC on 2009-04-13
What kind of video card do you have and could you please list your hardware specifications in your signature with links the way mine are?

---

### Post by gtccswsv on 2009-04-13
Thank you, details as follows.
Dell Vostro 1310, 

Intel®  CoreTM  2 Duo T5670
Integrated graphics: Intel®  GM965 Express chipset

ntel Integrated Graphics Media Accelerator X31003
128MB NVIDIA®  GeForceTM  8400M GS (64 bit) Graphic Card 
 
  Displays	
13.3" Widescreen WXGA (1280 x 800) Display

  Storage	
5400 RPM hard drive 250GB

  Optical Drives	
Fixed Internal 8x DVD / 24x CDRW Combo Slot Load Drive including Software

  Power	
4-cell 38 WHr Lithium Ion battery

  Connectivity	
Integrated Wired: Gigabit RJ45 Ethernet network interface adapter standard (100% attached)
  
  Wireless LAN:
Dell Wireless 1395 802.11g Wi-Fi Mini-card
Bluetooth: Dell Wireless 360 Bluetooth®  Module

---

### Post by gtccswsv on 2009-04-13
I found this bug

[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-08/msg26347.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-08/msg26347.html)

But my screen works well after the initial installation of Ubuntu 9.04, after updating some applications, the screen goes funny, how can I know which application leads to this problem and roll it back...

---

### Post by gtccswsv on 2009-04-13
Hi all,

I managed to get this problem fixed, after reading Thread *How can I set Intel experimental modesetting driver as my default card in Intrepid?*

1. Boot up with CD. Open terminal,
sudo mkdir /mnt/repair
sudo mount /dev/sda7 /mnt/repair
sudo chroot /mnt/repair



2. Remove current Intel Video driver and install latest intel video driver.

sudo apt-get remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel


3. Removed all packages containing "fglrx" from Synaptic package manager.

sudo apt-get remove fglrx*

4. Reboot

My Xserver log:


root@ubuntu:/# ls
bin   cdrom  etc   home        lib	   media  mnt  proc    root  selinux  sys  usr	vmlinuz
boot  dev    halt  initrd.img  lost+found  misc   opt  repair  sbin  srv      tmp  var
root@ubuntu:/# cd var
root@ubuntu:/var# ls
backups  cache	crash  games  lib  local  lock	log  mail  opt	run  spool  tmp
root@ubuntu:/var# cd log
root@ubuntu:/var/log# ls
apparmor	 bittorrent	daemon.log.0	    dmesg.1.gz	fontconfig.log	kern.log.0  mediatomb.log     syslog		   user.log.0
apport.log	 boot		debug		    dmesg.2.gz	fsck		lastlog     messages	      syslog.0		   wpa_supplicant.log
apport.log.1	 bootstrap.log	debug.0		    dmesg.3.gz	gdm		lpr.log     messages.0	      syslog.1.gz	   wpa_supplicant.log.1.gz
apport.log.2.gz  btmp		dist-upgrade	    dmesg.4.gz	installer	mail.err    news	      syslog.2.gz	   wpa_supplicant.log.2.gz
apt		 ConsoleKit	dkms_autoinstaller  dpkg.log	jockey.log	mail.info   pm-powersave.log  udev		   wtmp
auth.log	 cups		dmesg		    exim4	jockey.log.1	mail.log    pycentral.log     unattended-upgrades  Xorg.0.log
auth.log.0	 daemon.log	dmesg.0		    faillog	kern.log	mail.warn   samba	      user.log		   Xorg.0.log.old
root@ubuntu:/var/log# cat Xorg.0.log
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

[    0.002095] (WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
[    0.002137] (WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
[    0.002161] (WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log


root@ubuntu:/var/log# cat Xorg.0.log
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux norman-laptop 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009 i686
Build Date: 20 March 2009  02:01:06PM
xorg-server 2:1.6.0-0ubuntu4 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: [    0.000714] (--) probed, [    0.000725] (**) from config file, [    0.000734] (==) default setting,
	[    0.000742] (++) from command line, [    0.000751] (!!) notice, [    0.000759] (II) informational,
	[    0.000767] (WW) warning, [    0.000776] (EE) error, [    0.000784] (NI) not implemented, [    0.000793] (??) unknown.
[    0.000856] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 13 20:43:21 2009
[    0.000896] (==) Using config file: "/etc/X11/xorg.conf"
[    0.000970] (==) No Layout section.  Using the first Screen section.
[    0.000981] (**) |-->Screen "Default Screen" (0)
[    0.000990] (**) |   |-->Monitor "Configured Monitor"
[    0.001210] (**) |   |-->Device "Configured Video Device"
[    0.001236] (==) Automatically adding devices
[    0.001244] (==) Automatically enabling devices
[    0.001402] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.001456] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.001464] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001471] (II) Cannot locate a core pointer device.
[    0.001477] (II) Cannot locate a core keyboard device.
[    0.001483] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.001496] (II) Loader magic: 0x3bc0
[    0.001503] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.001525] (II) Loader running on linux
[    0.001534] (++) using VT number 7

[    0.065126] (--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xf8000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
[    0.065194] (--) PCI: (0@0:2:1) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xf8100000/1048576
[    0.065358] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.065381] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.065495] (II) LoadModule: "extmod"
[    0.065880] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.066038] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.066064] (II) Loading extension MIT-SCREEN-SAVER
[    0.066071] (II) Loading extension XFree86-VidModeExtension
[    0.066077] (II) Loading extension XFree86-DGA
[    0.066085] (II) Loading extension DPMS
[    0.066091] (II) Loading extension XVideo
[    0.066099] (II) Loading extension XVideo-MotionCompensation
[    0.066105] (II) Loading extension X-Resource
[    0.066112] (II) LoadModule: "dbe"
[    0.066387] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.066456] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.066482] (II) Loading extension DOUBLE-BUFFER
[    0.066489] (II) LoadModule: "glx"
[    0.066734] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.066855] (II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.066888] (II) Loading extension GLX
[    0.066897] (II) LoadModule: "record"
[    0.067148] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.067221] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.067246] (II) Loading extension RECORD
[    0.067253] (II) LoadModule: "dri"
[    0.067490] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.067650] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.067668] (II) Loading extension XFree86-DRI
[    0.067675] (II) Loading sub module "fglrxdrm"
[    0.067682] (II) LoadModule: "fglrxdrm"
[    0.067714] (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
[    0.067797] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
[    0.067829] (II) LoadModule: "dri2"
[    0.068073] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.068148] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.068170] (II) Loading extension DRI2
[    0.068186] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.068748] (II) Matched intel from file name intel.ids
[    0.068801] (==) Matched intel for the autoconfigured driver
[    0.068809] (==) Assigned the driver to the xf86ConfigLayout
[    0.068816] (II) LoadModule: "intel"
[    0.068972] (II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
[    0.069251] (II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.069287] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
[    0.070578] (II) Primary Device is: PCI 00@00:02:0
[    0.091131] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.091256] (II) resource ranges after probing:
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
[    0.110888] (II) Loading sub module "vgahw"
[    0.110897] (II) LoadModule: "vgahw"
[    0.110986] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.111077] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.111123] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.111133] (==) intel(0): Depth 24, [    0.111139] (--) framebuffer bpp 32
[    0.111147] (==) intel(0): RGB weight 888
[    0.111155] (==) intel(0): Default visual is TrueColor
[    0.111185] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    0.111194] (--) intel(0): Chipset: "965GM"
[    0.111201] (--) intel(0): Linear framebuffer at 0xD0000000
[    0.111224] (--) intel(0): IO registers at addr 0xF8000000
[    0.111235] (WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
[    0.111770] (==) intel(0): Using EXA for acceleration
[    0.111853] (II) intel(0): 2 display pipes available.
[    0.111861] (II) Loading sub module "ddc"
[    0.111867] (II) LoadModule: "ddc"
[    0.111880] (II) Module "ddc" already built-in
[    0.111886] (II) Loading sub module "i2c"
[    0.111892] (II) LoadModule: "i2c"
[    0.111903] (II) Module "i2c" already built-in
[    0.111930] (II) intel(0): Output VGA using monitor section Configured Monitor
[    0.111943] (II) intel(0): Output LVDS has no monitor section
[    0.111960] (II) intel(0): I2C bus "LVDSDDC_C" initialized.
[    0.111970] (II) intel(0): Attempting to determine panel fixed mode.
[    0.111987] (II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
[    0.111996] (II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
[    0.164082] (II) intel(0): EDID vendor "LPL", prod id 0
[    0.164093] (II) intel(0):     EDID quirk: Detailed timings give sizes in cm.
[    0.164134] (II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
[    0.168656] (II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
[    0.168688] (II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
[    0.169578] (II) intel(0): No SDVO device found on SDVOC
[    0.169590] (II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
[    0.169598] (II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
[    0.169613] (II) intel(0): Output TV has no monitor section
[    0.234658] (II) intel(0): Resizable framebuffer: not available (1 3)
[    0.241022] (II) intel(0): EDID for output VGA
[    0.292572] (II) intel(0): EDID for output LVDS
[    0.292581] (II) intel(0): Manufacturer: LPL  Model: 0  Serial#: 0
[    0.292589] (II) intel(0): Year: 2008  Week: 0
[    0.292596] (II) intel(0): EDID Version: 1.3
[    0.292602] (II) intel(0): Digital Display Input
[    0.292609] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 18
[    0.292623] (II) intel(0): Gamma: 2.20
[    0.292643] (II) intel(0): No DPMS capabilities specified
[    0.292653] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    0.292660] (II) intel(0): First detailed timing is preferred mode
[    0.292667] (II) intel(0): GTF timings supported
[    0.292673] (II) intel(0): redX: 0.590 redY: 0.343   greenX: 0.328 greenY: 0.540
[    0.292688] (II) intel(0): blueX: 0.161 blueY: 0.148   whiteX: 0.313 whiteY: 0.329
[    0.292701] (II) intel(0): Manufacturer's mask: 0
[    0.292708] (II) intel(0): Supported additional Video Mode:
[    0.292714] (II) intel(0): clock: 69.3 MHz   Image Size:  290 x 180 mm
[    0.292727] (II) intel(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1416 h_border: 0
[    0.292739] (II) intel(0): v_active: 800  v_sync: 804  v_sync_end 810 v_blanking: 817 v_border: 0
[    0.292750] (II) intel(0): Supported additional Video Mode:
[    0.292757] (II) intel(0): clock: 69.3 MHz   Image Size:  290 x 180 mm
[    0.292768] (II) intel(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1416 h_border: 0
[    0.292778] (II) intel(0): v_active: 800  v_sync: 804  v_sync_end 810 v_blanking: 817 v_border: 0
[    0.292789] (II) intel(0):  D684C&#65533;133WX1
[    0.292796] (II) intel(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz,
[    0.292807] (II) intel(0): EDID (in hex):
[    0.292817] (II) intel(0): 	00ffffffffffff00320c000000000000
[    0.292826] (II) intel(0): 	00120103901d12780a31459757548a29
[    0.292835] (II) intel(0): 	26505400000001010101010101010101
[    0.292845] (II) intel(0): 	010101010101121b0088502011301820
[    0.292854] (II) intel(0): 	46001eb31000001b121b008850201130
[    0.292863] (II) intel(0): 	182046001eb31000001b000000fe0044
[    0.292872] (II) intel(0): 	36383443813133335758310a00000000
[    0.292882] (II) intel(0): 	001f36424c6b8ab2ff01010a2020006e
[    0.292888] (II) intel(0): EDID vendor "LPL", prod id 0
[    0.292909] (II) intel(0):     EDID quirk: Detailed timings give sizes in cm.
[    0.292990] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.292998] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    0.293006] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    0.293012] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.293019] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.293026] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.293033] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.293039] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.293046] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.293053] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.293059] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.293066] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    0.293073] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    0.293079] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    0.293086] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    0.293093] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    0.293100] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    0.293107] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293113] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293120] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293127] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293134] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293141] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.293147] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.293154] (II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
[    0.293169] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.293176] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.293183] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.293189] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.293196] (II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
[    0.293203] (II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
[    0.293210] (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    0.293216] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.293223] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.293230] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.293237] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.293244] (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    0.293250] (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
[    0.293257] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    0.293264] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    0.293271] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    0.293278] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    0.293287] (II) intel(0): Printing probed modes for output LVDS
[    0.293308] (II) intel(0): Modeline "1280x800"x59.9   69.30  1280 1304 1336 1416  800 804 810 817 +hsync -vsync (48.9 kHz)
[    0.293322] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    0.293335] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.293346] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.293358] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.293370] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.293382] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    0.293394] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.293405] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.293417] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.293428] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.293439] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    0.293451] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.293462] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.293473] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.293485] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    0.293496] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    0.293508] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    0.942835] (II) intel(0): EDID for output TV
[    0.942857] (II) intel(0): Output VGA disconnected
[    0.942870] (II) intel(0): Output LVDS connected
[    0.942882] (II) intel(0): Output TV disconnected
[    0.942897] (II) intel(0): Using exact sizes for initial modes
[    0.942908] (II) intel(0): Output LVDS using initial mode 1280x800
[    1.705946] (II) intel(0): detected 512 kB GTT.
[    1.705973] (II) intel(0): detected 7676 kB stolen memory.
[    1.705984] (==) intel(0): video overlay key set to 0x101fe
[    1.705994] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    1.706010] (==) intel(0): DPI set to (96, 96)
[    1.706016] (II) Loading sub module "fb"
[    1.706023] (II) LoadModule: "fb"
[    1.706111] (II) Loading /usr/lib/xorg/modules//libfb.so
[    1.706271] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    1.706296] (II) Loading sub module "exa"
[    1.706304] (II) LoadModule: "exa"
[    1.706383] (II) Loading /usr/lib/xorg/modules//libexa.so
[    1.706470] (II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
[    1.706491] (II) Loading sub module "ramdac"
[    1.706497] (II) LoadModule: "ramdac"
[    1.706511] (II) Module "ramdac" already built-in
[    1.706522] (II) intel(0): Comparing regs from server start up to After PreInit
[    1.706539] (WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
[    1.706553] (WW) intel(0): PP_STATUS before: on, ready, sequencing idle
[    1.706561] (WW) intel(0): PP_STATUS after: on, ready, sequencing on
[    1.706584] (WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00012d2d to 0x00028283
[    1.706593] (WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00009696 to 0x00014141
[    1.726083] (==) Depth 24 pixmap format is 32 bpp
[    1.726093] (II) do I need RAC?  No, I don't.
[    1.726102] (II) resource ranges after preInit:
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
[    1.726356] (II) intel(0): Kernel reported 238592 total, 1 used
[    1.726373] (II) intel(0): I830CheckAvailableMemory: 954364 kB available
[    1.726384] (WW) intel(0): DRI2 requires UXA
[    1.726408] (EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 5.4.x is needed.
[dri] Disabling DRI.
[    1.726426] (**) intel(0): Framebuffer compression disabled
[    1.726433] (**) intel(0): Tiling enabled
[    1.726473] (==) intel(0): VideoRam: 262144 KB
[    1.726482] (II) intel(0): Attempting memory allocation with tiled buffers.
[    1.728404] (II) intel(0): Tiled allocation successful.
[    1.729469] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    1.729630] (II) EXA(0): Offscreen pixmap area of 19660800 bytes
[    1.729644] (II) EXA(0): Driver registered support for the following operations:
[    1.729653] (II)         Solid
[    1.729660] (II)         Copy
[    1.729665] (II)         Composite (RENDER acceleration)
[    1.729676] (==) intel(0): Backing store disabled
[    1.729686] (==) intel(0): Silken mouse enabled
[    1.729705] (II) intel(0): Initializing HW Cursor
[    1.795260] (II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
[    1.795904] (II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01a2b000 (pgoffset 6699)
[    1.796396] (II) intel(0): Fixed memory allocation layout:
[    1.796426] (II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
[    1.796436] (II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
[    1.796443] (II) intel(0): 0x0002a000-0x00129fff: fake bufmgr (1024 kB)
[    1.796451] (II) intel(0): 0x0012a000-0x0012afff: overlay registers (4 kB)
[    1.796459] (II) intel(0): 0x0012b000-0x0076afff: front buffer (6400 kB)
[    1.796466] (II) intel(0): 0x0076b000-0x01a2afff: exa offscreen (19200 kB)
[    1.796474] (II) intel(0): 0x0077f000:            end of stolen memory
[    1.796482] (II) intel(0): 0x01a2b000-0x01a2bfff: power context (4 kB)
[    1.796490] (II) intel(0): 0x10000000:            end of aperture
[    1.799301] (WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
[    1.799350] (WW) intel(0): Existing errors found in hardware state.
[    2.025082] (II) intel(0): using SSC reference clock of 96 MHz
[    2.025865] (II) intel(0): Selecting standard 18 bit TMDS pixel format.
[    2.550441] (II) intel(0): Output configuration:
[    2.550462] (II) intel(0):   Pipe A is off
[    2.550481] (II) intel(0):   Display plane A is now disabled and connected to pipe A.
[    2.550496] (II) intel(0):   Pipe B is on
[    2.550508] (II) intel(0):   Display plane B is now enabled and connected to pipe B.
[    2.550521] (II) intel(0):   Output VGA is connected to pipe none
[    2.550534] (II) intel(0):   Output LVDS is connected to pipe B
[    2.550545] (II) intel(0):   Output TV is connected to pipe none
[    2.550562] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    2.556751] (II) intel(0): DPMS enabled
[    2.556762] (==) intel(0): Intel XvMC decoder disabled
[    2.556786] (II) intel(0): Set up textured video
[    2.556814] (II) intel(0): Set up overlay video
[    2.556858] (II) intel(0): direct rendering: Failed
[    2.556870] (--) RandR disabled
[    2.576418] (II) Initializing built-in extension Generic Event Extension
[    2.576448] (II) Initializing built-in extension SHAPE
[    2.576454] (II) Initializing built-in extension MIT-SHM
[    2.576460] (II) Initializing built-in extension XInputExtension
[    2.576467] (II) Initializing built-in extension XTEST
[    2.576472] (II) Initializing built-in extension BIG-REQUESTS
[    2.576478] (II) Initializing built-in extension SYNC
[    2.576484] (II) Initializing built-in extension XKEYBOARD
[    2.576490] (II) Initializing built-in extension XC-MISC
[    2.576496] (II) Initializing built-in extension SECURITY
[    2.576502] (II) Initializing built-in extension XINERAMA
[    2.576507] (II) Initializing built-in extension XFIXES
[    2.576513] (II) Initializing built-in extension RENDER
[    2.576519] (II) Initializing built-in extension RANDR
[    2.576525] (II) Initializing built-in extension COMPOSITE
[    2.576530] (II) Initializing built-in extension DAMAGE

---

### Post by niceguy123 on 2009-07-23
> **strAlan said:**
> What kind of video card do you have and could you please list your hardware specifications in your signature with links the way mine are?


strAlan Hi,

Here are my specs ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
```

BTW - Is there a way to add them to the signature automatically or do I need to research the web for sites and write html to add them like you did?

And back to the main issue, I have a 1600X900 screen and haven't been able to figure out how to get my OS to recognize it. Can you help.

---

