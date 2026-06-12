---
title: "Seemingly no way to fix screen resolution [notebook Asus K54H]"
date: 2012-01-29
forum: Hardware
---

### Post by Sleesh on 2012-01-29
Hey guys,
i just made myself an account for this forum, because my ideas to fix my problem are running low...


_overview (naming the things i think are important):_
- **Ubuntu 10.04 LTS** with macbuntu (don't care 'bout it, i tried it without macbuntu and the problem was the same)
- **Asus K54H-SO166V**
     monitor: 15,6" notebook
     cpu: Intel Pentium CPU B940 @ 2.00GHz (clock: 800MHz)
     gfxcard: Intel HD Graphics (SubVendor: ASUSTeK)
     monitor: unknown (originally 15,6" HD LED Backlight)


And that mainly is the problem: as described from many laptop owners my screen resolution can't be set to 1366x768, only to 800x600 or 1024x768

that ofcourse is, because the monitor is unknown...

i tried to get informations about how ubuntu gets along with my screen, although it's unknown, with the "hwinfo" package. the "hwinfo" package gives me very detailed information about every little bit of everything, but if i give him the command "hwinfo --monitor" - which is the command line for getting information via the terminal with this package - he simply gives nothing,nada,niente,nichts -.-

if i start "hardware drivers", it searches for quite some time, but the only message he has for me is: "No proprietary drivers are in use on this system"

xorg.conf doesn't exist. i read somewhere, that i can just create it, but i don't know how...

i really don't know what to try out next - it just seems unsolveable for a newbie like me...

please post every little bit of help and tips here, but consider, that i don't know that much about ubuntu/linux

and last but not least: sorry for my english, i'm not that good by now (I am German...)

---

### Post by wolfen69 on 2012-01-29
You may want to try the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa").

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
then
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

Ask if you have any questions.

---

### Post by Sleesh on 2012-01-29
well, that worked just fine, but it did change exactly nothing... :/

some of the text in the terminal said "amd" or "ati" (don't remember correctly) - maybe that one thought i have an amd gfxcard?

edit: i already restarted, no difference...

---

### Post by Sleesh on 2012-01-30
anyone some ideas? i studied almost EVERY forum and wiki about ubuntu... and still no clue...

---

### Post by MoreOrLess on 2012-01-30
The open-source ati driver is installed by default, so you probably saw that getting updated (just ignore it). Can you post/pastebin your /var/log/Xorg.0.log ?

---

### Post by Sleesh on 2012-01-31
i tried to manually create xorg.conf and to force him into "1366x768" but it didn't wokr, as you will see in the logfile:

[SIZE="4"]xOrg.0.log[/SIZE]
[    14.746] 
X.Org X Server 1.8.2
Release Date: 2010-07-01
[    14.746] X Protocol Version 11, Revision 0
[    14.746] Build Operating System: Linux 2.6.24-27-xen x86_64 Ubuntu
[    14.746] Current Operating System: Linux PaulAmosKreiner 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64
[    14.746] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=7df6641f-2b03-4f99-8e47-dad4b99cf4b5 ro quiet splash
[    14.746] Build Date: 08 July 2010  01:50:43AM
[    14.746] xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.746] Current version of pixman: 0.21.4
[    14.746] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    14.746] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.746] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 31 11:41:38 2012
[    14.746] (==) Using config file: "/etc/X11/xorg.conf"
[    14.746] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.755] (==) ServerLayout "X.org Configured"
[    14.755] (**) |-->Screen "DefaultScreen" (0)
[    14.755] (**) |   |-->Monitor "Monitor0"
[    14.756] (**) |   |-->Device "Card0"
[    14.756] (**) |-->Input Device "Mouse0"
[    14.756] (**) |-->Input Device "Keyboard0"
[    14.756] (==) Automatically adding devices
[    14.756] (==) Automatically enabling devices
[    14.756] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.756] 	Entry deleted from font path.
[    14.756] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.756] 	Entry deleted from font path.
[    14.756] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.756] (**) ModulePath set to "/usr/lib/xorg/modules"
[    14.756] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.756] (WW) Disabling Mouse0
[    14.756] (WW) Disabling Keyboard0
[    14.756] (II) Loader magic: 0x7cea40
[    14.756] (II) Module ABI versions:
[    14.756] 	X.Org ANSI C Emulation: 0.4
[    14.756] 	X.Org Video Driver: 7.0
[    14.756] 	X.Org XInput driver : 9.0
[    14.756] 	X.Org Server Extension : 3.0
[    14.790] (--) PCI:*(0:0:2:0) 8086:0106:1043:13c7 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xdd000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    14.790] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.790] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    14.790] (II) LoadModule: "dbe"
[    14.790] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.790] (II) Module dbe: vendor="X.Org Foundation"
[    14.790] 	compiled for 1.8.2, module version = 1.0.0
[    14.790] 	Module class: X.Org Server Extension
[    14.790] 	ABI class: X.Org Server Extension, version 3.0
[    14.790] (II) Loading extension DOUBLE-BUFFER
[    14.790] (II) LoadModule: "dri2"
[    14.791] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.791] (II) Module dri2: vendor="X.Org Foundation"
[    14.791] 	compiled for 1.8.2, module version = 1.2.0
[    14.791] 	ABI class: X.Org Server Extension, version 3.0
[    14.791] (II) Loading extension DRI2
[    14.791] (II) LoadModule: "glx"
[    14.791] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.791] (II) Module glx: vendor="X.Org Foundation"
[    14.791] 	compiled for 1.8.2, module version = 1.0.0
[    14.791] 	ABI class: X.Org Server Extension, version 3.0
[    14.791] (==) AIGLX enabled
[    14.791] (II) Loading extension GLX
[    14.791] (II) LoadModule: "extmod"
[    14.791] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.791] (II) Module extmod: vendor="X.Org Foundation"
[    14.791] 	compiled for 1.8.2, module version = 1.0.0
[    14.791] 	Module class: X.Org Server Extension
[    14.791] 	ABI class: X.Org Server Extension, version 3.0
[    14.791] (II) Loading extension MIT-SCREEN-SAVER
[    14.791] (II) Loading extension XFree86-VidModeExtension
[    14.791] (II) Loading extension XFree86-DGA
[    14.791] (II) Loading extension DPMS
[    14.791] (II) Loading extension XVideo
[    14.791] (II) Loading extension XVideo-MotionCompensation
[    14.791] (II) Loading extension X-Resource
[    14.791] (II) LoadModule: "dri"
[    14.791] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.791] (II) Module dri: vendor="X.Org Foundation"
[    14.791] 	compiled for 1.8.2, module version = 1.0.0
[    14.791] 	ABI class: X.Org Server Extension, version 3.0
[    14.791] (II) Loading extension XFree86-DRI
[    14.791] (II) LoadModule: "record"
[    14.792] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.792] (II) Module record: vendor="X.Org Foundation"
[    14.792] 	compiled for 1.8.2, module version = 1.13.0
[    14.792] 	Module class: X.Org Server Extension
[    14.792] 	ABI class: X.Org Server Extension, version 3.0
[    14.792] (II) Loading extension RECORD
[    14.792] (II) LoadModule: "fbdev"
[    14.792] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.792] (II) Module fbdev: vendor="X.Org Foundation"
[    14.792] 	compiled for 1.8.2, module version = 0.4.2
[    14.792] 	ABI class: X.Org Video Driver, version 7.0
[    14.792] (II) FBDEV: driver for framebuffer: fbdev
[    14.792] (++) using VT number 7

[    14.792] (II) Loading sub module "fbdevhw"
[    14.792] (II) LoadModule: "fbdevhw"
[    14.792] (II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
[    14.792] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.792] 	compiled for 1.8.2, module version = 0.0.2
[    14.792] 	ABI class: X.Org Video Driver, version 7.0
[    14.792] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    14.792] (II) FBDEV(0): using default device
[    14.792] (**) FBDEV(0): Depth 16, (--) framebuffer bpp 16
[    14.792] (==) FBDEV(0): RGB weight 565
[    14.792] (==) FBDEV(0): Default visual is TrueColor
[    14.792] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.792] (II) FBDEV(0): hardware: VGA16 VGA (video memory: 64kB)
[    14.792] (II) FBDEV(0): checking modes against framebuffer device...
[    14.792] (II) FBDEV(0): 	mode "1366x768" not found
[    14.792] (II) FBDEV(0): checking modes against monitor...
[    14.792] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    14.792] (**) FBDEV(0):  Built-in mode "current": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    14.792] (II) FBDEV(0): Modeline "current"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync -csync (31.5 kHz)
[    14.792] (==) FBDEV(0): DPI set to (96, 96)
[    14.792] (EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver
[    14.792] 
Backtrace:
[    14.821] 0: /usr/bin/X (xorg_backtrace+0x28) [0x468ad8]
[    14.821] 1: /usr/bin/X (0x400000+0x58589) [0x458589]
[    14.821] 2: /lib/libpthread.so.0 (0x7ff1699f6000+0xf8f0) [0x7ff169a058f0]
[    14.821] 3: /lib/libc.so.6 (cfree+0x40) [0x7ff1689ade50]
[    14.821] 4: /usr/bin/X (xf86DeleteMode+0x45) [0x515705]
[    14.821] 5: /usr/bin/X (xf86DeleteScreen+0xa0) [0x46d380]
[    14.821] 6: /usr/bin/X (InitOutput+0x9fc) [0x47434c]
[    14.821] 7: /usr/bin/X (0x400000+0x25f25) [0x425f25]
[    14.821] 8: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7ff16894ec4d]
[    14.821] 9: /usr/bin/X (0x400000+0x25c79) [0x425c79]
[    14.821] Segmentation fault at address 0x7ff164000000
[    14.822] 
Fatal server error:
[    14.822] Caught signal 11 (Segmentation fault). Server aborting
[    14.822] 
[    14.822] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.822] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.822]


wow, it automatically created a smiley in between the log-text :D

---

### Post by MoreOrLess on 2012-01-31
WHy are you using the fbdev driver? What video card do you have?
```
lspci | grep VGA
```

---

### Post by Sleesh on 2012-01-31
i don't know what an fbdriver is and i did not install it (atleast not on purpose)

i have - as said - an Intel HD Graphics card

---

### Post by MoreOrLess on 2012-01-31
Oh, you're trying to use an intel sandy bridge GPU on Lucid. To do that, you need a newer kernel (try the 3.0 kernel from lucid-proposed).

---

### Post by Sleesh on 2012-01-31
Thank you so much! that worked :)

---

