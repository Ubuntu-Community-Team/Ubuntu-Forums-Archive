---
title: "kdm and gdm problem when installing NVidia driver for 8800GT"
date: 2009-05-12
forum: Hardware
---

### Post by starsheeep on 2009-05-12
Hello, I'm trying to setup the 9.04 Jackalope, Kubundu and Ubuntu.

The rig has two 8800GT SLI GPU's, for now I don't care about SLI, just want the NVidia drivers to work.

After installing I tried activating the NVidia restricted drivers (1.80, 1.7x, 1.85 and the Beta 1.85.18.08 ) the result when rebooting is that the computer stops at "* Checking battery state..."

So far so good, now starts the funny part!:(
No error post, the machine just stops there. Pressing Ctrl+Alt+F1, login in and running sudo /etc/init.d/gdm start (or kdm) returns 'kdm already running', if I use the reload flag it returns to shell prompt and the monitor flashes a couple of times.
EDIT: changing the driver in xorg.conf to 'vesa' won't work, I have to uninstall the driver to be able to boot with GUI.

NOTICE: If I use ext4 for root partition, RAID will also fail in the second reboot, 1st reboot hangs, 2nd reboot prompts to login with raid errors.
I did not record the errors at the time, but while messing around I found out that this would happen only when activating the NVidia drivers, using ext3 solved this.

Thats it! tried to find some relative thread, but I couldn't find anything with no error post, maybe theres a log I should look to but I'm not that familiar with the OS.

Thank you for your time, any help appreciated.


EDIT: Found the LOG

START OF LOG
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Hephaistos 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 12 18:01:40 2009
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@3:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xcc000000/16777216, 0xa0000000/536870912, 0xca000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xc8000000/16777216, 0x80000000/536870912, 0xc6000000/33554432, I/O @ 0x00008c00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.08  Thu Apr 30 16:17:08 PDT 2009
(II) Loading extension GLX
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

[COLOR="Red"]Fatal server error:
no screens found[/COLOR]

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```
END OF LOG

START OF  xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
END OF  xorg.conf

---

### Post by starsheeep on 2009-05-12
Solved.

Thanks to this [thread]("http://ubuntuforums.org/showthread.php?t=1139101") by [ed-koala]("http://ubuntuforums.org/member.php?u=397691").

> Now, perform the following command in a terminal:

sudo lspci | grep VGA

The output will look something like this:

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)

Write down the number begining each line (the 02:00:0 and 03:00:0 or whatever your output shows).

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>

nvidia-180-lidvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common


Open terminal and type:

sudo gedit /etc/X11/xorg.conf

Replace the graphics "Device" section with the following:

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:1:0:0"
Driver "nvidia"
EndSection

Edit the BusID line to reflect the number you wrote down earlier (for me, that would be "PCI:2:0:0". ***MAKE SURE*** you use all colons as shown (the original line you copied had a period before the last zero), and add the PCI part as shown.

If you have sli, add the following line after the driver line:

Option "sli" "auto"

Save the file, reboot and you should have 3d graphics working.

***NOTE*** - for dual graphic card PCs, you may boot to a black screen but you'll hear the normal boot sounds. If that happens, use the other number you got from earlier OR plug your monitor into the other card.


This got Nvidia's restricted driver working for me after a number of other solutions failed. After this, upgrading within Jaunty releases should go smoothly, but save this in case the next OS update screws you again.

---

