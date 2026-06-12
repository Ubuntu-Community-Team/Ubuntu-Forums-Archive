---
title: "Screen resolution Broken  automagically..."
date: 2009-03-26
forum: Hardware
---

### Post by Marcelo Ramone on 2009-03-26
Today when I log in on ubuntu 8.10, error messages appeared about x server ...

My 1440 x 900 resolution is broken, since then I'm trying to recover it without success.

I tried with:```
marcelo@linux:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for marcelo: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090327003239
marcelo@linux:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090327003259
marcelo@linux:~$ 
```

And: ```
marcelo@linux:~$ xrandr --output VGA --mode 1440x900 --rate 60
```
 but nothing works...
```
marcelo@linux:~$ xrandr -q
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
marcelo@linux:~$ 
```


 I have the X server log I can see  when i  login :

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 27 00:25:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfde80000/0, 0xd0000000/0, 0xfde40000/0, I/O @ 0x0000cc00/0
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.4.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFDE80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945G Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
```
no screens found

***Is there a way to recover the 1400x900 resolution that  always I used?***

This happened today when I logged on GNOME.

---

### Post by Marcelo Ramone on 2009-04-20
Hello.

Any help please?

My Ubuntu is running in Low Graphics Mode. The options showed before GDM screen don't work, i created a new configuration but always run in low graphics mode after restart. The screens looks ugly.

---

### Post by go2dell on 2009-04-21
Can you post the contents of your */etc/X11/xorg.conf*?

If I'm not mistaken, when you reconfigured you told your system to use a VGA output (--output VGA), meaning a physical connector into which you would normally plug an external monitor.  My notebook with Intel video shows the connection for the notebook's screen to be called LVDS, but yours appears to be called *default*.

Also, have you tried booting into Recovery Mode and reparing from there?

As a troubleshooting step, do you have either a bootable Ubuntu system CD or something like Knoppix lying around?  If booting from a CD gives you full resolution then you'll know the problem is somewhere in your Ubuntu install.  If not, then it's possible it's a hardware issue.

---

### Post by Marcelo Ramone on 2009-04-21
Hello.

In the Windows partition the resolution is fine (1440x900) 

The file content here: 

> 
marcelo@linux:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
marcelo@linux:~$ 


I not try from recovery mode yet.

I will try it.

---

### Post by go2dell on 2009-04-22
First off, I'll say that I've seen Windows drivers do goofy things to hardware so that it wouldn't work properly in any other OS.  I really haven't seen that sort of thing for video cards for years; it's more common on sound cards in my experience.

The only thing I see that's not completely standard is this line:
```
Option "UseFBDev" "true"
```

Just wondering if you added that manually.  Try editing xorg.conf to comment out that line (put a # character in front) and starting X.

If that doesn't work, then my only other guess is that the X server somehow became corrupted.  It may be worth a shot running fsck while you're in recovery mode, unless this is something you already do on a regular basis.

The final step I would try is reinstalling the X server:
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Beyond that you're likely to need help from somebody else with your exact machine because I'll risk breaking more than I fix.

Good luck!

---

### Post by Marcelo Ramone on 2009-04-22
Manually I'm trying to configure the video:

```

Section "Device"
        Identifier      "Configured Video Device"
      # Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Video Device"
        Device          "Configured Monitor"
        DefaultDepth    24
        SubSection      "Display"
        Viewport        0 0
        Depth           24
        Modes           "1440x900"
        EndSubSection
EndSection


```

I reinstalled the video driver.

But, the problem persist.

---

### Post by go2dell on 2009-04-22
I was looking at your Xorg log again and noticed that there is a warning about an invalid video BIOS checksum.  Was this warning in your logs before the problems started?

I'm wondering if maybe you flashed your computer's BIOS to a new version, or made any other changes to the machine before the resolution stopped being detected correctly.

Have you tried booting from a Live CD/DVD, like Ubuntu, Knoppix, or pretty much any other one?

---

### Post by Marcelo Ramone on 2009-04-22
I deleted my Ubuntu 8.10 and installed 9.04 RC...

From the live CD session the problem appear and the system ran in low graphics mode...

Now with the system installed, only run in low graphics mode...

Incredible.

I'll trying with other distro un live cd mode and test the graphics in order to determine if it's a hardware issue or it's an Ubuntu issue with 945 intel graphics.

---

### Post by go2dell on 2009-04-22
Be sure to update after tomorrow's final 9.04 release so you have the latest of everything.

Good luck with everything!  If you don't mind, please post back when you fix the problem so it can be of help to people who aren't as persistent as you.  Thanks for doing all the work!

This section of the release notes for the 9.04 RC may be helpful to you:

> Performance regressions on Intel graphics cards

Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (bug [252094]("https://bugs.launchpad.net/bugs/252094")). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

    *

      Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
    *

      Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

      /!\ In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
    *

      If none of the above helps, some users reported success with using an [older driver version]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4"). 

The rest of the release notes can be found [here]("http://http://www.ubuntu.com/getubuntu/releasenotes/904").

---

### Post by Marcelo Ramone on 2009-04-22
The logs:

Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 22 22:01:23 2009
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

(--) PCI:*(0@0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfde80000/524288, 0xd0000000/268435456, 0xfde40000/262144, I/O @ 0x0000cc00/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFDE80000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

lspci-vvnn:
```
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
    Subsystem: ASRock Incorporation Device [1849:2770]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
    Subsystem: ASRock Incorporation Device [1849:2772]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fde80000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at cc00 [size=8]
    Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at fde40000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: 00000000  Data: 0000
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: intelfb

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:3662]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fde38000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe000000-febfffff
    Prefetchable memory behind bridge: 00000000fa000000-00000000fcffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
            Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt+ MRL- PresDet+ CmdCplt+ HPIrq+ LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0300c  Data: 4159
    Capabilities: [90] Subsystem: ASRock Incorporation Device [1849:27d0]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: 00000000f9f00000-00000000f9ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
            Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet+ LinkState+
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0300c  Data: 4161
    Capabilities: [90] Subsystem: ASRock Incorporation Device [1849:27d2]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27c8]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at c400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27c9]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at c480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27ca]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27cb]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at c880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01) (prog-if 20)
    Subsystem: ASRock Incorporation Device [1849:27cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fde37c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) (prog-if 01)
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Subsystem: ASRock Incorporation Device [1849:244e]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27b8]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation Device [1849:27df]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASRock Incorporation Device [1849:27c0]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at c080 [size=8]
    Region 1: I/O ports at c000 [size=4]
    Region 2: I/O ports at bc00 [size=8]
    Region 3: I/O ports at b880 [size=4]
    Region 4: I/O ports at b800 [size=16]
    Capabilities: [70] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
    Subsystem: ASRock Incorporation Device [1849:27da]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 5
    Region 4: I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: ASRock Incorporation Device [1849:8136]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 2301
    Region 0: I/O ports at d800 [size=256]
    Region 2: Memory at f9fff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at f9fe0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at fdfe0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0300c  Data: 4181
    Capabilities: [70] Express (v2) Endpoint, MSI 01
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 4096 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
        Vector table: BAR=4 offset=00000000
        PBA: BAR=4 offset=00000800
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-01
    Kernel driver in use: r8169
    Kernel modules: r8169

```

xrandr-verbose:
```
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 (0x102) normal (normal) 0mm x 0mm
    Identifier: 0x101
    Timestamp:  20530
    Subpixel:   no subpixels
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
  1280x1024 (0x102)    0.0MHz *current
        h: width  1280 start    0 end    0 total 1280 skew    0 clock    0.0KHz
        v: height 1024 start    0 end    0 total 1024           clock    0.0Hz
  1024x768 (0x103)    0.0MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock    0.0KHz
        v: height  768 start    0 end    0 total  768           clock    0.0Hz
  800x600 (0x104)    0.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock    0.0KHz
        v: height  600 start    0 end    0 total  600           clock    0.0Hz
  640x480 (0x105)    0.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock    0.0KHz
        v: height  480 start    0 end    0 total  480           clock    0.0Hz
```

---

### Post by go2dell on 2009-04-23
Where did you get those logs?  Were they from Ubuntu or from another distro?

In the new Xorg log you posted, it's complaining that it can't find any memory available.  This is completely different from the error the first time.

If the logs are from your same Ubuntu install, the different error issue sounds a bit like the problem may be in hardware, since if it was software related the error should be identical both times.  Unfortunately, Ubuntu is set up to only log a minimum of old Xorg logs, so any that were created before your problem started have probably already been overwritten.

I do notice that xrandr is still saying the correct name for your video output is "default" but the X server is trying to use an output named "VGA."  How many outputs do you have on this board?

It looks like you're using an AsRock board, so it might be worth trying their hardware diagnostics (if any).  You could also check your battery, which I don't think should cause this problem, but I've seen weak batteries cause bizarre problems.

Since it's integrated video, you could even try reflashing your board BIOS again just to see if it helps; it worked for me on a board that had some bad capacitors that would occasionally zap tiny bits of the BIOS.  Flash with your current BIOS version, not with a new one; you don't want to introduce any new problems that might be caused by changing things at this point.

How much data do you have on the Ubuntu partition?  Would it be worth reinstalling with the final 9.04 release?

Good luck!

---

### Post by Marcelo Ramone on 2009-04-23
The logs are from freshly installed ubuntu 9.04 rc

The ubuntu partition is almost empty.

the board is an Asrock wolfade with intel 945 integrated graphics.

I do not know if the bios has upgraded.

---

### Post by Marcelo Ramone on 2009-04-24
With the final release installed the problem persists.

There is no hardware issues...

**I installed Debian Lenny and the Graphics are running 100%**

This is a serious Ubuntu problem with Intel Graphics cards.

Thanks for the help.

---

### Post by go2dell on 2009-04-27
I finally got around to installing Kubuntu 9.04 and am having no real problems with my Intel graphics, in any variant.  There's a problem with the kernel detecting corrupt memory (when the memory is fine) but that doesn't appear to affect performance any, and there's also one of the weird error messages in the Xorg log that I noticed in your log, but it appears that this has no effect on the system.

Debian Lenny is equivalent to Ubuntu 8.10.  To compare Debian to Ubuntu, you need to be running Squeeze or Sid, with Sid being probably a better match -- although it's a moving target so it's never a true complete match.  To stick with Ubuntu, you should probably try staying with 8.10, which is still supported.  Problems with a chipset as popular as Intel will likely be ironed out in short order.  These fixes will be pushed upstream to Debian so they also benefit from the Ubuntu community's experiences.

Have you filed a bug report in Launchpad to help the developers try to solve the problem?  The single greatest advantage to running a Linux distro is that bug reports are taken seriously and help to improve the experience for everyone.  If you can remember which update stopped your system from working, then the developers will have an idea of which update may have caused the error.

Thanks for taking the time to report here to the forums!

---

### Post by nval on 2009-04-28
I got a similar problem with my laptop today when I tried to use it with a projector. The X wouldn't go to 1280x800 again. I went into my bios and found out it was locked to VGA-only mode. I changed the boot mode to LCD and ubuntu could use the video card properly again.

---

### Post by go2dell on 2009-04-28
Do you think the BIOS had been set that way all the time, or was it something that magically "flipped" on its own?  This could be the OP's problem as well.

---

### Post by Marcelo Ramone on 2009-07-19
Hello,

I'm writing from Ubuntu 9.04 32 bits.

The system was installed and the video card was properly detected and graphics effects activated by default.

All perfect...

A few days ago, the low graphics mode began again and I fix activating the backports and proposed updates.

The system worked perfect for 1 week approximately, but today when I starter the system the problem appeared again.

I followed [***this guide***]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=low+graphics+mode") carefully, tried with safe and optimal configurations but doesn't works.

I reverted the changes now.

I reported the bug with errors collected with ubuntu-bug xserver-xorg-video-intel

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/401280](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/401280)

Ubuntu 9.04 is running in low graphics mode with my asrock motherboard with 945 Intel video card and I can't find a solution.

[IMG]http://img176.imageshack.us/img176/5059/pantallazopreferenciasd.png[/IMG]

***Refresh rate is 0 Hz and the video modes are wrong and 1440x900 (my resolution) is not present any more.***

---

