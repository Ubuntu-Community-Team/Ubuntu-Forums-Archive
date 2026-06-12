---
title: "Getting video to work _right_ on a mini-note (hp 2133)"
date: 2009-01-25
forum: Hardware
---

### Post by Kyle_S on 2009-01-25
I'm reposting this from the ubuntu answers page, where I posted it originally, just in case this will help someone.


This is more information than a question, for folks who bought a 2133 and are frustrated with the resolution the VESA driver is giving them. This is how to get the mini-note working with the openchrome driver (which comes with ubuntu). Yes I know all the docs say that it's broken in 8.10, but they're wrong. It's more that the default settings in X are wrong for the card.

Two things to remember about these instructions:
If you want to switch to and from X to console, you need to have the VESA framebuffer setup.
Sometimes, when switching from console to X, or starting X (or coming out of suspend-to-disc), you get weird wobbly line video. When that happens, you need to reboot, or re-suspend to disc (which is a reboot, as far as the hardware is concerned).

So, here's two sets of instructions. One for the cut & paste crowd, and one for those who want to dig deeper.

Cut&Paste:
There is nothing wrong with not wanting to learn the guts of your car just to get the windows to roll down. Similarly, there isn't anything wrong with just doing a copy&paste. This is done in four steps

Step 1) backup your xorg.conf
sh$ cp /etc/X11/xorg.conf ~/xorg.conf-old

Step 2) as root, edit the xorg.conf, and replace the contents with the config file at the end of this post.
sh$ sudo gedit /etc/X11/xorg.conf

Step 3) log out. This should cause X to restart. If it didn't work, reboot. Log back in to your fresh X

One more step..

Step 4) Open the screen resolution applet from the system menu. System>Preferences>Screen Resolution
Select the correct resolution for your mini-note (for most it will be 1280x768).

Dig Deeper!
So what is going on here?
X (ubuntu uses the x.org version) can do a _ton_ of auto-configuration for you. It's been able to do it for ages. You just type X -configure as root. BUT, X can't be running for you to do this....

So
Log out, and switch to a graphical console
On the console, log in as you, sudo to root
Use the massively powerful killall command to kill the display manager: gdm
sh$ killall gdm
Unsurprisingly this will kill all running binaries with the name "gdm", that root is allowed to (root is allowed to kill everything).
Run X's autoconf by typing X -configure
sh$ X -configure
You'll end up with lots of text on screen, and a file called xorg.conf.new
Usually, this would be all you needed, but on the mini-note, we need to tweak it.
If you were to use this file now, it would display, then probably lock up your system.
Open up the file with vi(or vim, or emacs, or jove, whatever you like), and find the part that starts with Section "Device". More or less, this is how X drivers are really setup.
Every line that starts with a # is a comment, so you see a ton of options are commented out.
In our case, we need two of the unused options, I2CScan and ShadowFB. Start by uncommenting those two lines. Note that there is a second comment at the end of that line that says, #[<bool>]. You guessed it, we need to say "true" to those now.
        Option "I2CScan" "true" # [<bool>]
        Option "ShadowFB" "true" # [<bool>]
Save your file, and move it into place. I encourage you to play more with it, but start by making sure this part works for you.
Now that the /root/xorg.conf.new is edited, make a backup of /etc/X11/xorg.conf.
Seriously, make the backup.
Move /root/xorg.conf.new over to /etc/X11/xorg.conf, cross your fingers, and reboot.

Enjoy digging into things from now on!

## Xorg.conf ##
Section "ServerLayout"
 Identifier "X.org Configured"
 Screen 0 "Screen0" 0 0
 InputDevice "Mouse0" "CorePointer"
 InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
 ModulePath "/usr/lib/xorg/modules"
 FontPath "/usr/share/fonts/X11/misc"
 FontPath "/usr/share/fonts/X11/cyrillic"
 FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
 FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
 FontPath "/usr/share/fonts/X11/Type1"
 FontPath "/usr/share/fonts/X11/100dpi"
 FontPath "/usr/share/fonts/X11/75dpi"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load "dbe"
 Load "glx"
 Load "extmod"
 Load "xtrap"
 Load "dri"
 Load "record"
EndSection

Section "InputDevice"
 Identifier "Keyboard0"
 Driver "kbd"
EndSection

Section "InputDevice"
 Identifier "Mouse0"
 Driver "mouse"
 Option "Protocol" "auto"
 Option "Device" "/dev/input/mice"
 Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
 Identifier "Monitor0"
 VendorName "Monitor Vendor"
 ModelName "Monitor Model"
EndSection

Section "Device"
        Option "I2CScan" "true" # [<bool>]
        Option "ShadowFB" "true" # [<bool>]
 Identifier "Card0"
 Driver "openchrome"
 VendorName "VIA Technologies, Inc."
 BoardName "CN896/VN896/P4M900 [Chrome 9 HC]"
 BusID "PCI:1:0:0"
EndSection

Section "Screen"
 Identifier "Screen0"
 Device "Card0"
 Monitor "Monitor0"
 SubSection "Display"
  Viewport 0 0
  Depth 15
 EndSubSection
 SubSection "Display"
  Viewport 0 0
  Depth 16
 EndSubSection
 SubSection "Display"
  Viewport 0 0
  Depth 24
 EndSubSection
EndSection

---

### Post by tomcoussement on 2009-02-21
Hello,

I have installed jaunty (xubuntu) on my new hp mini because I have been reading somewhere in the forums that jaunty works out of the box...

It indeed takes the right driver but the configuration is still not correct.

I get a graphical session but I only see the upper left part of the screen on the lcd of my mini.
If I connect an external screen I see the whole screen but no mouse pointer... 
The resolution seems to be 1366x768 but I can't change the resolution with "(sudo) xfce4-display-settings"

There is no /etc/X11/xorg.conf

If I use the above xorg.conf file I get the same result as without an xorg.conf file as does the xorg.conf file comming out of X -configure.

How can I configure Xorg to use 1024x768 or 1024x600 on the hp mini display and 1680x1050 on my external display.

Those are the settings that work in Windows XP on the mini but I don't want to use MS!!

Any help would be greatly appreciated!

My hp mini 2133 is a FU353EA#UUG model.

lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

/var/log/Xorg.0.log:
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.902 (1.6.0 RC 2)
Release Date: 2009-1-30
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.28-8-generic #24-Ubuntu SMP Wed Feb 18 18:48:55 UTC 2009 i686
Build Date: 18 February 2009  01:41:32AM
xorg-server 2:1.5.99.902-0ubuntu7 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.028259] (--) probed, [    0.028310] (**) from config file, [    0.028338] (==) default setting,
	[    0.028366] (++) from command line, [    0.028393] (!!) notice, [    0.028421] (II) informational,
	[    0.028448] (WW) warning, [    0.028475] (EE) error, [    0.028502] (NI) not implemented, [    0.028529] (??) unknown.
[    0.028787] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 21 10:23:54 2009
[    0.045748] (WW) Unable to locate/open config file
[    0.045873] (II) Loader magic: 0x3bc0
[    0.045895] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.045972] (II) Loader running on linux
[    0.046001] (++) using VT number 7

[    0.304169] (--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] rev 1, Mem @ 0xd0000000/0, 0xfc000000/0, BIOS @ 0x????????/65536
[    0.304412] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.305995] (II) Matched openchrome from file name openchrome.ids
[    0.306304] (==) Using default built-in configuration (39 lines)
[    0.306332] (==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default openchrome Device 0"
		Driver	"openchrome"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default openchrome Screen 0"
		Device	"Builtin Default openchrome Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default openchrome Device 0"
		Driver	"openchrome"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default openchrome Screen 0"
		Device	"Builtin Default openchrome Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default openchrome Screen 0"
		Screen	"Builtin Default openchrome Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
[    0.310114] (==) --- End of built-in configuration ---
[    0.310353] (==) ServerLayout "Builtin Default Layout"
[    0.310370] (**) |-->Screen "Builtin Default openchrome Screen 0" (0)
[    0.310385] (**) |   |-->Monitor "<default monitor>"
[    0.310992] (**) |   |-->Device "Builtin Default openchrome Device 0"
[    0.311008] (==) No monitor specified for screen "Builtin Default openchrome Screen 0".
	Using a default monitor configuration.
[    0.311020] (**) |-->Screen "Builtin Default openchrome Screen 0" (1)
[    0.311031] (**) |   |-->Monitor "<default monitor>"
[    0.311573] (**) |   |-->Device "Builtin Default openchrome Device 0"
[    0.311585] (==) No monitor specified for screen "Builtin Default openchrome Screen 0".
	Using a default monitor configuration.
[    0.311596] (**) |-->Screen "Builtin Default vesa Screen 0" (2)
[    0.311607] (**) |   |-->Monitor "<default monitor>"
[    0.312189] (**) |   |-->Device "Builtin Default vesa Device 0"
[    0.312202] (==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
[    0.312213] (**) |-->Screen "Builtin Default fbdev Screen 0" (3)
[    0.312224] (**) |   |-->Monitor "<default monitor>"
[    0.312775] (**) |   |-->Device "Builtin Default fbdev Device 0"
[    0.312788] (==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
[    0.312839] (==) Automatically adding devices
[    0.312851] (==) Automatically enabling devices
[    0.313049] (==) No FontPath specified.  Using compiled-in default.
[    0.389717] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.585800] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
[    0.585887] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.585913] (II) Cannot locate a core pointer device.
[    0.585934] (II) Cannot locate a core keyboard device.
[    0.585953] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.586087] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.586181] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.589541] (II) LoadModule: "extmod"
[    0.654166] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.654995] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.655138] (II) Loading extension MIT-SCREEN-SAVER
[    0.655162] (II) Loading extension XFree86-VidModeExtension
[    0.655181] (II) Loading extension XFree86-DGA
[    0.655205] (II) Loading extension DPMS
[    0.655225] (II) Loading extension XVideo
[    0.655247] (II) Loading extension XVideo-MotionCompensation
[    0.655268] (II) Loading extension X-Resource
[    0.655294] (II) LoadModule: "dbe"
[    0.656407] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.656821] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.656941] (II) Loading extension DOUBLE-BUFFER
[    0.656968] (II) LoadModule: "glx"
[    0.658035] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.658694] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.658845] (==) AIGLX enabled
[    0.658890] (==) Exporting typical set of GLX visuals
[    0.658919] (II) Loading extension GLX
[    0.658951] (II) LoadModule: "record"
[    0.660031] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.660455] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.660575] (II) Loading extension RECORD
[    0.660601] (II) LoadModule: "dri"
[    0.661630] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.714529] (II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.714692] (II) Loading extension XFree86-DRI
[    0.714740] (II) LoadModule: "dri2"
[    0.715860] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.768555] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.768712] (II) Loading extension DRI2
[    0.768750] (II) LoadModule: "openchrome"
[    0.769569] (II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
[    0.783664] (II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.99.902, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.783904] (II) LoadModule: "vesa"
[    0.784699] (II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
[    0.824516] (II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.824688] (II) LoadModule: "fbdev"
[    0.825324] (II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
[    0.830671] (II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
[    0.830843] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800
[    0.831200] (II) VESA: driver for VESA chipsets: vesa
[    0.831256] (II) FBDEV: driver for framebuffer: fbdev
[    0.834857] (II) Primary Device is: PCI 01@00:00:0
[    0.834973] (!!) VIA Technologies does not support this driver in any way.
[    0.835003] (!!) For support, please refer to http://www.openchrome.org/.
[    0.835023] (!!) (development build, compiled on Fri Feb 13 08:34:27 2009)
[    0.835055] (WW) Falling back to old probe method for vesa
[    0.835103] (WW) Falling back to old probe method for fbdev
[    0.835218] (II) Loading sub module "fbdevhw"
[    0.835250] (II) LoadModule: "fbdevhw"
[    0.835471] (II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
[    0.850825] (II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
[    0.851142] (EE) open /dev/fb0: No such file or directory
[    0.851253] (II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.950283] (II) CHROME(0): VIAPreInit
[    0.950350] (II) Loading sub module "vgahw"
[    0.950368] (II) LoadModule: "vgahw"
[    0.950611] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.950931] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.951057] (II) CHROME(0): VIAGetRec
[    0.951094] (II) CHROME(0): Creating default Display subsection in Screen section
	"Builtin Default openchrome Screen 0" for depth/fbbpp 24/32
[    0.951127] (==) CHROME(0): Depth 24, [    0.951142] (--) framebuffer bpp 32
[    0.951165] (==) CHROME(0): RGB weight 888
[    0.951186] (==) CHROME(0): Default visual is TrueColor
[    0.951217] (--) CHROME(0): Chipset: P4M900/VN896/CN896
[    0.951301] (--) CHROME(0): Chipset revision: 0
[    0.951354] (--) CHROME(0): Probed amount of VideoRAM = 131072 kB
[    0.951373] (II) CHROME(0): Setting up default chipset options.
[    0.951391] (II) CHROME(0): VIASetupDefaultOptions
[    0.951448] (II) CHROME(0): Reading config file...
[    0.951493] (II) CHROME(0): Starting to parse config file options...
[    0.951511] (==) CHROME(0): Shadow framebuffer is disabled.
[    0.951522] (==) CHROME(0): Hardware acceleration is enabled.
[    0.951538] (==) CHROME(0): Using XAA acceleration architecture.
[    0.951551] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[    0.951565] (==) CHROME(0): GPU virtual command queue will be enabled.
[    0.951577] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[    0.951590] (==) CHROME(0): AGP DMA will be disabled if DRI is enabled.
[    0.951602] (==) CHROME(0): PCI DMA will not be used for XV image transfer if DRI is enabled.
[    0.951615] (==) CHROME(0): Will not enable VBE modes.
[    0.951626] (==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
[    0.951639] (==) CHROME(0): Xv Bandwidth check is enabled.
[    0.951651] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[    0.951663] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[    0.951675] (==) CHROME(0): Digital output bus width is 12 bits.
[    0.951688] (==) CHROME(0): DVI Center is disabled.
[    0.951699] (==) CHROME(0): Panel size is not selected from config file.
[    0.951711] (==) CHROME(0): Panel will not be forced.
[    0.951722] (==) CHROME(0): TV dotCrawl is disabled.
[    0.951734] (==) CHROME(0): TV deflicker is set to 0.
[    0.951745] (==) CHROME(0): No default TV type is set.
[    0.951757] (==) CHROME(0): No default TV output signal type is set.
[    0.951776] (II) CHROME(0): VIAMapMMIO
[    0.951788] (--) CHROME(0): mapping MMIO @ 0xfc000000 with size 0x9000
[    0.951894] (--) CHROME(0): mapping BitBlt MMIO @ 0xfc200000 with size 0x200000
[    0.951999] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.952019] (==) CHROME(0): Will not print VGA registers.
[    0.952031] (==) CHROME(0): Will not scan I2C buses.
[    0.952043] (II) CHROME(0): ...Finished parsing config file options.
[    0.952062] (--) CHROME(0): Detected Hewlett Packard 2133 Mini-Note.
[    0.952076] (II) CHROME(0): Detected MemClk 8
[    0.952090] (II) CHROME(0): ViaGetMemoryBandwidth
[    0.952104] (II) CHROME(0): Detected TV standard: PAL.
[    0.952120] (==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.952152] (II) Loading sub module "i2c"
[    0.952163] (II) LoadModule: "i2c"
[    0.952199] (II) Module "i2c" already built-in
[    0.952212] (II) CHROME(0): ViaI2CInit
[    0.981454] (II) CHROME(0): ViaI2CBus1Init
[    0.981526] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[    0.981544] (II) CHROME(0): ViaI2cBus2Init
[    0.981556] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[    0.981568] (II) CHROME(0): ViaI2CBus3Init
[    0.981580] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[    0.981591] (II) Loading sub module "ddc"
[    0.981602] (II) LoadModule: "ddc"
[    0.981635] (II) Module "ddc" already built-in
[    0.981671] (II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
[    0.981688] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[    0.985210] (II) CHROME(0): ViaOutputsDetect
[    0.985234] (II) CHROME(0): Enabling panel from PCI-subsystem ID information.
[    0.985247] (II) CHROME(0): Will not try to detect TV encoder.
[    0.985260] (II) CHROME(0): ViaOutputsSelect
[    0.985271] (II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
[    0.985284] (II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
[    0.985298] (II) CHROME(0): ViaOutputsSelect: Panel.
[    0.985322] (II) CHROME(0): ViaPanelPreInit
[    0.985334] (II) CHROME(0): VIAGetPanelSizeFromDDCv1
[    0.985647] (II) CHROME(0): ViaPanelGetNativeModeFromScratchPad
[    0.985663] (II) CHROME(0): Native Panel Resolution is 1366x768
[    0.985675] (II) CHROME(0): ViaPanelGetNativeDisplayMode
[    0.985737] (II) CHROME(0): NativeModeIndex: 9
[    0.985751] (II) CHROME(0): ViaModesAttach
[    0.985811] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 29.677456
[    0.985865] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 48.383930
[    0.985884] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 53.692764
[    0.985902] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 60.155556
[    0.985918] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 64.146919
[    0.985937] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 65.279785
[    0.985954] (II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 74.904167
[    0.985978] (II) CHROME(0): <default monitor>: Using hsync range of 29.68-74.90 kHz
[    0.986001] (II) CHROME(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    0.986037] (WW) CHROME(0): Unable to estimate virtual size
[    0.986050] (II) CHROME(0): Clock range:  20.00 to 230.00 MHz
[    0.986072] (II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
[    0.986088] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986107] (II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
[    0.986121] (II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    0.986135] (II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
[    0.986147] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986159] (II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
[    0.986172] (II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    0.986185] (II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
[    0.986197] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986209] (II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
[    0.986222] (II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    0.986235] (II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
[    0.986247] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986502] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    0.986518] (II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
[    0.986530] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986542] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[    0.986554] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    0.986567] (II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
[    0.986579] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986591] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[    0.986604] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    0.986617] (II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
[    0.986629] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986641] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[    0.986654] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    0.986667] (II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
[    0.986679] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986691] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    0.986704] (II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
[    0.986716] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986729] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    0.986742] (II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
[    0.986754] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986766] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[    0.986779] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    0.986791] (II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
[    0.986803] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986815] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[    0.986828] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    0.986861] (II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
[    0.986874] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986886] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[    0.986899] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    0.986912] (II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
[    0.986924] (II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
[    0.986938] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    0.986951] (II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
[    0.986963] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.986976] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    0.986989] (II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
[    0.987002] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987014] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    0.987027] (II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
[    0.987040] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987195] (II) CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.987208] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    0.987220] (II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
[    0.987233] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987245] (II) CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.987257] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    0.987270] (II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
[    0.987282] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987294] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.987307] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.987320] (II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
[    0.987332] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987344] (II) CHROME(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    0.987356] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    0.987369] (II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
[    0.987382] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987393] (II) CHROME(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    0.987406] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    0.987419] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
[    0.987431] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987442] (II) CHROME(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.987455] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    0.987468] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
[    0.987480] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987491] (II) CHROME(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.987504] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    0.987517] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
[    0.987529] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987540] (II) CHROME(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.987553] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    0.987565] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (162000)
[    0.987578] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987589] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.987601] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    0.987614] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (175500)
[    0.987626] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987653] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.987666] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    0.987679] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (189000)
[    0.987692] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987703] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.987715] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    0.987728] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (202500)
[    0.987740] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987752] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.987764] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    0.987777] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (229500)
[    0.987789] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987800] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.987813] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    0.987826] (II) CHROME(0): ViaValidMode: Validating 1792x1344 (204800)
[    0.987838] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987849] (II) CHROME(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    0.987862] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    0.987874] (II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[    0.987887] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    0.987900] (II) CHROME(0): ViaValidMode: Validating 1856x1392 (218300)
[    0.987912] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.987924] (II) CHROME(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    0.987936] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    0.987949] (II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[    0.987962] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    0.987975] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    0.987988] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    0.988001] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    0.988014] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    0.988027] (II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
[    0.988039] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988051] (II) CHROME(0): Not using default mode "832x624" (vrefresh out of range)
[    0.988064] (II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    0.988077] (II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
[    0.988089] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988100] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988117] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988130] (II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
[    0.988142] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988153] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988166] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988179] (II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
[    0.988191] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988203] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988215] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988228] (II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
[    0.988241] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988252] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988279] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988293] (II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
[    0.988305] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988317] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988329] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988342] (II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
[    0.988355] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988366] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.988379] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    0.988392] (II) CHROME(0): ViaValidMode: Validating 1360x768 (72000)
[    0.988404] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988560] (II) CHROME(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.988573] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    0.988586] (II) CHROME(0): ViaValidMode: Validating 1360x768 (84750)
[    0.988598] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988755] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    0.988768] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (122000)
[    0.988780] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988792] (II) CHROME(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.988804] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    0.988817] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (145060)
[    0.988830] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988841] (II) CHROME(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.988854] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    0.988867] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (155800)
[    0.988879] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988890] (II) CHROME(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.988903] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    0.988916] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (179260)
[    0.988928] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988939] (II) CHROME(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.988952] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    0.988965] (II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
[    0.988977] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.988989] (II) CHROME(0): Not using default mode "1440x900" (exceeds panel dimensions)
[    0.989002] (II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    0.989015] (II) CHROME(0): ViaValidMode: Validating 1600x1024 (103125)
[    0.989027] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989038] (II) CHROME(0): Not using default mode "1600x1024" (exceeds panel dimensions)
[    0.989051] (II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    0.989064] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (119000)
[    0.989076] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989087] (II) CHROME(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.989100] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    0.989113] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (146250)
[    0.989126] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989137] (II) CHROME(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.989149] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    0.989163] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (174000)
[    0.989175] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989186] (II) CHROME(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.989216] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    0.989230] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (187000)
[    0.989242] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989253] (II) CHROME(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.989266] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    0.989279] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (214750)
[    0.989291] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989302] (II) CHROME(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    0.989315] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    0.989328] (II) CHROME(0): ViaValidMode: Validating 1920x1080 (138500)
[    0.989340] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989351] (II) CHROME(0): Not using default mode "1920x1080" (exceeds panel dimensions)
[    0.989364] (II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    0.989377] (II) CHROME(0): ViaValidMode: Validating 1920x1200 (154000)
[    0.989389] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989401] (II) CHROME(0): Not using default mode "1920x1200" (exceeds panel dimensions)
[    0.989413] (II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    0.989426] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    0.989439] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    0.989452] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    0.989464] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    0.989477] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    0.989490] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    0.989502] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    0.989515] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    0.989528] (II) CHROME(0): ViaValidMode: Validating 640x480 (25312)
[    0.989540] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989553] (II) CHROME(0): ViaValidMode: Validating 720x480 (26591)
[    0.989566] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989579] (II) CHROME(0): ViaValidMode: Validating 720x576 (32663)
[    0.989591] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989604] (II) CHROME(0): ViaValidMode: Validating 800x480 (40000)
[    0.989616] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989638] (II) CHROME(0): ViaValidMode: Validating 800x600 (39822)
[    0.989651] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989664] (II) CHROME(0): ViaValidMode: Validating 848x480 (33750)
[    0.989677] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989690] (II) CHROME(0): ViaValidMode: Validating 856x480 (31704)
[    0.989702] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989715] (II) CHROME(0): ViaValidMode: Validating 1024x512 (41164)
[    0.989727] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989740] (II) CHROME(0): ViaValidMode: Validating 1024x576 (46981)
[    0.989752] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989765] (II) CHROME(0): ViaValidMode: Validating 1024x600 (48960)
[    0.989777] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989933] (II) CHROME(0): ViaValidMode: Validating 1024x768 (65028)
[    0.989946] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989958] (II) CHROME(0): ViaValidMode: Validating 1152x864 (81613)
[    0.989971] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.989982] (II) CHROME(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    0.989995] (II) CHROME(0): ViaValidMode: Validating 1280x768 (81135)
[    0.990007] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990020] (II) CHROME(0): ViaValidMode: Validating 1280x720 (74600)
[    0.990047] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990204] (II) CHROME(0): ViaValidMode: Validating 1280x960 (108280)
[    0.990216] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990228] (II) CHROME(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    0.990240] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (108280)
[    0.990252] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990264] (II) CHROME(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    0.990276] (II) CHROME(0): ViaValidMode: Validating 1360x768 (85500)
[    0.990288] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990460] (II) CHROME(0): ViaValidMode: Validating 1366x768 (85860)
[    0.990473] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990629] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (122726)
[    0.990642] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990653] (II) CHROME(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    0.990666] (II) CHROME(0): ViaValidMode: Validating 1440x900 (106470)
[    0.990678] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990689] (II) CHROME(0): Not using default mode "1440x900" (exceeds panel dimensions)
[    0.990702] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (161793)
[    0.990714] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990725] (II) CHROME(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    0.990737] (II) CHROME(0): ViaValidMode: Validating 1920x1080 (172900)
[    0.990750] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990761] (II) CHROME(0): Not using default mode "1920x1080" (exceeds panel dimensions)
[    0.990789] (II) CHROME(0): ViaValidMode: Validating 1366x768 (85860)
[    0.990803] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.990964] (II) CHROME(0): ViaValidMode: Validating 1360x768 (85500)
[    0.990977] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991138] (II) CHROME(0): ViaValidMode: Validating 1360x768 (84750)
[    0.991150] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991311] (II) CHROME(0): ViaValidMode: Validating 1280x768 (81135)
[    0.991323] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991341] (II) CHROME(0): ViaValidMode: Validating 1280x720 (74600)
[    0.991353] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991514] (II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
[    0.991527] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991544] (II) CHROME(0): ViaValidMode: Validating 1024x768 (65028)
[    0.991557] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991574] (II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
[    0.991587] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991604] (II) CHROME(0): ViaValidMode: Validating 1024x600 (48960)
[    0.991616] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991850] (II) CHROME(0): ViaValidMode: Validating 1024x576 (46981)
[    0.991867] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991884] (II) CHROME(0): ViaValidMode: Validating 1024x512 (41164)
[    0.991897] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991924] (II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
[    0.991937] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991954] (II) CHROME(0): ViaValidMode: Validating 800x600 (39822)
[    0.991966] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.991983] (II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
[    0.991996] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992012] (II) CHROME(0): ViaValidMode: Validating 720x576 (32663)
[    0.992024] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992041] (II) CHROME(0): ViaValidMode: Validating 856x480 (31704)
[    0.992053] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992069] (II) CHROME(0): ViaValidMode: Validating 848x480 (33750)
[    0.992082] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992098] (II) CHROME(0): ViaValidMode: Validating 800x480 (40000)
[    0.992110] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992126] (II) CHROME(0): ViaValidMode: Validating 720x480 (26591)
[    0.992138] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992154] (II) CHROME(0): ViaValidMode: Validating 640x480 (25312)
[    0.992183] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992199] (II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
[    0.992212] (II) CHROME(0): ViaSecondCRTCModeValid
[    0.992461] (--) CHROME(0): Virtual size is 1368x768 (pitch 1368)
[    0.992475] (**) CHROME(0): *Default mode "1366x768": 85.9 MHz, 47.7 kHz, 60.0 Hz
[    0.992510] (II) CHROME(0): Modeline "1366x768"x60.0   85.86  1366 1440 1584 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[    0.992535] (**) CHROME(0): *Default mode "1360x768": 85.5 MHz, 49.0 kHz, 60.7 Hz
[    0.992556] (II) CHROME(0): Modeline "1360x768"x60.7   85.50  1360 1392 1712 1744  768 783 791 807 +hsync +vsync (49.0 kHz)
[    0.992579] (**) CHROME(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[    0.992601] (II) CHROME(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.992624] (**) CHROME(0): *Default mode "1280x768": 81.1 MHz, 48.1 kHz, 59.9 Hz
[    0.992645] (II) CHROME(0): Modeline "1280x768"x59.9   81.14  1280 1328 1440 1688  768 770 776 802 +hsync -vsync (48.1 kHz)
[    0.992669] (**) CHROME(0): *Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
[    0.992690] (II) CHROME(0): Modeline "1280x720"x59.2   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync (44.2 kHz)
[    0.992713] (**) CHROME(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    0.992734] (II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.992757] (**) CHROME(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    0.992779] (II) CHROME(0): Modeline "1024x768"x60.0   65.03  1024 1048 1184 1344  768 770 776 806 -hsync -vsync (48.4 kHz)
[    0.992801] (**) CHROME(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    0.992822] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.992845] (**) CHROME(0): *Default mode "1024x600": 49.0 MHz, 37.3 kHz, 60.0 Hz
[    0.992867] (II) CHROME(0): Modeline "1024x600"x60.0   48.96  1024 1064 1168 1312  600 601 604 622 -hsync +vsync (37.3 kHz)
[    0.992890] (**) CHROME(0): *Default mode "1024x576": 47.0 MHz, 35.8 kHz, 60.0 Hz
[    0.992912] (II) CHROME(0): Modeline "1024x576"x60.0   46.98  1024 1064 1168 1312  576 576 579 597 -hsync +vsync (35.8 kHz)
[    0.992935] (**) CHROME(0): *Default mode "1024x512": 41.2 MHz, 31.8 kHz, 59.8 Hz
[    0.992956] (II) CHROME(0): Modeline "1024x512"x59.8   41.16  1024 1056 1160 1296  512 512 515 531 -hsync +vsync (31.8 kHz)
[    0.992979] (**) CHROME(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    0.993000] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.993023] (**) CHROME(0): *Default mode "800x600": 39.8 MHz, 37.7 kHz, 60.0 Hz
[    0.993044] (II) CHROME(0): Modeline "800x600"x60.0   39.82  800 840 968 1056  600 600 604 628 +hsync +vsync (37.7 kHz)
[    0.993067] (**) CHROME(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    0.993088] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.993111] (**) CHROME(0): *Default mode "720x576": 32.7 MHz, 35.8 kHz, 60.0 Hz
[    0.993132] (II) CHROME(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 576 579 597 -hsync +vsync (35.8 kHz)
[    0.993155] (**) CHROME(0): *Default mode "856x480": 31.7 MHz, 29.8 kHz, 60.0 Hz
[    0.993177] (II) CHROME(0): Modeline "856x480"x60.0   31.70  856 872 960 1064  480 480 483 497 -hsync +vsync (29.8 kHz)
[    0.993200] (**) CHROME(0): *Default mode "848x480": 33.8 MHz, 31.0 kHz, 60.0 Hz
[    0.993221] (II) CHROME(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 485 493 517 +hsync +vsync (31.0 kHz)
[    0.993243] (**) CHROME(0): *Default mode "800x480": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    0.993264] (II) CHROME(0): Modeline "800x480"x60.3   40.00  800 832 960 1056  480 541 545 628 -hsync +vsync (37.9 kHz)
[    0.993286] (**) CHROME(0): *Default mode "720x480": 26.6 MHz, 29.7 kHz, 59.7 Hz
[    0.993339] (II) CHROME(0): Modeline "720x480"x59.7   26.59  720 736 808 896  480 480 483 497 -hsync +vsync (29.7 kHz)
[    0.993364] (**) CHROME(0): *Default mode "640x480": 25.3 MHz, 31.6 kHz, 60.3 Hz
[    0.993386] (II) CHROME(0): Modeline "640x480"x60.3   25.31  640 656 752 800  480 489 491 525 -hsync -vsync (31.6 kHz)
[    0.993409] (**) CHROME(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    0.993431] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.993459] (==) CHROME(0): DPI set to (96, 96)
[    0.993471] (II) Loading sub module "fb"
[    0.993481] (II) LoadModule: "fb"
[    0.993683] (II) Loading /usr/lib/xorg/modules//libfb.so
[    0.994091] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.994160] (II) Loading sub module "xaa"
[    0.994171] (II) LoadModule: "xaa"
[    0.994316] (II) Loading /usr/lib/xorg/modules//libxaa.so
[    1.156687] (II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
[    1.156833] (II) Loading sub module "ramdac"
[    1.156852] (II) LoadModule: "ramdac"
[    1.156972] (II) Module "ramdac" already built-in
[    1.156996] (II) CHROME(0): VIAUnmapMem
[    1.157144] (II) UnloadModule: "vesa"
[    1.157168] (II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
[    1.157198] (II) UnloadModule: "fbdev"
[    1.157215] (II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
[    1.157233] (II) UnloadModule: "fbdevhw"
[    1.157249] (II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
[    1.157276] (--) Depth 24 pixmap format is 32 bpp
[    1.157293] (II) do I need RAC?  No, I don't.
[    1.157317] (II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    1.160007] (II) CHROME(0): VIAScreenInit
[    1.160026] (II) CHROME(0): VIAMapFB
[    1.160044] (--) CHROME(0): mapping framebuffer @ 0xd0000000 with size 0x8000000
[    1.162237] (--) CHROME(0): Frame buffer start: 0xaf83d000, free start: 0x402000 end: 0x8000000
[    1.162295] (II) CHROME(0): VIAMapMMIO
[    1.162313] (--) CHROME(0): mapping MMIO @ 0xfc000000 with size 0x9000
[    1.162423] (--) CHROME(0): mapping BitBlt MMIO @ 0xfc200000 with size 0x200000
[    1.162707] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    1.162745] (II) CHROME(0): VIASave
[    1.162764] (II) CHROME(0): Primary
[    1.383769] (II) CHROME(0): Crtc...
[    1.383836] (II) CHROME(0): TVSave...
[    1.383946] (II) CHROME(0): VIAWriteMode
[    1.383971] (II) CHROME(0): ViaModeSet
[    1.383985] (II) CHROME(0): Name: 1366x768
[    1.383996] (II) CHROME(0): Clock: 85860
[    1.384008] (II) CHROME(0): VRefresh: 60.000000
[    1.384031] (II) CHROME(0): HSync: 47.700001
[    1.384046] (II) CHROME(0): HDisplay: 1366
[    1.384058] (II) CHROME(0): HSyncStart: 1440
[    1.384070] (II) CHROME(0): HSyncEnd: 1584
[    1.384081] (II) CHROME(0): HTotal: 1800
[    1.384093] (II) CHROME(0): HSkew: 0
[    1.384104] (II) CHROME(0): VDisplay: 768
[    1.384115] (II) CHROME(0): VSyncStart: 769
[    1.384127] (II) CHROME(0): VSyncEnd: 772
[    1.384138] (II) CHROME(0): VTotal: 795
[    1.384150] (II) CHROME(0): VScan: 0
[    1.384161] (II) CHROME(0): Flags: 6
[    1.384172] (II) CHROME(0): CrtcHDisplay: 0x556
[    1.384184] (II) CHROME(0): CrtcHBlankStart: 0x556
[    1.384196] (II) CHROME(0): CrtcHSyncStart: 0x5a0
[    1.384208] (II) CHROME(0): CrtcHSyncEnd: 0x630
[    1.384219] (II) CHROME(0): CrtcHBlankEnd: 0x708
[    1.384231] (II) CHROME(0): CrtcHTotal: 0x708
[    1.384242] (II) CHROME(0): CrtcHSkew: 0x0
[    1.384253] (II) CHROME(0): CrtcVDisplay: 0x300
[    1.384265] (II) CHROME(0): CrtcVBlankStart: 0x300
[    1.384276] (II) CHROME(0): CrtcVSyncStart: 0x301
[    1.384288] (II) CHROME(0): CrtcVSyncEnd: 0x304
[    1.384299] (II) CHROME(0): CrtcVBlankEnd: 0x31b
[    1.384311] (II) CHROME(0): CrtcVTotal: 0x31b
[    1.384323] (II) CHROME(0): ViaModeSecondCRTC
[    1.384334] (II) CHROME(0): ViaPanelScale: 1366,768 -> 1366,768
[    1.384359] (II) CHROME(0): mode: 0x950d798
[    1.384371] (II) CHROME(0): mode->name: 0x95108a8
[    1.384383] (II) CHROME(0): mode->name: 1366x768
[    1.384394] (II) CHROME(0): ViaSecondCRTCSetMode
[    1.384405] (II) CHROME(0): Setting up 1366x768
[    1.384438] (II) CHROME(0): ViaSetSecondaryFIFO
[    1.384600] (II) CHROME(0): ViaSetSecondaryDotclock to 0x2e8800
[    1.384615] (II) CHROME(0): ViaSetUseExternalClock
[    1.384628] (II) CHROME(0): ViaSecondDisplayChannelEnable
[    1.384642] (II) CHROME(0): ViaDisplayDisableCRT
[    1.384654] (II) CHROME(0): ViaDisplayDisableSimultaneous
[    1.384714] (II) CHROME(0): VIAAdjustFrame
[    1.384741] (II) CHROME(0): VIAAdjustFrame
[    1.384755] (II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
[    1.881362] (EE) [drm] drmOpen failed.
[    1.881435] (EE) CHROME(0): [dri] DRIScreenInit failed.  Disabling DRI.
[    1.881504] (II) CHROME(0): - Visuals set up
[    1.881520] (II) CHROME(0): VIAInternalScreenInit
[    1.910916] (II) CHROME(0): - B & W
[    1.912480] (II) CHROME(0): CursorStart: 0x7fc0000
[    1.912617] (II) CHROME(0): Using 2304 lines for offscreen memory.
[    1.912782] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		17 256x256 slots
		5 512x512 slots
		32 8x8 color pattern slots
[    1.913987] (==) CHROME(0): Backing store disabled
[    1.914003] (II) CHROME(0): - Backing store set up
[    1.914947] (II) CHROME(0): - SW cursor set up
[    1.915182] (II) CHROME(0): VIAHWCursorInit
[    1.925465] (II) CHROME(0): - Def Color map set up
[    1.925583] (II) CHROME(0): VIALoadPalette
[    1.925603] (II) CHROME(0): VIALoadRgbLut
[    1.925717] (II) CHROME(0): - Palette loaded
[    1.925735] (II) CHROME(0): DPMS enabled
[    1.925746] (II) CHROME(0): - DPMS set up
[    1.925757] (II) CHROME(0): - Color maps etc. set up
[    1.925768] (II) CHROME(0): direct rendering disabled
[    1.934544] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[    1.952425] (--) CHROME(0): Timed   libc YUV420 copy... 9850055. Throughput: 96.1 MiB/s.
[    1.992202] (--) CHROME(0): Timed kernel YUV420 copy... 10831490. Throughput: 87.4 MiB/s.
[    2.027159] (--) CHROME(0): Timed    SSE YUV420 copy... 5452920. Throughput: 173.6 MiB/s.
[    2.062140] (--) CHROME(0): Timed    MMX YUV420 copy... 20019669. Throughput: 47.3 MiB/s.
[    2.062243] (--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
[    2.074876] (--) CHROME(0): Timed   MMX2 YUV420 copy... 6005785. Throughput: 157.7 MiB/s.
Freed 16815488 (pool 1)
[    2.075367] (--) CHROME(0): Using SSE YUV42X copy for video.
[    2.075520] (WW) CHROME(0): [XvMC] XvMC is not supported on this chipset.
[    2.075569] (II) CHROME(0): - Done
[    2.075613] (==) RandR enabled
[    2.111107] (II) Initializing built-in extension Generic Event Extension
[    2.113885] (II) Initializing built-in extension SHAPE
[    2.113932] (II) Initializing built-in extension MIT-SHM
[    2.113944] (II) Initializing built-in extension XInputExtension
[    2.113954] (II) Initializing built-in extension XTEST
[    2.113964] (II) Initializing built-in extension BIG-REQUESTS
[    2.113975] (II) Initializing built-in extension SYNC
[    2.113985] (II) Initializing built-in extension XKEYBOARD
[    2.114036] (II) Initializing built-in extension XC-MISC
[    2.114048] (II) Initializing built-in extension SECURITY
[    2.114058] (II) Initializing built-in extension XINERAMA
[    2.114068] (II) Initializing built-in extension XFIXES
[    2.114078] (II) Initializing built-in extension RENDER
[    2.114088] (II) Initializing built-in extension RANDR
[    2.114097] (II) Initializing built-in extension COMPOSITE
[    2.114107] (II) Initializing built-in extension DAMAGE
[    2.159502] (II) AIGLX: Screen 0 is not DRI2 capable
[    2.159582] (II) AIGLX: Screen 0 is not DRI capable
[    2.350619] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    2.350709] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    4.726549] (II) config/hal: Adding input device AT Translated Set 2 keyboard
[    4.726637] (II) LoadModule: "evdev"
[    4.726930] (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[    4.747389] (II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
[    4.747563] (**) AT Translated Set 2 keyboard: always reports core events
[    4.747589] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
[    4.747747] (II) AT Translated Set 2 keyboard: Found keys
[    4.747768] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    4.747835] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    4.747883] (**) Option "xkb_rules" "evdev"
[    4.747907] (**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
[    4.747920] (**) Option "xkb_model" "pc105"
[    4.747941] (**) AT Translated Set 2 keyboard: xkb_model: "pc105"
[    4.747954] (**) Option "xkb_layout" "be"
[    4.747975] (**) AT Translated Set 2 keyboard: xkb_layout: "be"
[    4.747994] (**) Option "xkb_options" "lv3:ralt_switch"
[    4.748015] (**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
[    5.117125] (II) config/hal: Adding input device Video Bus
[    5.117783] (**) Video Bus: always reports core events
[    5.117842] (**) Video Bus: Device: "/dev/input/event7"
[    5.130557] (II) Video Bus: Found keys
[    5.130649] (II) Video Bus: Configuring as keyboard
[    5.130713] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    5.130754] (**) Option "xkb_rules" "evdev"
[    5.130779] (**) Video Bus: xkb_rules: "evdev"
[    5.130792] (**) Option "xkb_model" "pc105"
[    5.130813] (**) Video Bus: xkb_model: "pc105"
[    5.130826] (**) Option "xkb_layout" "be"
[    5.130847] (**) Video Bus: xkb_layout: "be"
[    5.130866] (**) Option "xkb_options" "lv3:ralt_switch"
[    5.130887] (**) Video Bus: xkb_options: "lv3:ralt_switch"
[    5.413216] (II) config/hal: Adding input device Macintosh mouse button emulation
[    5.413352] (**) Macintosh mouse button emulation: always reports core events
[    5.413374] (**) Macintosh mouse button emulation: Device: "/dev/input/event4"
[    5.430520] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[    5.430584] (II) Macintosh mouse button emulation: Found x and y relative axes
[    5.430598] (II) Macintosh mouse button emulation: Configuring as mouse
[    5.430637] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    5.430652] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    5.430699] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    5.430802] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    5.430822] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[    5.430843] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[    5.430886] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[    5.438802] (II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
[    5.438883] (II) LoadModule: "synaptics"
[    5.439280] (II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
[    5.469210] (II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
[    5.469348] (II) Synaptics touchpad driver version 0.99.3
[    5.469398] (**) Option "Device" "/dev/input/event10"
[    5.489007] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    5.489071] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    5.489087] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    5.489099] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    5.489121] (II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
[    5.489240] (--) SynPS/2 Synaptics TouchPad touchpad found
[    5.489268] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    5.514585] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    5.514740] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    5.514762] (**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
[    5.514784] (**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
[    5.514816] (**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
[    5.525264] (--) SynPS/2 Synaptics TouchPad touchpad found
[    6.086164] (II) CHROME(0): VIAAdjustFrame
[    6.086257] (II) CHROME(0): VIAAdjustFrame


```

---

