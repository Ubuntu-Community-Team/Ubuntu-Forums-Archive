---
title: "[SOLVED] Can't upgrade to 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by 24601oxy on 2008-12-31
I finally decided to upgrade to 8.10 from 8.04. 

I installed a few outstanding updates, then tried to use the update manager to upgrade. It ran for a little while, then displayed the following error message:

> Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 101M free space on disk '/boot'. Please free at least an additional 40.9M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I followed its instructions, then tried again. Same message. So I restarted the computer, and tried again. 

When I open the package manager, it tells me I have 1237 updates, and that I have to run a partial update. However, if I do that, it comes up with almost the same error message as before (differnt amounts of memory). If I try to hit "upgrade" on the top, it gives the same error as before. 


Can anyone help?

---

### Post by lemming465 on 2009-01-01
Can you show us the output of **df -m**?  You probably need about 2 GB of free space on /var to cache copies of packages.  If /boot is a separate partition, try removing obsolete kernels to free up additional space there.  You can do that from synaptic.

---

### Post by 24601oxy on 2009-01-02
Here's df -m

```
/dev/sda6               107876     23139     79257  23% /
varrun                    1009         1      1009   1% /var/run
varlock                   1009         0      1009   0% /var/lock
udev                      1009         1      1009   1% /dev
devshm                    1009         3      1007   1% /dev/shm
/dev/sda3                  193       127        58  69% /boot
tmpfs                     1009        39       971   4% /lib/modules/2.6.24-22-generic/volatile

```

---

### Post by lemming465 on 2009-01-02
Ok, with 79GB free on /, you have more than enough space for /var/cache/apt to stage the upgrades.  So the problem is the 127 MB of stuff in /boot.  
Fire up the synaptic package manager, search for *linux-image*, and do right-click -> remove for the kernels you aren't actually running.  **Be sure you leave the kernel you are running alone!**.  Then click apply, and wait a while.  

If you only have 1 kernel and 1 initrd in /boot, it should be using less than 15 MB there, and with >170 MB free, your upgrade will probably run OK.

---

### Post by 24601oxy on 2009-01-03
I think I must have ****** something up...

I removed all but the most recent kernal package, and then proceeded with the installing the upgrade. All that went fine. 

When it rebooted, however, the GUI wouldn't load, bringing me to a command line. It says:

```

Starting up ...
Loading, please wait ...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/5c6d4297-94d5-44f7-93e2-9ee9b92b98c0) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/5c6d4297-94d5-44f7-93e2-9ee9b92b98c0
kinit: No resume image, doing normal boot... 

Ubuntu 8.10 RivenDell tty1

RivenDell login: 

``` 

I'm guessing I deleted the wrong packages?

---

### Post by lemming465 on 2009-01-03
If you aren't getting a graphical login, and you wanted one, as most of us on non-servers do, then either a key desktop package got deleted too, or there is a problem with the drivers for your video chip.  8.10 did some radical surgery on the X support, so there have been a few more teething problems than normal.

You can do a character-mode / command line login at the login: prompt using your usual user account.  Then you can try:```
sudo -i
apt-get update
apt-get upgrade --fix-broken
apt-get install ubuntu-desktop
```
Let us know what the results are, and if you are still having problems, attach the contents of /etc/X11/xorg.conf and /var/log/Xorg.0.log to your next post.

---

### Post by 24601oxy on 2009-01-03
It says the most recent version of Ubuntu desktop is installed, and after rebooting, it still brings me to command interface. 

Stupid question, how do I find out the contents of those files?

---

### Post by lemming465 on 2009-01-03
If you want to read files at the command line, a typical program for scrolling them is "less".  Use the spacebar to go forward, "b" to go backward, "h" for help, and "q" to quit.  "man less" will tell you more about it.  Sorry, I should have mentioned that originally.

Next thing to try is **sudo dpkg-reconfigure xserver-xorg**.  We're still interested in the contents of /etc/X11/xorg.conf and /var/log/Xorg.0.log.  If you have a live CD which works, you could use that to upload them.

---

### Post by 24601oxy on 2009-01-03
OK, I got into the files from the command interface, but how would you access the old filesystem when booting from a live CD?

---

### Post by lemming465 on 2009-01-04
> how would you access the old filesystem when booting from a live CD?
With any luck, the live CD put icons for your hard disk partitions on the desktop and you can just double-click them. Failing that, you can do it by hand```
sudo mkdir /media/a6
sudo mount /dev/sda6 /media/a6
cd /media/a6/var/log
less Xorg.0.log
cd /media/a6/etc/X11
less xorg.conf
```

---

### Post by 24601oxy on 2009-01-04
No, no icons. Did it by hand. 

xorg.conf 
```
 # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Generic Keyboard"
#       Driver          "kbd"
#       Option          "XkbRules"      "xorg"
#       Option          "XkbModel"      "pc105"
#       Option          "XkbLayout"     "us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "Emulate3Buttons"       "true"
#EndSection


# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Synaptics Touchpad"
#       Driver          "synaptics"
#       Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
#       Option          "Protocol"              "auto-dev"
#       Option          "HorizEdgeScroll"       "0"
#EndSection
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Modes   "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
# commented out by update-manager, HAL is now used
#       InputDevice     "Synaptics Touchpad"
EndSection

``` 


Xorg.0.log

```
 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux RivenDell 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  4 13:21:45 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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

(--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfea00000/0, 0xe0000000/0, I/O @ 0x0000eff8/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfeb00000/0
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.5.0, module version = 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7616 kB
(II) VESA(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SEC  Model: 4457  Serial#: 0
(II) VESA(0): Year: 2007  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) VESA(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.2 MHz   Image Size:  303 x 190 mm
(II) VESA(0): h_active: 1440  h_sync: 1486  h_sync_end 1556 h_blank_end 1928 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 909  v_sync_end 918 v_blanking: 935 v_border: 0
(WW) VESA(0): Unknown vendor-specific block f
(II) VESA(0):  GR619^C141WD
(II) VESA(0):  ^Y)4:Tp<8A><B9>^B^A
(II) VESA(0): EDID (in hex):
(II) VESA(0):   00ffffffffffff004ca3574400000000
(II) VESA(0):   00110103801e13780a87f594574f8c27
(II) VESA(0):   27505400000001010101010101010101
(II) VESA(0):   010101010101442aa0e8518423302e46
(II) VESA(0):   99002fbe100000190000000f00000000
(II) VESA(0):   00000000000000000000000000fe0047
(II) VESA(0):   523631390331343157440a20000000fe
(II) VESA(0):   001929343a54708ab902010a20200009
(II) VESA(0): EDID vendor "SEC", prod id 17495
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1440x900"x0.0  108.20  1440 1486 1556 1928  900 909 918 935 -hsync -vsync (56.1 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 161 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 162 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 163 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 164 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 165 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 166 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 167 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 168 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 169 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16b (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16d (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16e (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 16f (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 170 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 171 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 13c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 14d (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 15c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 13a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 14b (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 15a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 107 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 11a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 11b (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 105 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 1024
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 8
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 1024
        BnkNumberOfImagePages: 8
        LinNumberOfImagePages: 8
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 117 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 2048
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 3
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 2048
        BnkNumberOfImagePages: 3
        LinNumberOfImagePages: 3
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 118 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 4096
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 4096
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
*Mode: 112 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 2560
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 5
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 2560
        BnkNumberOfImagePages: 5
        LinNumberOfImagePages: 5
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 114 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 1600
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 6
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 1600
        BnkNumberOfImagePages: 6
        LinNumberOfImagePages: 6
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 115 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 3200
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 3200
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 101 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 640
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 22
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 640
        BnkNumberOfImagePages: 22
        LinNumberOfImagePages: 22
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 103 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 832
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 13
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 832
        BnkNumberOfImagePages: 13
        LinNumberOfImagePages: 13
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 111 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0007bea
        BytesPerScanline: 1280
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 10
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xe0000000
        LinBytesPerScanLine: 1280
        BnkNumberOfImagePages: 10
        LinNumberOfImagePages: 10
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
(II) VESA(0): Total Memory: 119 64KB banks (7616kB)
(II) VESA(0): Configured Monitor: Using hsync value of 56.12 kHz
(II) VESA(0): Configured Monitor: Using vrefresh value of 60.02 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync value of 56.12 kHz
(II) VESA(0): Configured Monitor: Using vrefresh value of 60.02 Hz
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

``` 

Should I still try "sudo dkpg-reconfigure xserver-xorg"?

---

### Post by lemming465 on 2009-01-05
> Should I still try "sudo dkpg-reconfigure xserver-xorg"?

It's worth a try.  Unfortunately, I don't have any systems with intel video chips to test against.  Currently you are using the "vesa" driver > Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection
 rather than the intel one; unfortunately the vesa driver doesn't have a graphics mode that matches your screen> (EE) VESA(0): No valid modes


The intel driver seems to be having issues such as [bug 178451]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/178451"), [bug 120834]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834").

---

### Post by 24601oxy on 2009-01-05
Well, that seems to have worked.

 Thanks for everything!

---

### Post by Zofc on 2009-01-05
I had the same problem with upgrading from 8.04 to 8.10 . I recently made the transition from Windows to Ubuntu, so I was rather confused. I got a live CD from a friend, and took a long time to upgrade from 6 to 8.04. And when I upgraded to 8.10 I had the same GUI problem on boot up. I am running a nvidea graphics card (6800GT). 

Currently I'm not brave enough to try and upgrade, but if anybody has any ideas for me I would appreciate it. I would hate to have to clean sweep my pc. But, I do love having the most up-to-date system. Maybe I'll wait for Jackelope......

---

### Post by 24601oxy on 2009-01-05
It might have been easier for you to burn/order an 8.10 disk, rather than upgrading from 6. 

That being said, did you try going through **sudo dpkg-reconfigure xserver-xorg ** and just accepting all the defaults? That's what worked for me.

---

### Post by Zofc on 2009-01-05
Yeah probably would have been easier, but I admit I am an instant gratification kind of person. But I have an idea. I'll set up another partition (using the 6 Live CD) and try the solution that worked for you. If it works for me on the newer partition, I should be ok to do it on the other partition (the one I actively use). Lets just hope all goes well.....

---

### Post by lemming465 on 2009-01-06
What I usually recommend is trying a live desktop CD of a new version before deciding whether or not to upgrade.  If the live version sees all of your hardware and gets the video right, then upgrading will probably go OK.  Also, you have to figure your risk tolerance.  If you like being on the bleeding edge and don't mind doing some troubleshooting, you can upgrade prematurely, around the beta or RC1 versions.  If you are slightly risk averse, and just want stuff to mostly work, wait a month or two for the pioneers to shake out the problems first.  If you are really risk averse, run the long term release versions only, and wait for the .1 spins before you upgrade.

---

