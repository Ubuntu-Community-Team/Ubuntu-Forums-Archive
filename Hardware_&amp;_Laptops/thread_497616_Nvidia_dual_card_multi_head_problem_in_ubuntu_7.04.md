---
title: "Nvidia dual card multi head problem in ubuntu 7.04"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by damber on 2007-07-10
I've recently purchased 2 nvidia Geforce 8800 GTS cards (pci-e x16) sitting in an ASUS P5WDG2 WS Pro m/b with the expectation of outputting to 3 monitors for a multi-card,multi-head setup using either Xinerama or Twinview.

But... no joy yet.

The problem:
I can output video successfully to each monitor individually using the nv driver no problem, however I can't get it to output to all monitors at the same time, thus giving me the multi-monitor setup I want.
I get the feeling that the open source nv driver just doesn't support this at all... can someone please confirm this, so I don't waste my time on it if it's a no-go.

I have also tried the 'restricted drivers manager' proposed proprietary driver and downloaded the latest driver (100.14.11) from the nvidia website to see if these help things along.  I did manage to get a dual head working from one card, however it just doesn't seem to 'see' or accept the second card (I can selectively choose which card it will work with by changing the busid's, so I don't think it is the card).

Basically it says it cannot find the device section for the pci bus ID, despite it being present and seemingly correct in the xorg.conf... it also states on occasion that there is no such device or file, which seems to indicate that the /dev/nvidiactl char device is not available (despite the character device 'file' being present). 

in /dev I have seen nvidia0, nvidia1 and nvidiactl, but it sometimes shows just nvidia1 and nvidiactl 

lspci shows both cards, on PCI bus 6:0:0 and 7:0:0

xorg.conf:

```


... some other stuff...

Section "Device"
        Identifier      "Videocard1a"
        Driver          "nvidia"
        BusID           "PCI:7:0:0"
        Screen          0
EndSection
Section "Device"
        Identifier      "Videocard1b"
        Driver          "nvidia"
        BusID           "PCI:7:0:0"
        Screen          1
EndSection
Section "Device"
        Identifier      "Videocard0a"
        Driver          "nvidia"
        BusID           "PCI:6:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "Videocard0b"
        Driver          "nvidia"
        BusID           "PCI:6:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Option          "DPMS"
        # HorizSync     28-51
        # VertRefresh   43-60
EndSection
Section "Monitor"
        Identifier      "Monitor1"
        Option          "DPMS"
        # HorizSync     28-51
        # VertRefresh   43-60
EndSection
Section "Monitor"
        Identifier      "Monitor2"
        Option          "DPMS"
        # HorizSync     28-51
        # VertRefresh   43-60
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Videocard1a"
        Monitor         "Monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Videocard0a"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
Section "Screen"
        Identifier      "Screen2"
        Device          "Videocard1b"
        Monitor         "Monitor2"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Screen1" 0 0
        Screen          1 "Screen0" RightOf "Screen1"
        Screen          2 "Screen2" LeftOf "Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        Option          "Clone" "off"
        Option          "Twinview" "on"
        # Option         "Xinerama" "on"
EndSection

... some other stuff...

```

Does anyone have any ideas ?

Some thoughts:
1.  Does nv driver support multi-card-multi-head with Twinview or Xinerama ?
2.  Could my mobo be confusing the issue somehow ?
3.  Both are SLI cards with an SLI 'ready' m/b - is it trying to do something 'clever' and run this in sli mode ?
4.  Is my xorg.conf causing the problem ?
5.  Has anyone got this running ? or even just to output cloned screens to each monitor ?  


Thanks in advance

---

### Post by damber on 2007-07-10
OK, after reading through the /usr/share/doc/NVIDIA_GLX-1.0/README.txt (which is pretty thorough), I identified a possible problem with the driver not initialising the secondary card properly.  It advised (in Appendix B) to load the Int10 Xfree86 lib (Option "UseInt10Module" "on").

So, I added the option to each device and Load "Int10" into the Modules section.  Still no success, but the log states:

```

....
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Setting vga for screen 2.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseInt10Module" "on"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
**(WW) NVIDIA(0): Unable to load "xf86ExecX86int10".**
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "UseInt10Module" "on"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
**(WW) NVIDIA(1): Unable to load "xf86ExecX86int10"**.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "UseInt10Module" "on"
(**) NVIDIA(2): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
**(WW) NVIDIA(2): Unable to load "xf86ExecX86int10".**
.....

```


More detailed view of the log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
......
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen1" (0)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1a"
(**) |-->Screen "Screen0" (1)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0a"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Videocard1b"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
....
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
.....
(II) PCI: 06:00:0: chip 10de,0193 card 10de,0420 rev a2 class 03,00,00 hdr 00
(II) PCI: 07:00:0: chip 10de,0193 card 10de,0420 rev a2 class 03,00,00 hdr 00
......
(--) PCI: (6:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xe8000000/24, 0xb0000000/28, 0xe6000000/25, I/O @ 0xbc00/7, BIOS @ 0xe9de0000/17
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xee000000/24, 0xd0000000/28, 0xec000000/25, I/O @ 0xcc00/7, BIOS @ 0xefee0000/17
......
......
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
......
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
......
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Setting vga for screen 2.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseInt10Module" "on"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(0): Unable to load "xf86ExecX86int10".
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "UseInt10Module" "on"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(1): Unable to load "xf86ExecX86int10".
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "UseInt10Module" "on"
(**) NVIDIA(2): Enabling RENDER acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(2): Unable to load "xf86ExecX86int10".
(II) UnloadModule: "nvidia"
(II) UnloadModule: "int10"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(II) UnloadModule: "nvidia"
(II) UnloadModule: "int10"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(II) UnloadModule: "nvidia"
(II) UnloadModule: "int10"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Any ideas as to whether this is a versioning issue, or any way to resolve it ?

Thanks

---

### Post by damber on 2007-07-10
ok, found a link about the error (well quite a lot thanks to google):
[https://answers.launchpad.net/ubuntu/+question/4219](https://answers.launchpad.net/ubuntu/+question/4219)

I tried using nv instead of nvidia and come back to the error in the log file:

```

...etc...
(--) PCI: (6:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xe8000000/24, 0xb0000000/28, 0xe6000000/25, I/O @ 0xbc00/7, BIOS @ 0xe9de0000/17
(--) PCI:**[COLOR="DarkRed"]*[/COLOR]**(7:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xee000000/24, 0xd0000000/28, 0xec000000/25, I/O @ 0xcc00/7, BIOS @ 0xefee0000/17
.....etc....
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
....etc...
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
......etc....
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, **GeForce 8800 GTS**,
	Quadro FX 5600, Quadro FX 4600
(II) Primary Device is: **PCI 07:00:0**
(--) Chipset GeForce 8800 GTS found
(--) Chipset GeForce 8800 GTS found
(--) Chipset GeForce 8800 GTS found
Fatal server error:
**Requested Entity already in use!**

```


It seems to load one device, then stumble over the next - when using the nv driver, should I specify the device / screen / layout differently in my xorg.conf ?  Or is this a bug ?

---

### Post by damber on 2007-07-11
It seems that the nv driver doesn't support dual head configurations from various discussions found through google.  Anyone care to confirm/correct that assertion ?

Any ideas on how to get this working ?

---

### Post by I'd_rather_be_____'ing. on 2007-07-12
Well, for sure i'm not attempting the same things as you are -- monitor via VGA and TV via DVI off the same 8500gt -- however:
I've got a dual boot FF 7.04 / Vista going and the nvidia drivers were kind of a pain to get going in both OS's.  Now that they are, I've noticed that the linux drivers are less capaple than the vista ones. (surprise!)  

Specifically to my case, nvidia in vista can output to both connections with equal (reduced) resolution and cloned screens.  Nvidia in FF, however, can only put the screens side-by-side and never with equal resolution, even with separate Xscreens.  It also causes X to hang after switching resolutions.

Point being:  the hardware is probably very capable of it, but the drivers never had any MS $$'s thrown at them and need more time.

I also recall when installing nvidia 100.14.11 that it called for the removal of all traces of previous nv drivers, quoting bad references to shared libraries or references to old libraries that confuddle the new driver.  This might rule out your 'nv' approach altogether.

Please bear in mind that I don't know **** about any of this and I've never had more than one functioning video card in a pc at a time.  I'm just relating my experience here.

---

### Post by damber on 2007-07-12
Anyone have any other ideas I can try ?

---

### Post by damber on 2007-07-15
anyone..?

---

### Post by damber on 2007-07-16
OK, problem solved:

Thanks to the insights of 'bugspray' over at nvnews.net forums I have identified the issue:

**_The Issue_**
Running dual nvidia 8800 GTS cards with 320MB of mem each in a 32 bit linux system requires you to manually increase the vmalloc to something that will cope with the additional memory addressing requirements.  Pass the kernel parameter vmalloc=256M (or similar - moving up from 128 to no more than 512) either in grub to test or statically once it works - check the README.txt file in the nvidia driver package (/usr/share/doc/NVIDIA*/README.txt) - search for "vmalloc" and it will give you a detailed description of the issue and things to try.  You'll see vmalloc errors in your /var/log/messages file after boot up if it's not working.

**_The Resolution_**
I fixed my installation by simply installing the 64 bit version of ubuntu (I was wary previously because of the extra hassle you need to go through to get things working when someone doesn't offer a pre-packaged x86_64 option, though not insurmountable it's extra work - and then there is the 'unknown' aspect of potential quirks / bugs in the less used architecture package). 

Once installed, I then followed the process to remove the existing pre-packaged drivers (nv / nvidia-glx) - instructions can be found here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)   make sure you remove all traces to prevent any compatibility issues.

Then I exited the x session (ctrl+alt+f1) and ran the nvidia driver .run package from their website (v 100.14.11) and let it do it's thing.  

I then created my xorg.conf file like so:
```


Section "Module"
	Load		"nvidia"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

... input device stuff taken out for brevity....

Section "Device
	Identifier	"Videocard1-port1"
	Driver		"nvidia"
	Busid		"PCI:7:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen 		0
EndSection
Section "Device
	Identifier	"Videocard1-port2"
	Driver		"nvidia"
	Busid		"PCI:7:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen		1
EndSection
Section "Device
	Identifier	"Videocard2-port1"
	Driver		"nvidia"
	Busid		"PCI:6:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen		0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection
Section "Monitor"
	Identifier	"Monitor2"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection
Section "Monitor"
	Identifier	"Monitor3"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1-port1"
	Monitor		"Monitor1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes 	"1280x1024" 	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Screen2"
	Device		"Videocard1-port2"
	Monitor		"Monitor2"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Screen3"
	Device		"Videocard2-port1"
	Monitor		"Monitor3"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "Screen1" 0 0
	Screen 1 "Screen2" LeftOf "Screen1"
	Screen 2 "Screen3" RightOf "Screen1"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Option		"Clone" "off"
	Option		"Xinerama" "on"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I could then startx and bask in the glorious glow of 3 monitors working just how I want them. 
However....

The nvidia module isn't loaded permanently (i.e. added to the boot startup modules) so I then took steps to ensure it loads at boot up (otherwise it will crash and you will have to load the drivers manually before starting x again).  Now, I did try to use the /etc/modules file and the /etc/modprobe.d/ directory to achieve this, but I just couldn't get it to work... so out of impatience I simply added the following to the /etc/init.d/ scripts (a new script):

modprobe -i nvidia

Ideally I would like this to be loaded through the modules list, but it just didn't work for me - if anyone has any ideas, let me know.

Hopefully this will be useful to anyone wanting to use mutli-cards on a 32 bit system.

---

