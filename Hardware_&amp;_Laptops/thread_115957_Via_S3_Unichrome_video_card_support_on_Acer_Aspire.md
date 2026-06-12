---
title: "Via S3 Unichrome video card support on Acer Aspire 1362LC"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by optotron on 2006-01-11
Is there any working video card drivers for my laptop? i have some trouble making it work properly; neither of the drivers ive found on via's homepage has worked properly.

It works with the vesa driver, but i'd like to use the video card's full potential, is there currently any working drivers?

---

### Post by Greg2 on 2006-01-11
I don’t have your video card so I can’t help you with instructions, but I can show you the location of the drivers others with your card are using. Here:
[http://www.openchrome.org/snapshots/ubuntu/](http://www.openchrome.org/snapshots/ubuntu/)

Please do a search for Unichrome in the forum for more info.

---

### Post by optotron on 2006-01-12
[QUOTE=Greg2]I don’t have your video card so I can’t help you with instructions, but I can show you the location of the drivers others with your card are using. Here:
[http://www.openchrome.org/snapshots/ubuntu/](http://www.openchrome.org/snapshots/ubuntu/)

Please do a search for Unichrome in the forum for more info.[/QUOTE]



thanks for the link and the help!

---

### Post by JDoza on 2006-01-13
I have an Averatec 3270-EH1 which has the same video card. The instructions on that page are either vauge or My newb status doesn't allow me to understand them. Have you had any luck?

---

### Post by optotron on 2006-01-13
[QUOTE=JDoza]I have an Averatec 3270-EH1 which has the same video card. The instructions on that page are either vauge or My newb status doesn't allow me to understand them. Have you had any luck?[/QUOTE]

Not so far, but i'll let you know once I do!

---

### Post by optotron on 2006-01-14
[QUOTE=Greg2]I don’t have your video card so I can’t help you with instructions, but I can show you the location of the drivers others with your card are using. Here:
[http://www.openchrome.org/snapshots/ubuntu/](http://www.openchrome.org/snapshots/ubuntu/)

Please do a search for Unichrome in the forum for more info.[/QUOTE]

i installd all thos packages and Ifollowed the instructions found on page, but I hav no clue what to do next...

---

### Post by Greg2 on 2006-01-14
[QUOTE=optotron]i installd all thos packages and Ifollowed the instructions found on page, but I hav no clue what to do next...[/QUOTE]
I have an ATI card so I’m not even sure what the /etc/X11/XvMCConfig file is, as I don’t have one? That said, I will still try to help you since no one with your card has helped.

So what does /etc/X11/xorg.conf say in the device section? Driver “?”

---

### Post by optotron on 2006-01-14
Hi greg! I'm glad that you try to help. :D :D :D :D 
[QUOTE=Greg2]I have an ATI card so I’m not even sure what the /etc/X11/XvMCConfig file is, as I don’t have one? That said, I will still try to help you since no one with your card has helped.

So what does /etc/X11/xorg.conf say in the device section? Driver “?”[/QUOTE]

I didn't have the /etc/X11/XvMCConfig neither. I have never heard of it before.

this is my current setting;

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"


I have tried to change driver by editing the file, but without success. Thats because i'm not sure how to do it properly, and I have no idea what the "BusID" is...

---

### Post by Greg2 on 2006-01-14
[QUOTE=optotron]I have tried to change driver by editing the file, but without success. Thats because i'm not sure how to do it properly, and I have no idea what the "BusID" is...[/QUOTE]
First make a backup copy of your xorg.conf file.

To edit do:```
sudo gedit /etc/X11/xorg.conf
``` if the file is busy you may have to reboot in the recovery mode and use:```
sudo nano /etc/X11/xorg.conf
``` if you have never used nano or pico please read the man pages.

I &#8216;believe&#8217; your BusID is correct so just edit the driver.

Then restart the gui with:```
sudo /etc/init.d/gdm restart
```
Edit: I just noticed your using Kubuntu, so to restart the gui do:```
sudo /etc/init.d/kdm restart
```
I can&#8217;t seem to connect to openchrome.org for over an hour now for more info? It keeps timing out.

I have found working drivers but they are compiled for AMD 64... I believe you have a Sempron?

Sorry, I&#8217;ll try later to find more info.

---

### Post by Greg2 on 2006-01-14
I still have no access to openchrome.org but I have found some more info.

It ‘sounds’ to me like the new Dapper snapshots have this working with the openchrome drivers out of the box? So you could try that?

I’ve also read that some users are having success with:
[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

The via snapshot packages are at the bottom of the page here:
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

I have d/l one of this and checked it out. It comes with an install.sh that appears to be pretty simple to use. You may want to give it a try? Please read the wiki first!

I’m afraid that’s all I can help you with without access to a via chipset to test.

Good luck:smile:

---

### Post by optotron on 2006-01-14
[QUOTE=Greg2]
I’m afraid that’s all I can help you with without access to a via chipset to test.

Good luck:smile:[/QUOTE]

Thats a whole lot of help. Thanks a lot i'll give it a new try =D

cheers!

---

### Post by JDoza on 2006-01-15
Newb status may have stumped me, but the script failed....


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


Contents of ,log file....
Makefile:166: *** Cannot find a kernel config file.  Stop.


ideas???

---

### Post by optotron on 2006-01-15
[QUOTE=JDoza]Newb status may have stumped me, but the script failed....


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


Contents of ,log file....
Makefile:166: *** Cannot find a kernel config file.  Stop.


ideas???[/QUOTE]

You've come as far as i have. I'm trying to figure this out. 
I'll let you know once i've figured this out!

---

### Post by JDoza on 2006-01-15
I think it failed because it asks for location or XFree86 stuff. Xorg is currently in my box.

Maybe we could get some body smart to rewrite the script for xorg....any takers?

---

### Post by Greg2 on 2006-01-15
[QUOTE=JDoza]
Compiling...
ERROR: Kernel modules did not compile[/QUOTE]
Do you have the headers and tools:
```
sudo apt-get install linux-headers-$(uname -r)
```

```
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
```

Then try your script?

---

### Post by JDoza on 2006-01-15
It ‘sounds’ to me like the new Dapper snapshots have this working with the openchrome drivers out of the box? So you could try that?

I'm running Dapper Flight 2 right now kernel 2.6.15-12-k7
and I am running the vesa driver, it's the only way to make my screen work.


[QUOTE=Greg2]Do you have the headers and tools:
```
sudo apt-get install linux-headers-$(uname -r)
```

```
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
```

Then try your script?[/QUOTE]

Thanks for your help....compiled with zero errors. I changed the setting in xorg.conf, rebooted, and nothing. Back to square one.

Thanks for all the help so far...

---

### Post by Greg2 on 2006-01-16
[QUOTE=JDoza]
compiled with zero errors. I changed the setting in xorg.conf, rebooted, and nothing.[/QUOTE]
Changed the setting from what to what?

Did you d/l the ‘common’ snapshot with your ‘via’ snapshot?

From the dri.wiki:> 
Nightly snapshots of the DRI drivers for Linux are available from  [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/). You need to download and install the correct snapshot for your graphics card and a "common" snapshot in order to get all new DRI features.

---

### Post by optotron on 2006-01-16
It seems to me as if you've at least come further than I have


[QUOTE=JDoza]Thanks for your help....compiled with zero errors. I changed the setting in xorg.conf, rebooted, and nothing. Back to square one.

Thanks for all the help so far...[/QUOTE]

I get this message instead :confused: 

```
==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

doddo@puh:~/mozilla-downloads/via-20060116-linux.i386$

```
although i do this
```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

```
I'll try this wiki that greg posted a link to, and see if I can figure this out

to be continued :smile:

---

### Post by optotron on 2006-01-17
this may be of some help, at least if you've manage to run the scripts correctly

[http://www.ubuntulinux.se/node/164](http://www.ubuntulinux.se/node/164)

---

### Post by kubuntu2k6 on 2006-01-28
I have the same laptop and been running vesa for so long it's rediculous. :( 
If you get it working pls post your solution. I will try to look into this also, but all my attempts so far has failed.

---

### Post by JDoza on 2006-01-28
Ok...not sure if it is a fluke but this is what I did. I placed the  2 Options of EnableAGPDMA and the disableIRQ like what was listed in the script that Optotron linked to, changed the driver to "via" as well in my xorg.conf. I restarted X and it worked. DRI is enabled.

I am currently using Dapper Flight 3 with the kernel 2.6.15-14-k7. 

I am going to restart my laptop and see if it was just a fluke...

will post result of the restart.\\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by JDoza on 2006-01-28
The reboot went well....Here is the output of my "glxinfo"

name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
display: :0  screen: 0
[COLOR="Red"]direct rendering: Yes[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_MESA_render_texture
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
[COLOR="Red"]OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20050526
OpenGL version string: 1.2 Mesa 6.4.1[/COLOR]
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow

Here is my xorg.conf...

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
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	" VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter "
	[COLOR="Red"]Driver		"via"[/COLOR]
	BusID		"PCI:1:0:0"
	[COLOR="Red"]Option          "DisableIRQ"
	Option          "EnableAGPDMA"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"12.1 inch High Resolution XGA LCD"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		" VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter "
	Monitor		"12.1 inch High Resolution XGA LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

### Post by Greg2 on 2006-01-28
[QUOTE=JDoza]Ok...not sure if it is a fluke but this is what I did. I placed the  2 Options of EnableAGPDMA and the disableIRQ like what was listed in the script that Optotron linked to, changed the driver to "via" as well in my xorg.conf. I restarted X and it worked. DRI is enabled.[/QUOTE]
I’m glad to see you have it working! Now maybe optotron and some others that are having the same problem will try again with this method?

Out of curiosity how well does the DRI work compared to the Windows graphics your laptop came with? I don’t need a benchmark, I just want to know if it looks good.:)

---

### Post by JDoza on 2006-01-29
I haven't done any testing. My wallpaper looks ALOT better. I have a pic of a Big Dog Motorcycle as my Wallpaper and it has better look to it like my Windows desktop.

Sorry....I still dual-boot.:cry:

---

### Post by kubuntu2k6 on 2006-01-29
[QUOTE=JDoza]Ok...not sure if it is a fluke but this is what I did. I placed the  2 Options of EnableAGPDMA and the disableIRQ like what was listed in the script that Optotron linked to, changed the driver to "via" as well in my xorg.conf. I restarted X and it worked. DRI is enabled.

I am currently using Dapper Flight 3 with the kernel 2.6.15-14-k7. 

I am going to restart my laptop and see if it was just a fluke...

will post result of the restart.\\:D/ \\:D/ \\:D/ \\:D/ \\:D/[/QUOTE]

Sorry for being bit of a n00b here... did you make and copy kernel drivers etc as in the script, or is it working out of the box with the Dapper kernel?

Edit: Upgraded to Dapper and modified my xorg.conf as suggested. All I get is a black screen. [Xorg.0.log]("http://hem.bredband.net/jonwik/Xorg.0.log")

---

### Post by JDoza on 2006-01-29
I did a clean install of Dapper Flight 3, all updates and the 2.6.15-14-k7 kernel. Check a few posts back for the output of my "lspci". Your MOBO and video card may be different than mine. All I did was add those 2 options, change to the via driver in my xorg.conf.

I hope it helps you.

---

### Post by kubuntu2k6 on 2006-01-30
Thanks for your input.

Wiped my upgraded breezy/dapper mess, and started over with a fresh dapper f3 install, updated everything and installed the 2.6.15-14 kernels (2.6.15-14-k7).

Compared your lspci output in the other thread and found it to be almost identical to mine (good sign).

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
```
One difference though is I'm using a Mobile AMD Sempron 2800+ 32 bit processor.

Didn't get the results I was hoping for. Just the black screen of death. 
Maybe optotron and others in this forum will have better success getting this working. Staying tuned. :cool:

---

### Post by JDoza on 2006-01-30
I have the same processor as you, Sempron 2800+. That is what the case says...

Maybe your LCD needs  horiz and vert rates...  just a thought.

With last nights updates, my wireless card doesn't work now....Go Figure.

---

### Post by kubuntu2k6 on 2006-01-31
Oh OK.. so basically it's the same laptop. :) 

Never used the wireless stuff but guess thats life when running testing.

You may be right about LCD settings, tried different horiz/vert rates (even plugged in a monitor) but havn't got it to work yet. Btw. what's your Xorg version? 

Would like to know optotron's (and/or others) results as he is using an Acer Aspire 1362LC also.

For the record, below is the only output stored in Xorg.0.log before I hit the power button (guess it doesn't say anything). 

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux localhost 2.6.15-14-k7 #1 SMP PREEMPT Wed Jan 25 16:23:02 UTC 2006 i686
Build Date: 21 December 2005
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 31 08:21:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
```

---

### Post by JDoza on 2006-01-31
My Xorg.0.log is too large to attach to this message. It says it exceeds the character length for the message... Ideas on a place to host it?  Did you apply all the updates that Dapper wanted to install before you tried to get DRI working. I ask because I remember a few xorg updates thay may contain the VIA driver that you need to get it working.

---

### Post by JDoza on 2006-01-31
Here is what a dude did to get his to work from another thread...

[http://www.ubuntuforums.org/showthread.php?t=81743&page=4](http://www.ubuntuforums.org/showthread.php?t=81743&page=4)

---

### Post by optotron on 2006-02-01
[QUOTE=kubuntu2k6]
Didn't get the results I was hoping for. Just the black screen of death. 
Maybe optotron and others in this forum will have better success getting this working. Staying tuned. :cool:[/QUOTE]

I havent even been able to find
  # file #1: via-20050608-linux.i386.tar.bz2
so it is not working properly for me.. Yet
:???:

---

### Post by kubuntu2k6 on 2006-02-01
I don't even have a via driver in /usr/X11R6/lib/modules/drivers/. I believe there should be one. :confused:

Edit: 
Drivers seem to have moved to /usr/lib/xorg/modules/drivers.

Anyway, followed this thread [http://ubuntuforums.org/showthread.php?t=76037](http://ubuntuforums.org/showthread.php?t=76037) downloading and replacing the via_drv.o file. But it just crashes my X. [(Xorg.0.log)]("http://hem.bredband.net/jonwik/Xorg.0.log_0202")

optotron, I don't know about the via-20050608-linux.i386.tar.bz2 file. I havn't followed any kernel-module compiling guide. 

JDoza, thanks for the link, unfortunately the method didn't work for me.

---

### Post by optotron on 2006-02-05
[QUOTE=optotron]I havent even been able to find
  # file #1: via-20050608-linux.i386.tar.bz2
so it is not working properly for me.. Yet
:???:[/QUOTE]

did any of the other snapshots work instead?

I followed that thread too, but i also got the black screen of death

:confused: :confused: :confused:

---

### Post by dcstar on 2006-02-06
I recently put together this UNICHROME Direct Rendering HOWTO (for 386 based Breezy Ubuntu), someone may be able to try it and let me know if it actually works:

[http://ubuntuforums.org/showthread.php?t=124604](http://ubuntuforums.org/showthread.php?t=124604)

---

### Post by optotron on 2006-02-06
[QUOTE=dcstar]I recently put together this UNICHROME Direct Rendering HOWTO (for 386 based Breezy Ubuntu), someone may be able to try it and let me know if it actually works:

[http://ubuntuforums.org/showthread.php?t=124604](http://ubuntuforums.org/showthread.php?t=124604)[/QUOTE]

I followed the instructions and I ran the script. in the 386 kernel, 
got the following error message:
```
Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
```

I think I have all the headers and stuff. Anyway I tried running the script with the K7 kernel image instead. I ran the script with 0 errors, and altered the xorg.conf according to the instructions in the script. 

when I then tried to start x it couldnt. here's the log
```
 Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "Generic Video Card" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
```

:confused: :confused:

---

### Post by optotron on 2006-02-06
mjn

---

### Post by Greg2 on 2006-02-06
[QUOTE=optotron]mjn[/QUOTE]
Is this good of bad?:???:

---

### Post by optotron on 2006-02-06
[QUOTE=Greg2]Is this good of bad?:???:[/QUOTE]

 :-? I finally tought i booted with the via driver, but i didnt 

so bad i guess ;)

---

### Post by dcstar on 2006-02-06
[QUOTE=optotron]I.....
when I then tried to start x it couldnt. here's the log
```
 Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "Generic Video Card" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
```

:confused: :confused:[/QUOTE]
Do:

sudo dpkg-reconfigure xserver-xorg

and select the via driver.

If this doesn't start up when you reboot, you may have to restart in Recovery mode and rename your /etc/X11/xorg.conf file to the previous version.

---

### Post by optotron on 2006-02-06
[QUOTE=dcstar]Do:

sudo dpkg-reconfigure xserver-xorg

and select the via driver.

If this doesn't start up when you reboot, you may have to restart in Recovery mode and rename your /etc/X11/xorg.conf file to the previous version.[/QUOTE]

Yeah I've tried that without success. I also noted that it does not add the "enableAGPDMA" option by default nor does it autodetect the driver

The computer freezes when i set the xorg to "via"

Ive also tried booting into different kernel images. so far i havent managed to properly install the driver...

but i'll keep trying :p

---

### Post by dracflamloc on 2006-02-08
I'm not having any luck at all =(

It wont start X. I have a gateway mx3215 laptop with a unichrome pro.

---

### Post by dcstar on 2006-02-08
[QUOTE=dracflamloc]I'm not having any luck at all =(

It wont start X. I have a gateway mx3215 laptop with a unichrome pro.[/QUOTE]
On my system - KM400 - it had detected (and used) the VIA driver before I got the direct rendering going, perhaps this needs to be working before that stage is tried.

Sorry to see people still having problems!

---

### Post by dracflamloc on 2006-02-09
Oh ok... yea it wont even start X with the via driver. =(

I'm wondering if maybe the flavor of unipro I have in this laptop isnt the same as other unipro's and as such the via driver doesnt think its a unipro?

---

### Post by sandcalc on 2006-02-09
Well I do have a unichrome pro as well (packard bell e6 307 laptop). Specfically a k8n800. I'm pretty much at the same point, i've been able to get the script to finish with no errors (after switching to the 686 image). But if I change the xorg.conf script it still crashes as per usual. I've tried every driver I can, but if i change from 'vesa' to 'via' it always crashes.

---

### Post by dcstar on 2006-02-09
[QUOTE=dracflamloc]Oh ok... yea it wont even start X with the via driver. =(

I'm wondering if maybe the flavor of unipro I have in this laptop isnt the same as other unipro's and as such the via driver doesnt think its a unipro?[/QUOTE]
You could be right, you might have to wait for Dapper to come out to see if it detected ok in that release.

---

### Post by dracflamloc on 2006-02-13
From what I've been told by the developer of the via driver, the chipset I have is not supported and probably wont be until someone can provide it to the developers to test.

My card's device id is 3344 so if you've got that type of card you're out of lluck for now it seems. 

This kind of stinks, I was hoping that getting a card other than ati/nvidia would mean its easier to get to work in linux, not harder! Oh well...Vesa works fairly well for the time being.

---

### Post by optotron on 2006-02-14
i tried running dapper, but it did not autodetect the driver. At least not for me. 

I too guess the vesa driver will have to do, at least for the time being.

---

### Post by dcstar on 2006-02-18
After the latest kernel upgrade to **2.6.12-10.28** my Via Direct Rendering stopped working! (with lots of "disagrees about version of symbol" errors in my dmesg output).

I found I had to now remove the Via module I previously created by with:

sudo modprobe -r via

And after a reboot all was well again!

**It looks like the Via DRM code is now included in this kernel** - people with Via Unichrome hardware may now want to check if Direct Rendering works.

---

### Post by shapht on 2006-02-18
Really? When I upgraded my kernel I just recompiled drm from the latest snapshot...oh well whatever works.

---

### Post by optotron on 2006-02-19
Hey! I tried running the old script that i found and the one that worked for JDoza (this one [http://www.ubuntulinux.se/node/164](http://www.ubuntulinux.se/node/164)) with the new k7 kernel 2.6.12-10.28. I then got the following error message when starting x 
```
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

I altered the lines in xorg.conf as instructed in the script.

---

### Post by dracflamloc on 2006-02-20
Has anyone tried flight4? I'll be trying it later. Though I'm pretty skeptical about it working since my device id is supposedly not supported at all

---

### Post by optotron on 2006-02-20
[QUOTE=dracflamloc]My card's device id is 3344 so if you've got that type of card you're out of lluck for now it seems. [/QUOTE]

how do you determine what device id your card has?

---

### Post by dracflamloc on 2006-02-20
Look at the log your X server spits out. In there you'll see a list of PCI devices. Look for the 3344 ;)

---

### Post by optotron on 2006-02-21
[QUOTE=dracflamloc]Look at the log your X server spits out. In there you'll see a list of PCI devices. Look for the 3344 ;)[/QUOTE]

cheers! :mrgreen:

---

### Post by dracflamloc on 2006-02-21
Yea welcome to the club!

I'm gonna try FLight4 in a few minutes, though I'm not too hopeful

[edit] no luck with flight4. guess we just need to wait and hope

---

### Post by optotron on 2006-02-21
Here's part of my log from last time i tried starting x with the via driver.
```

(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400
(II) Primary Device is: PCI 01:00:0
(--) Chipset K8M800 found

``` It seems to me as if I have the K8M900 Chipset whatever that means. I searched for "3344" anywhere in the PCI scan but i did not find it.

Here's when it loads the part where the preferences are
```

(II) VIA(0): VIAGetRec
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(**) VIA(0): Option "DisableIRQ"
(**) VIA(0): Option "EnableAGPDMA"
(==) VIA(0): Using HW cursor
(**) VIA(0): Option: DisableIRQ - DRI IRQ Disabled
(**) VIA(0): Option: EnableAGPDMA - Enabling AGP DMA

```

and finally the error message that tells me it cant boot X
```
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```
I might be doing something wrong, I just cant figure out what..:-k

---

### Post by Tomy on 2006-02-21
The K8M800 is a UnichromePro and is better supported when you get to dapper and the 2.6.15-xx kernels. I installed dapperFlight4 the other day and it did not detect the K8M800 at install and I had to create xorg.conf manually. 3d acceleration (dri) did work but the via driver was not-so-great. 

I "borrowed" openchrome_drv.so from Linspire 5.1 beta (Linspire compiles both the openchrome via driver and the xorg via driver). This driver worked fairly well but planetpenguin racer still freezes the system solid. I installed tuxracer from the old hoary repositories and it worked most of the time only freezing towards the end of the race.

UnichromePro support is getting better -- I hope the patches from openchrome.org make it into the xorg via driver before dapper is released.

Tomy

---

### Post by optotron on 2006-02-23
[QUOTE=Tomy]The K8M800 is a UnichromePro and is better supported when you get to dapper and the 2.6.15-xx kernels. I installed dapperFlight4 the other day and it did not detect the K8M800 at install and I had to create xorg.conf manually. 3d acceleration (dri) did work but the via driver was not-so-great. 

I "borrowed" openchrome_drv.so from Linspire 5.1 beta (Linspire compiles both the openchrome via driver and the xorg via driver). This driver worked fairly well but planetpenguin racer still freezes the system solid. I installed tuxracer from the old hoary repositories and it worked most of the time only freezing towards the end of the race.

UnichromePro support is getting better -- I hope the patches from openchrome.org make it into the xorg via driver before dapper is released.

Tomy[/QUOTE]

Great! I might just try dapperFlight 4 then.

---

### Post by raziel on 2006-04-25
Hi,

I've got a Fujitsu-Siemens Laptop ( L7310W ) with a:

```
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
```

And I'm also getting the black screen of death. I'm with Dapper, and the funny thing is, connecting the laptop to an IBM LCD monitor and pressing Fn + F5 to export the image to the IMB LCD, I'm able to use Xorg - I'm writing this post in that fashion.

If I try to use the laptop's built-in LCD, I get the black screen of death - but I get the intro theme as soon as gdm starts up.

I also have to alternate with Fn+F5 while in grub, if I do it while ubuntu is loading, say at the splash screen, it crashes - If I try to alternate after Xorg is loaded, it also crashes...

Does anyone have an ideas?

Attachments for the Xorg.0.log and xorg.conf follow

---

### Post by automatvapen on 2006-05-09
I have a Acer Aspire 1362LC to.
Is there no way to get the onboard graphics to work correctly?

---

### Post by MihaiM on 2006-06-13
lspci:
VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

If I use 'via' instead of 'vesa' as a device driver glxgears runs ok, google earth shows a black screen and quake 3 has shadows, etc.

I use Ubuntu 6.06 and have a Benq JoyBook R23E

---

