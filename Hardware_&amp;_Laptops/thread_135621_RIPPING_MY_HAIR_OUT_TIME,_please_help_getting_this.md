---
title: "RIPPING MY HAIR OUT TIME, please help getting this ATI card working !"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by combat squirrel on 2006-02-24
Hello all, iv got many many posts in the video and sound section under the 'getting gflrx driver working'

Right iv been trying forever and a day to get it working on my 9100AGP card, it ALWAYS goes back to mesa, see the other thread for more detail:

[http://www.ubuntuforums.org/showthread.php?t=76116&page=79](http://www.ubuntuforums.org/showthread.php?t=76116&page=79)

Now, since then iv totally reinstalled ubuntu (so running the 386 kernal), ran the updates etc, put automatix on for firefox 1.5, thats all iv done.

Right now all im trying to do is get the darn thing working with ubuntus built in 3d driver, thats all i want ! 

I followed this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

ALL apparently went according to plan, but no tis not working, I got this out of Xorg.o.log:

[drm] register handle = 0xff5f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0b3a000 at 0xb7ac5000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x04000000


What does this mean and how do i fix it ? further up the log it states my chipset is supported and -should- run ! Please help, iv been posting a couple of days and no1 has been able to answer me :(

---

### Post by Teroedni on 2006-02-24
Hello
I have no clue how to fix the ati fglrx driver, but

Have you tried the Radeon driver instead

If you see at this site [http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)

Supported ATi hardware:
R200
    Radeon 8500, 9100, FireGL 8800/8700

your card seem to have fully accelerated driver;)

---

### Post by combat squirrel on 2006-02-24
iv had a look, how do i get this 'radeon' driver working ? is it in the system already ?

---

### Post by Teroedni on 2006-02-24
I believe a simple change from 
```
driver fglrx
```

 to

```
driver radeon
```

in your xorg.conf file will do it:)

---

### Post by combat squirrel on 2006-02-24
**Right possibly getting a little further now, when i type in fglrx info, it still says mesa, but since telling it to use 'radeon driver' it now doesnt say the above error in the xorg.0.log file, it says stuff whats written below:**

(II) Loading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.7
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9100 QM (AGP)" (ChipID = 0x514d)
(--) RADEON(0): Linear framebuffer at 0xe8000000
(--) RADEON(0): BIOS at 0xff5c0000
(--) RADEON(0): VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II)RADEON(0): AGP card detected
[B]
THEN A FEW MORE PAGES DOWN THE XORG.O.LOG FILE:[/B]

(II) RADEON(0): [drm] loaded kernel module for "radeon" driver
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0b3a000
(II) RADEON(0): [drm] mapped SAREA 0xe0b3a000 to 0xb3ca7000
(II) RADEON(0): [drm] framebuffer handle = 0xe8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xe0b3a000 at 0xb3ca7000
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
[B]
What do you thinks happening here? after 2 days were possibly getting closer to getting it working ! \\:D/  lol, i hope it can be solved anyways! :)[/B]

---

### Post by combat squirrel on 2006-02-24
Or maybe not then........ no linux guru's online ?, iv noticed this part myself:

(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.

How would I make sure agp is initialized before driver loading ? is that the problem why its not working ?

---

### Post by combat squirrel on 2006-02-25
:( i realise this has probably been bought up a million and 1 times, but iv been reading through ALL the previous work on this problem and have yet to find a solution, any any clues? all evidence above,lol

---

### Post by Teroedni on 2006-02-25
I think you are loadin a framebuffer device and that is bad

Could you post your xorg.conf file here ?

Thanks:)

---

### Post by combat squirrel on 2006-02-25
[B]Not a problem:
[/B]



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9100 AGP"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"NEC LCD1530V"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9100 AGP"
	Monitor		"NEC LCD1530V"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by combat squirrel on 2006-02-25
n e use 2 anyone^ ?

---

### Post by Teroedni on 2006-02-25
as i thought
the evil framebuffer:P


Section "Device"
Identifier "ATI Radeon 9100 AGP"
Driver "radeon"
BusID "PCI:1:0:0"
Option "UseFBDev" "true"<-------------remove this
EndSection

---

### Post by combat squirrel on 2006-02-26
Cheers for reply Teroedni, unfortuanatly didnt seem to work :(, still running mesa after removing line and rebooting :-?

---

### Post by Teroedni on 2006-02-26
huh what do you mean
you edited the file and removed the framebuffer right

You must reeboot also!!


so what problem are you left with?

---

### Post by combat squirrel on 2006-02-26
Yep I edited the xorg.conf file and removed Option "UseFBDev" "true" then rebooted my ubuntu machine and its still not hardware accelerated, I typed in fglrxinfo at the terminal and it says its using the mesa gl hardware acceleration:

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I was under the impression when it works it should say something along the lines of radeon 9100AGP etc. basically anything but the above

---

### Post by Teroedni on 2006-02-26
how do you know is not accelerated

Type glxinfo
what does it gives?

fglrxinfo only works if you use driver fglrx
but since you use radeon you should have 3d
glxinfo will tell you if you have

---

### Post by bluevoodoo1 on 2006-02-26
I have integrated ATI 9100 video and I posted on this [thread]("http://ubuntuforums.org/showthread.php?t=75378&page=32"), go to post 319  to see my question and read some of the replies. The replies say that the "9100 and 9100IGP are not supported for 3D" I'm just using the default driver "mesa" which seems to be the only option.

---

### Post by combat squirrel on 2006-02-26
**IM NOT USING INTEGRATED, Its an AGP board, cheers for the input though**

[B]To teroedni, its still not accelerated on the radeon driver, this is what glxinfo gave me:
[/B]
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

**Any clue's as to the next angle of attack ?, all info so far has been v much appreciated, great community,I wouldnt of got this far without anyones help :)**

Just a little not, this card used to be a 8500LE, I flashed it to 9100 in windows, would flashing the card back to an 8500LE be of much use ?

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=combat squirrel]**IM NOT USING INTEGRATED, Its an AGP board, cheers for the input though**[/QUOTE]

Oh, excuse me.

---

### Post by Teroedni on 2006-02-26
hmm
try to change driver back to fglrx the and see if it works now

It may have been the fbdev


Its kinda strange i thought radeon included it all....hmm

Ati cards surely are hard to get working

I think the radeon driver may require some extra options, it should be possible to get your card going.
But try Fglrx first in case it just work tm now;)

---

### Post by Teroedni on 2006-02-26
[QUOTE=bluevoodoo1]I have integrated ATI 9100 video and I posted on this [thread]("http://ubuntuforums.org/showthread.php?t=75378&page=32"), go to post 319  to see my question and read some of the replies. The replies say that the "9100 and 9100IGP are not supported for 3D" I'm just using the default driver "mesa" which seems to be the only option.[/QUOTE]

look here
[http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)


your card is listed as supported both 2d and 3d

Have you tried driver Radeon
It works for Combat squirrel
He/she only problem is that dri dont work....yet;)

---

### Post by combat squirrel on 2006-02-26
Just tried fglrx, no go, reverts back to mesa, here is the rest of the system specs:

1.7ghz 0.18 celeron s478
ASrock P4VM800 (brand new, bought for this linux machine)
Hercules Radeon 8500LE 64Mb, flashed about 2 years ago to a Gigabite 9100 bios
512meg corsair ram
10gig wd HD
15" NEC tft

Tis true !! getting this to work is SO difficult

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=Teroedni]look here
[http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)


your card is listed as supported both 2d and 3d

Have you tried driver Radeon
It works for Combat squirrel
He/she only problem is that dri dont work....yet;)[/QUOTE]


Hmmm.... but it also says "It contains full support for..... hardware 3D acceleration (except R300 and IGP series cards),"  (Maybe I'll try it out, I don't mean to hijack this thread, but thank you.)

---

### Post by combat squirrel on 2006-02-26
Just tried fglrx, again it went back to mesa :(

rest of spec is :

1.7ghz celeron s478
Asrock P4VM800 (brand new, bought for linux machine)
Herc Radeon 8500LE 64Mb, flashed to 9100 gigabite bios 2 yrs ago
512meg corsair ram
10gig HD
15"tft NEC monitor

Any more clues as to what to do now ? just posted this, but it seems to of lost the post, ah well

---

### Post by Teroedni on 2006-02-26
Yea Atidont seem to care too much


You flashed your card!!
That may be part of the problem
hmm
anyway we should be able to get it work:)
Atleast you got glx now so your only missing dri 
I try to search for more info:)

---

### Post by Teroedni on 2006-02-26
[QUOTE=bluevoodoo1]Hmmm.... but it also says "It contains full support for..... hardware 3D acceleration (except R300 and IGP series cards),"  (Maybe I'll try it out, I don't mean to hijack this thread, but thank you.)[/QUOTE]

yea but r300 is
R300
    Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1 (2D only)


while your chipset is rs300
RS300
    Radeon 9100 IGP


so yeah try it and good luck:)

---

### Post by combat squirrel on 2006-02-26
possibly that its flashed is  part of the problem, but I dont see how, they both use the R200 core, and the card works perfectly in windows, no worries bluevoodoo1 ! the more the merrier, maybe we can finally crack it  and get it working for the whole community

Cheer Teroedni, whats this dri ? is this whats causing it to always go back to mesa?

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=Teroedni]yea but r300 is
R300
    Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1 (2D only)


while your chipset is rs300
RS300
    Radeon 9100 IGP


so yeah try it and good luck:)[/QUOTE]

just checked my xorg.conf and it says... "ATI Technologies, Inc. Radeon 9100 A5 (R200 IGP)" I'll try it out, you said earlier all I have to do is replace "driver   ati" with "driver   radeon" correct"

[QUOTE=combat squirrel]no worries bluevoodoo1 ! the more the merrier, maybe we can finally crack it  and get it working for the whole community[/QUOTE]

:mrgreen:

---

### Post by Teroedni on 2006-02-26
hmm it is direct rendering thought i still can use my ati rage pro without dri;)


anyway
we need to dive further in
set driver as radeon again 
Reboot

then when your back write in terminal

sudo gedit /var/log/Xorg.0.log


copy the whole file. I want all of it;) .And paste it here.
I will then search true the whole file too see if i can spot the problem.

I be back later

---

### Post by combat squirrel on 2006-02-26
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [EMAIL="root@vernadsky.buil"]root@vernadsky.buil[/EMAIL]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 
Current Operating System: Linux ubuntulinx 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686
Build Date: 10 October 2005
    Before reporting problems, check [http://wiki.X.Org]("http://wiki.X.Org")
    to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu) #1 Mon Feb 13 12:13:15 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 26 16:22:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "NEC LCD1530V"
(**) |   |-->Device "ATI Radeon 9100 AGP"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.7
    X.Org XInput driver : 0.4
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0314 card 1849,0314 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1314 card 1849,1314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2314 card 1849,2314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3208 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4314 card 1849,4314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7314 card 1849,7314 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,3149 card 1849,3149 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1849,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1849,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1849,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1849,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1849,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1849,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1849,3227 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1849,9761 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1849,3065 rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,514d card 1458,4009 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:1), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus -1 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus -1 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:2), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus -1 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus -1 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus -1 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus -1 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:4), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus -1 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus -1 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:7), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus -1 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus -1 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000b000 - 0x0000bfff (0x1000) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xff500000 - 0xff5fffff (0x100000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe7f00000 - 0xf7efffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R200 QM [Radeon 9100] rev 0, Mem @ 0xe8000000/27, 0xff5f0000/16, I/O @ 0xb800/8, BIOS @ 0xff5c0000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [1] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [2] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [3] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [4] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [5] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [6] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [7] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [8] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [9] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [10] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [12] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [13] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [14] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [15] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [16] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [17] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [18] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [19] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [1] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [2] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [3] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [4] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [5] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [6] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [7] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [8] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [9] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [10] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [12] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [13] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [14] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [15] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [16] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [17] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [18] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [19] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [5] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [6] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [7] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [8] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [9] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [10] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [13] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [14] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [15] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [16] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [17] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [18] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [19] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [20] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [21] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [22] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [23] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [24] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [25] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [26] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 6.8.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 4.0.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 6.5.6
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330/340/350 (A4) 4137,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
    ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP),
    ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
    ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
    ATI FireGL RV360 AV (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
    ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
    ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE),
    ATI Radeon Mobility X600 (M24) 3150 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireGL D1100 (RV370) 5B65 (PCIE),
    ATI Radeon Mobility M300 (M22) 5460 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
    ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
    ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
    ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
    ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
    ATI RADEON X700 SE, ATI RADEON X700 SE,
    ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
    ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
    ATI FireGL V7100 (R423) UT (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
    ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
    ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
    ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
    ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
    ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
    ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
    ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(--) Chipset ATI Radeon 9100 QM (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [5] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [6] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [7] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [8] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [9] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [10] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [13] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [14] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [15] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [16] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [17] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [18] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [19] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [20] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [21] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [22] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [23] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [24] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [25] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [26] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) resource ranges after probing:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [5] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [6] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [7] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [8] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [9] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [10] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [11] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [12] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [13] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [17] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [18] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [19] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [20] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [21] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [22] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [23] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [24] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [25] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [26] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [27] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [28] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [29] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
    [30] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [31] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xff5f0000
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9100 QM (AGP)" (ChipID = 0x514d)
(--) RADEON(0): Linear framebuffer at 0xe8000000
(--) RADEON(0): BIOS at 0xff5c0000
(--) RADEON(0): VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: NEC  Model: 65a8  Serial#: 16843009
(II) RADEON(0): Year: 2000  Week: 51
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.140 blueY: 0.100   whiteX: 0.320 whiteY: 0.340
(II) RADEON(0): Supported VESA Video Modes:

---

### Post by combat squirrel on 2006-02-26
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz Image Size: 307 x 230 mm
(II) RADEON(0): h_active: 1024 h_sync: 1040 h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768 v_sync: 769 v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 60 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: NEC LCD1530V
(II) RADEON(0): Serial No: 0Z01238IB
(II) RADEON(0):
(II) RADEON(0): Primary:
Monitor -- CRT
Connector -- VGA
DAC Type -- Primary
TMDS Type -- NONE
DDC Type -- VGA_DDC
(II) RADEON(0): Secondary:
Monitor -- NONE
Connector -- DVI-D
DAC Type -- TVDAC/ExtDAC
TMDS Type -- Internal
DDC Type -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=25000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(WW) RADEON(0): config file hsync range 28-50kHz not within DDC hsync ranges.
(WW) RADEON(0): config file vrefresh range 43-75Hz not within DDC vrefresh ranges.
(II) RADEON(0): NEC LCD1530V: Using hsync range of 28.00-50.00 kHz
(II) RADEON(0): NEC LCD1530V: Using vrefresh range of 43.00-75.00 Hz
(II) RADEON(0): Clock range:  20.00 to 350.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(WW) (1280x768,NEC LCD1530V) mode clock 80.14MHz exceeds DDC maximum 80MHz
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(WW) (1280x800,NEC LCD1530V) mode clock 83.46MHz exceeds DDC maximum 80MHz
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (310, 230) mm
(--) RADEON(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b]
    [1] 0    0    0xe8000000 - 0xefffffff (0x8000000) MX[b]
    [2] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [7] -1    0    0xff6ffc00 - 0xff6ffcff (0x100) MX[b]
    [8] -1    0    0xff6ff800 - 0xff6ff8ff (0x100) MX[b]
    [9] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [10] -1    0    0xff5c0000 - 0xff5dffff (0x20000) MX[b](B)
    [11] -1    0    0xff5f0000 - 0xff5fffff (0x10000) MX[b](B)
    [12] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [13] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [14] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [15] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [16] 0    0    0x0000b800 - 0x0000b8ff (0x100) IX[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [20] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [21] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [22] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [23] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [24] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [25] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[b]
    [26] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [27] -1    0    0x0000c400 - 0x0000c40f (0x10) IX[b]
    [28] -1    0    0x0000c800 - 0x0000c803 (0x4) IX[b]
    [29] -1    0    0x0000cc00 - 0x0000cc07 (0x IX[b]
    [30] -1    0    0x0000d000 - 0x0000d003 (0x4) IX[b]
    [31] -1    0    0x0000d400 - 0x0000d407 (0x IX[b]
    [32] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[b](B)
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(==) RADEON(0): Write-combining range (0xe8000000,0x4000000)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] loaded kernel module for "radeon" driver
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0b3a000
(II) RADEON(0): [drm] mapped SAREA 0xe0b3a000 to 0xb3ca5000
(II) RADEON(0): [drm] framebuffer handle = 0xe8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xe0b3a000 at 0xb3ca5000
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

---

### Post by combat squirrel on 2006-02-26
I found this myself already Teroedni:

[B] (WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.

[/B]Is this the problem? How would I fix that ?

---

### Post by Teroedni on 2006-02-26
some radeon info 
[http://dri.freedesktop.org/wiki/ATIRadeon#head-465a5bcb4ff2a8459736c469bfac6c242de7f3c1](http://dri.freedesktop.org/wiki/ATIRadeon#head-465a5bcb4ff2a8459736c469bfac6c242de7f3c1)

---

### Post by Teroedni on 2006-02-26
Combat squirrel add this in your section device


Option "EnablePageFlip" "on"


here is a bug about agp module
[http://groups.google.no/group/linux.debian.bugs.dist/browse_thread/thread/ce6ff308f0613776/ce5b8544edc96033%23ce5b8544edc96033?sa=X&oi=groupsr&start=1&num=3](http://groups.google.no/group/linux.debian.bugs.dist/browse_thread/thread/ce6ff308f0613776/ce5b8544edc96033%23ce5b8544edc96033?sa=X&oi=groupsr&start=1&num=3)

---

### Post by combat squirrel on 2006-02-26
hi there, you mean like this in the xorg.conf file? :

Section "Device"
Identifier "ATI Radeon 9100 AGP"
Driver "radeon"
BusID "PCI:1:0:0"
Option "EnablePageFlip" "on"
EndSection

---

### Post by Teroedni on 2006-02-26
Yes:)

---

### Post by Teroedni on 2006-02-26
can you give me output off
cat /etc/modules.autoload.d/kernel-2.6




This problem is very common it seems .
Google gives out 10+of pages with problem relating to this
[http://www.google.no/search?q=(WW)+RADEON(0):+%5Bagp%5D+AGP+not+available%0D%0A(EE)+RADEON(0):+%5Bagp%5D+AGP+failed+to+initialize.+Disabling+the+DRI.%0D%0A(II)+RADEON(0):+%5Bagp%5D+You+may+want+to+make+sure+the+agpgart+kernel+module%0D%0Ais+loaded+before+the+radeon+kernel+module.&hl=nn&lr=lang_en&start=20&sa=N](http://www.google.no/search?q=(WW)+RADEON(0):+%5Bagp%5D+AGP+not+available%0D%0A(EE)+RADEON(0):+%5Bagp%5D+AGP+failed+to+initialize.+Disabling+the+DRI.%0D%0A(II)+RADEON(0):+%5Bagp%5D+You+may+want+to+make+sure+the+agpgart+kernel+module%0D%0Ais+loaded+before+the+radeon+kernel+module.&hl=nn&lr=lang_en&start=20&sa=N)

---

### Post by combat squirrel on 2006-02-26
**Again didnt work :(**

glxinfo gives:

 glfinfo
bash: glfinfo: command not found
ben@ubuntulinx:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess ...............


hmmmmm why is it not working still ?

---

### Post by combat squirrel on 2006-02-26
How do I give you the output of cat /etc/modules.autoload.d/kernel-2.6 teroedni ?

---

### Post by Teroedni on 2006-02-26
you paste the command in terminal and press enter.
That will tell if agpmodule is loaded before radeon

---

### Post by combat squirrel on 2006-02-26
I only get this im afraid:

cat /etc/modules.autoload.d/kernel-2.6: No such file or directory

just going out for some food, back shortly, will try whatever you suggest next ! :) lol

---

### Post by Teroedni on 2006-02-26
okey it seems to be
cat /etc/modules
in ubuntu
sorry for that

---

### Post by combat squirrel on 2006-02-26
Hey Teroedni, back, let me know what u think the next best thing do it

---

### Post by Teroedni on 2006-02-26
what does ```
cat /etc/modules
``` give

---

### Post by combat squirrel on 2006-02-26
@ubuntulinx:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse


**The above is all it gives**

---

### Post by combat squirrel on 2006-02-26
Also got this info if it helps:

cat /var/log/Xorg.0.log | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.

 cat /var/log/Xorg.0.log | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
ben@ubuntulinx:~$ cat /var/log/Xorg.0.log | grep "(WW)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): config file hsync range 28-50kHz not within DDC hsync ranges.
(WW) RADEON(0): config file vrefresh range 43-75Hz not within DDC vrefresh ranges.
(WW) (1280x768,NEC LCD1530V) mode clock 80.14MHz exceeds DDC maximum 80MHz
(WW) (1280x800,NEC LCD1530V) mode clock 83.46MHz exceeds DDC maximum 80MHz
(WW) RADEON(0): [agp] AGP not available

---

### Post by Teroedni on 2006-02-26
add 

agpgart

as the first one
and restart afterwards

---

### Post by combat squirrel on 2006-02-26
how ya mean ? add agpgart to somewhere in this?:

Section "Device"
Identifier "ATI Radeon 9100 AGP"
Driver "radeon"
BusID "PCI:1:0:0"
Option "EnablePageFlip" "on"
EndSection

Sorry to be such a noob !! :D:)

or ya mean here ( i think u mean here! lol):

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

---

### Post by Teroedni on 2006-02-26
yes the last one:)

---

### Post by combat squirrel on 2006-02-26
ok i did, and rebooted, still not working, in mesa mode still, i take it were trying to make it work via the agpgart, i read on the other forums possibly using internal agpgart driver instead of external ? (i have not much idea what this means ! lol)

---

### Post by Teroedni on 2006-02-26
me neither but it is worth a try
im sorry that i begin to run out of ideas
could you join ubuntuforum irc channel on irc.freenode.net?

---

### Post by combat squirrel on 2006-02-26
ahhh but i have no idea how to give it a try ! lol

so great ubuntu god, lol :D tell me what can i do next to try and get it working ?

---

### Post by Teroedni on 2006-02-26
in device


Option "UseInternalAGPGART" "yes"

---

### Post by combat squirrel on 2006-02-26
tried, doesnt work, tried both with radeon and fglrx driver, next thing ? :S:D lol

---

### Post by Teroedni on 2006-02-26
could you join the ubuntu irc channel #ubuntuforums  on irc.freenode.net please?

---

### Post by rafaelwall on 2006-04-24
Did you fixed this problem?
I am getting this same problem too!

---

### Post by NoiseBOX on 2007-12-03
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm running Feisty, on an intel chipset with the radeon driver. I was having a similar problem where Xorg was reporting. 

"(WW) RADEON(0): [agp] AGP not available"

I tested this by dropping to terminal and properly loading each of the required modules in order. first comes your chipset agp (such as sis_agp or intel_agp), then load agpgart, then drm, and then radeon. Still no go.
I searched around on the Ubuntu Launchpad bug tracker. And came across the entry linked above. To sum it up this is a strange bug that isn't a problem with the agp stuffs, but rather to  a few edac modules that are preventing chipset_agp from linking to drm properly. the solution for my was to edit my blacklist appropriately

/etc/modprobe.d/blacklist :
blacklist i82875p_edac
blacklist edac_mc

Then a quick reboot into glorious direct rendered heaven. It seems a few other people have found different modules they needed to blacklist in order to bring the agp modules back in line so if this doesn't work for you read through the buglist. Please let us know if this is a solution for you, and if you're so inclined to post onto the launchpad to help the developers. Thanks

---

