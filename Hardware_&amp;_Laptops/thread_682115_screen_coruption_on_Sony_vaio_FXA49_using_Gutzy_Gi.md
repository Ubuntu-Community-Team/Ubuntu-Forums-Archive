---
title: "screen coruption on Sony vaio FXA49 using Gutzy Gibon"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by wwookie12 on 2008-01-29
I just installed the latest version of Ubuntu and after testing my 6 year old laptop by running the LiveCD with no problems, I installed it to the disk. Only after I installed I get some screen corruption on the LCD(vertical lines two pixels wide) that won't go away. I have no idea why it appears after install. Anybody have any suggestions? 

See the attached pic below.

Some system specs are:

AMD Athlon 1.2gHz
512 MB Ram
ATI Rage Mobility 8MB Graphics card

---

### Post by wwookie12 on 2008-02-01
I am beginning to think that this may be the wrong place to post, but here I am. First I wanted to bump, second add a little more info about the problem.

The lines go away if I plug in an external monitor, switch picture output to said monitor, then back to the laptop. So I believe that its a hardware issue with the laptop's LCD, but I don't know why it happens. Also does anyone have any input on how the LiveCD handles hardware that might be different from a full install?

I will be thankful for any help.

---

### Post by xeth_delta on 2008-02-01
The liveCD will most likely use either a generic or an open source driver.
If you want to use a proprietary one you will have to install it on the hard-disk.

I will post some ideas tomorrow, sorry i cannot do it now.

Xeth

---

### Post by wwookie12 on 2008-02-07
Well I found a fix...sort of. By using the generic VESA driver the problem went away, though now when I log off the screen goes wonky for a few seconds, but the lines are gone. If any one comes across away that the default ATI drivers could work, let me know.

---

### Post by xeth_delta on 2008-02-09
> **wwookie12 said:**
> Well I found a fix...sort of. By using the generic VESA driver the problem went away, though now when I log off the screen goes wonky for a few seconds, but the lines are gone. If any one comes across away that the default ATI drivers could work, let me know.

wwookie, what driver where you using when the lines where present? The proprietary ones (fglrx) or the open source ones (radeon/ati) ones? Unlike vesa, any of these I mentioned should also provide 3D acceleration.

---

### Post by wwookie12 on 2008-02-09
I was using the open source drivers that came with the 7.10 distro for ATI Rage Mobility. I haven't been able to find and propriatary at least ones that i could install onto the system. Do you know how? Because I have the driver from the ATI website that installs for Windows.

---

### Post by xeth_delta on 2008-02-09
> **wwookie12 said:**
> I was using the open source drivers that came with the 7.10 distro for ATI Rage Mobility. I haven't been able to find and propriatary at least ones that i could install onto the system. Do you know how? Because I have the driver from the ATI website that installs for Windows.

How old is the computer? I am not sure whether that card has 3d acceleration support on the proprietary drivers, but you maybe could still get better performance than with the vesa driver. Another laptop of mine has a Radeon Mobility 9000 IGP, it does not have 3d acceleration with the proprietary driver, but works great with the open source one.

I am not sure if I asked you this before, please post the output of:
```
sudo lshw -C Video
```
```
glxinfo
```
and the contents of "/etc/X11/xorg.conf".
Please post the code/output between CODE tags, for easier reading. You can use the # button in the posting page.

---

### Post by wwookie12 on 2008-02-11
**Here you go, in the order you requested. Thanks for all the help BTW.**




```
  description: VGA compatible controller
       product: Rage Mobility P/M AGP 2x
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 64
       width: 32 bits
       clock: 33MHz
       capabilities: agp agp-1.0 pm vga bus_master cap_list
       configuration: latency=66 mingnt=8

```

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by xeth_delta on 2008-02-11
You're welcome. Now, let's try a couple of things. If you have a look at /etc/X11/xorg.conf" You will see a <<Section "Device">>. You probably know this already, the line that starts with **driver** tells X11 what driver to use. Right now vesa is being used. Could you try opening the file with root privileges, then replacing "vesa" with "ati", save the file, reboot or kill the X11 server with Control-Alt-Backspace. Check what happens and post the output of glxinfo.

Try the same procedure replacing "vesa" with "radeon". Let us know the results.

---

### Post by xeth_delta on 2008-02-11
One driver I forgot to mention, and which has a high probablility of working: r128.
Replace "vesa" with "r128" and repeat the same procedure.

---

### Post by wwookie12 on 2008-02-11
one other question, When I am in the GUI how can I get root access? so far the only way I have accomplished this was to restart and use the command line as root. I know there is an easier was. Also this is my first real Linux experience. Until now i had used Unix, but some of the commands that I used there don't work here.

---

### Post by xeth_delta on 2008-02-11
> **wwookie12 said:**
> one other question, When I am in the GUI how can I get root access? so far the only way I have accomplished this was to restart and use the command line as root. I know there is an easier was. Also this is my first real Linux experience. Until now i had used Unix, but some of the commands that I used there don't work here.

Ubuntu has the policy to disable the root account as default. There is a small group of users (for example the first one created when installing Ubuntu) that are able to run commands with administrative privileges.
To run commands as root / with administrative privileges you have to precede them with sudo in the command line:
```
sudo command_to_be_run
```
or to run one that would use a graphical interface, for Gnome:
```
gksudo command_to_be_run
```
or for KDE:
```
kdesu command_to_be_run
```

There is, of course a way to permanently enable the root account, if you need to do that.

---

### Post by wwookie12 on 2008-02-11
As for permanent Root I am fine for now but maybe later. So far all the changes have resulted in worse results. Both times that I changed it, It reverted to the vesa and gave me a low graphics setting warning along with a lot of screen degredation.

---

### Post by xeth_delta on 2008-02-11
> **wwookie12 said:**
> As for permanent Root I am fine for now but maybe later. So far all the changes have resulted in worse results. Both times that I changed it, It reverted to the vesa and gave me a low graphics setting warning along with a lot of screen degredation.

Even with r128? Another driver you could give a try is atimisc.

---

### Post by wwookie12 on 2008-02-11
well now all display sections (graphics card and Monitor) of the xorg.conf file have gone to "fail safe". How do I revert it?

---

### Post by xeth_delta on 2008-02-11
> **wwookie12 said:**
> well now all display sections (graphics card and Monitor) of the xorg.conf file have gone to "fail safe". How do I revert it?

What do you mean by "gone to safe fail"? One way would be to over-write xorg.conf with a previous copy.

First, make a back-up of the current file, then open it with root privileges erase the contents and paste the xorg contents you sent in a previous post. Reboot and it should be it.

---

### Post by wwookie12 on 2008-02-11
I guess it happens when I changed the driver an the xserver didn't know what to do with it. Any ways I reconfigured the Xserver and tried the "atimisc" in place and it did not work either. I guess I may be stuck using the vesa... oh well.

---

### Post by xeth_delta on 2008-02-11
> **wwookie12 said:**
> I guess it happens when I changed the driver an the xserver didn't know what to do with it. Any ways I reconfigured the Xserver and tried the "atimisc" in place and it did not work either. I guess I may be stuck using the vesa... oh well.

For now, at least. We'll try to tjink of something else. The card is a bit old, that could very well be the reason for the bad driver support.

---

