---
title: "Change repositories through command line"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by TheFoe92 on 2009-09-05
I recently downloaded a copy of the Xubuntu alternate CD (the regular did not work, obviously), and installing it was a breeze. Unfortunately, to my dismay, I found out that while the installation went fine, booting up into Xubuntu is currently not an option. Among many other problems I have encountered, I do not have a GUI, so I am trying to repair the computer through a shell in command line. For the heck of it, because nothing else is working (for now), I wanted to try to upgrade. Then I fiugred out that I have 8.04 LTS and I couldn't upgrade until 10.04. My question is this: how do I upgrade from a LTS release to a regular one without a GUI? I tried decyphering which line it could be in the sources.list file but to no avail. Any suggestions? Thanks in advance.

---

### Post by bear24rw on 2009-09-05
you can sudo aptitude install xubuntu-desktop to get a gui real quick..

---

### Post by snowpine on 2009-09-05
Hi there, if I understand your question correctly, you are looking for a Xubuntu 9.04 Alternate CD, is that correct? 

[http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/)

---

### Post by TheFoe92 on 2009-09-05
No, I already have Xubuntu installed. I tried both CDs; the regular didn't work, so I installed it using the alternate.

I've tried using aptitude install xubuntu-desktop, but it reads 0 packages upgrade, 0 newly installed, 0 to remove and 0 not upgraded. If I then use startx, it leads to [this problem]("http://ubuntuforums.org/showthread.php?t=1255432").

---

### Post by oldos2er on 2009-09-05
What make/model video card do you have? If you don't know, can you post the output of **lspci** ?

---

### Post by TheFoe92 on 2009-09-06
After running the command, it gives me a list of different hardware parts. Among all the other hardware parts, the 'VGA compatible controller' seems like the most logical one. It reads 'Trident Microsystems CyberBlade/i1 (rev 5d).'

---

### Post by TheFoe92 on 2009-09-06
I figured out a way to upgrade to 9.04. After some more researching, I found some sort of driver for the CyberBlade. 
Now it tells me that no screens are found and that 'no such file or directory (errno 2): unable to connect to X server' and also 'no such process (errno 3): Server error.' I'm guessing this is some sort of improvement: it means something happened. The good thing is that now, instead of the computer freezing after every time I type in startx, I can get back to the commandline immediately.

---

### Post by earthpigg on 2009-09-06
> **TheFoe92 said:**
> No, I already have Xubuntu installed. I tried both CDs; the regular didn't work, so I installed it using the alternate.

I've tried using aptitude install xubuntu-desktop, but it reads 0 packages upgrade, 0 newly installed, 0 to remove and 0 not upgraded. If I then use startx, it leads to [this problem]("http://ubuntuforums.org/showthread.php?t=1255432").

verify that you have an internet connection:
```
ping -c 5 google.com
```

and look for this to verify your connection is good:
```
5 packets transmitted, 5 received, 0% packet loss
```

then run this, to update the list of available packages:
```
sudo apt-get update
```

then try installing xubuntu-desktop:
```

sudo apt-get install xubuntu-desktop
```


edit: also, how much RAM does your system have, out of curiosity?

---

### Post by TheFoe92 on 2009-09-07
I have 248 MB of RAM. I do have a good connection: I downloaded the 8.10 and 9.04 upgrades just yesterday.

Here is my Xorg.0.log file in case it helps:

```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntuEddie 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  6 20:57:33 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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

(--) PCI:*(0@1:0:0) Trident Microsystems CyberBlade/i1 rev 93, Mem @ 0xff000000/8388608, 0xfefe0000/131072, 0xfe000000/8388608, BIOS @ 0x????????/65536
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
	compiled for 7.4.0, module version = 1.0.0
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
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
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
	compiled for 7.1.1, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(EE) module ABI major version (1) doesn't match the server's version (5)
(II) UnloadModule: "trident"
(II) Unloading /usr/lib/xorg/modules/drivers//trident_drv.so
(EE) Failed to load module "trident" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

---

### Post by oldos2er on 2009-09-07
A Trident video card must be fairly old, I would think. Still, it should at least give you a GUI. Try running ```
sudo apt-get update && sudo apt-get purge xserver-xorg-video-trident && sudo apt-get install xserver-xorg-video-trident
```

---

