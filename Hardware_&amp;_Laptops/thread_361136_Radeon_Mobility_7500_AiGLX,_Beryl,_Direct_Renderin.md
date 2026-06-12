---
title: "Radeon Mobility 7500 AiGLX, Beryl, Direct Rendering WORKING!!"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by ness0216 on 2007-02-14
I've seen a few posts about people having trouble getting direct rendering to work with the open source radeon drivers. I had the exact same problems that a lot of people had and it seemed like I had tried every solution I could find and came up empty. After some deeper searching I finally got my IBM T42 with the Radeon 7500 to work properly. I'm assuming you already have beryl installed so I won't go over that, I'll just go over some of the issues I had and what steps I took to fix them.

1. fglrx stuff
If you tried to install the fglrx drivers you'll have some junk left over that needs to be removed. This was my main issue. After searching through forums I found that the 7500 and the fglrx driver just don't seem to work correctly. First blacklist the fglrx module.
```

sudo gedit /etc/default/linux-restricted-modules-common

```
Add
```

DISABLED_MODULES="fglrx"

```

Next, uninstall all the packages that you installed for fglrx. I don't have the list of packages that I removed (since they're gone now) but I basically did a search for "fglrx" in synaptic and uninstalled all of them except "xserver-xorg-video-ati"

Reboot

2. Getting direct rendering to work
If you run glxinfo you should find a line like this
```

OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1

```

If you've gotten this far and you still see "direct rendering: No" follow the next few steps. This is the part where I always got tripped up these next few steps solved the problem for me.

First run this command from a shell
```

export LIBGL_DEBUG="verbose"

```
Next run glxgears and note the output. If you encounter an error such as
```

libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/radeon_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/radeon_dri.so failed (/usr/X11R6/lib/modules/dri/radeon_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: radeon_dri.so

```
Then create a symlink like so...
```

sudo ln -s /usr/lib/dri/radeon_dri.so /usr/X11R6/lib/modules/dri/radeon_dri.so

```

If you get an error such as "cannot find libGL.so.1" try this
```

sudo cp /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

```
I think this has to do with fglrx not removing correctly, reinstalling the mesa drivers might also fix this.

Next open up /etc/profile and comment out or remove any lines that were added by fglrx. For example in my file I commented out the following line. I think this is the step most people are missing and this is what finally fixed direct rendering for me.
```

#. /etc/ati/ati-fglrx.sh  # Do not modify - set by ATI FGLRX

```

After all this try reinstalling the following packages.
```

libgl1-mesa-dri libgl1-mesa-glx xserver-xorg-video-ati

```

Finally
```

depmod -a

```

Reboot, login and cross your fingers. If you're lucky you'll get something similar to the output below when you run glxinfo.
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I think my biggest hurdle with all this was getting the fglrx drivers completely removed to finally get direct rendering working.

Beryl / AIGLX stuff
If you have beryl installed add the following to your xorg.conf if they aren't already there.
In the device section add
```

	Option		"XAANoOffscreenPixmaps"
	Option		"AccelMethod" "EXA"
	Option		"DRI" "true"
	Option		"AGPSize"	"32"  #fixes white title bars

```
In the server layout section add
```

	Option		"AIGLX"	"true"

```
And finally
```

Section "Extensions"
	Option  "Composite" "Enable"
EndSection

```

I hope this helps some of you guys out there who have been banging your head over this. I've done so many installs/uninstalls and different tweaks and such I might have left something out. If you still have problems let me know what errors you're getting and I'll try to remember the steps I took to solve them.

---

### Post by alfito on 2007-02-16
Hey! Sincery I thought my problems had blown when I read your post, but.. Unfortunately didn't worked for me. I still get "direct rendering: no"
I am running Feisty and removed fglrx, but I am pretty sure is something related with a wrong uninstall. My card is an ATI X700 Mobility Radeon.
LiveCD shows direct rendering working, I pasted same xorg.conf but nothing...

Any ideas? I will have tu reinstall? ag...

---

### Post by Turin Turambar on 2007-02-16
Thanks ness! It worked! :)

---

### Post by kfbucho on 2007-02-18
Awesome!  It worked. Thanks you ness!

---

### Post by ingo on 2007-02-21
> **ness0216 said:**
> First blacklist the fglrx module.
```

sudo gedit /etc/default/linux-restricted-modules-common

```Add
```

DISABLED_MODULES="fglrx"

```Next, uninstall all the packages that you installed for fglrx. I don't have the list of packages that I removed (since they're gone now) but I basically did a search for "fglrx" in synaptic and uninstalled all of them except "xserver-xorg-video-ati"

RebootWell, that did it for me!!! I've been going through the forums, googling, getting on peoples' nerves and it was as simple as that! Direct rendering is all there and GoogleEarth started up as it is supposed to. Brilliant!

---

### Post by lakamsani on 2007-02-25
Thanks for posting. I got it working too after trying a few things without luck on and off for almost a week. 

My setup is: LinuxMint Bianca on a Compaq Evo N800c with ATI Radeon Mobility 7500. 

Here's the path I took.

First tried this:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Did not work because direct rendering is not enabled. Above page had some useful info on beryl installation, short cuts and how to start beryl in session. I realized that for ATI 7500 I had to try something else.

Then I tried this:
[http://linuxmint.com/forum/viewtopic.php?p=8015](http://linuxmint.com/forum/viewtopic.php?p=8015). See the post by maximus659 with the following instructions:
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True" 

It still did not work. Then I tried this (upgrade to beryl from feisty)
[http://ubuntuforums.org/showthread.php?t=344271](http://ubuntuforums.org/showthread.php?t=344271)

Still did not work. Then I came to this thread. I un-installed all the fglrx stuff and restarted. Beryl started working. I tried to remove the xorg.conf options from [http://linuxmint.com/forum/viewtopic.php?p=8015](http://linuxmint.com/forum/viewtopic.php?p=8015) and it stopped working. So I put them back in. I think I need those for my setup. 

Beryl is nice. Thanks to all the Ubuntu, LinuxMint and Beryl developers and folks that post what works for them. I 'm very close to dropping XP on my laptop. Some of the advanced Vista versions won't even work on my laptop.

---

### Post by Cloudy on 2007-03-08
I don't have a modules folder in /usr/X11R6/lib, is that normal? :/ 

Whenver I try to create a symlink I get:

```

travis@travis-laptop:~$ sudo ln -s /usr/lib/dri/radeon_dri.so /usr/X11R6/lib/modules/dri/radeon_dri.so
ln: creating symbolic link `/usr/X11R6/lib/modules/dri/radeon_dri.so' to `/usr/lib/dri/radeon_dri.so': No such file or directory
travis@travis-laptop:~$

```

---

### Post by ctt1wbw on 2007-03-08
I'm glad I stumbled across this thread.  I'm getting a Thinkpad T30 in a day or so to use for school.  I'm planning on wiping the drive and installing Fedora Core 6.  This laptop has the same ATI card in it.

You think the procedures would be about the same on Fedora as they are here?  I'd love to get Beryl working on it.

---

### Post by ingo on 2007-03-08
Is there any point in running beryl on a t30? I haven't tried on my t41, but if my desktop with an NVidia Geforce 5200 and a faster processor is kind of slow, will a laptop be able to cope at all? be great if you could post your experiences...

---

### Post by ctt1wbw on 2007-03-08
I was wondering the same thing.  The 7500 only 32 meg of vram.  You could probably disable all the screen effects, but leave the rotating cube enabled.  I'll try it and post my results.  I'd love to be able to showcase Beryl in my Intro to Linux class.

---

### Post by Xeor on 2007-03-09
I have a Dell Inspiron 5100 with a Ati Mobility 7500 Radeon 16mb Video Ram.

After following the instruction up here I had to change some configuration in Xorg.conf; Here are the configuration I have now in my Xorg.conf where changes had to be made:

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
  load "drm"
  load "dri"
  load "radeon"
EndSection

and....

Section "Device"
# "identifier"'s name has to be the same that your Device in your Screen Section 
  identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  option "MergedFB" "off"
#	Option		"BusType" "PCI"				#Best Without

# acceleration

#!	VideoRam	"16384"
	Option          "AGPMode" "4"				#ok
	Option          "AGPFastWrite" "yes"			#ok
	Option          "EnablePageFlip" "on"			#ok
	Option          "RenderAccel" "on"			#ok
	Option          "AccelMethod"   "EXA" # or XXA		#ok
#	Option		"BackingStore" "true"
#	Option 		"ExaNoOffscreenPixmaps" 

        # enable (partial) PowerPlay features
#	Option          "DynamicClocks" "on"			#ok?

        # use bios hot keys on thinkpad (aka fn+f7)
#	Option          "BIOSHotkeys" "on"			#Ok?

        # enable radeon specific xinerama
#	Option          "MergedFB" "true"			#Ok?
#	Option          "CRT2Position" "RightOf"		#Ok?
#	Option          "CRT2Hsync" "50-75"
#	Option          "CRT2VRefresh" "30-82"
#	Option          "MetaModes" "1024x768-1280x1024"	#ok?
#	Option          "MergedNonRectangular" "true"

        # Color Tiling
	Option          "ColorTiling"   "on"

        # Video overlay
        Option          "OverlayOnCRTC2"        "on"

EndSection


And...

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 1
  option "MergedFB" "off"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

That's it for the changes I had to do in /etc/X11/Xorg.conf

Now here are the results I get:

run "glxgears -info"
libGL warning: 3D driver claims to not support visual 0x4b
GL_RENDERER   = Mesa DRI Radeon 20060327 AGP 4x TCL
GL_VERSION    = 1.3 Mesa 6.5.1
GL_VENDOR     = Tungsten Graphics, Inc.

run "glxgears -printfps"
libGL warning: 3D driver claims to not support visual 0x4b
3726 frames in 5.0 seconds = 745.035 FPS
3500 frames in 5.0 seconds = 699.729 FPS
3699 frames in 5.0 seconds = 739.565 FPS
3696 frames in 5.0 seconds = 739.049 FPS

After closing a couple a windows:

30492 frames in 5.0 seconds = 6098.284 FPS
33274 frames in 5.0 seconds = 6654.639 FPS
33422 frames in 5.0 seconds = 6684.285 FPS



Much better than the 155 FPS I use to have without Direct Rendering. Thanks to all those that helped me to make it work for some 3D games.

---

### Post by murlosad on 2007-03-09
great how-to, I didn't realize that I didn't need (in fact couldn't use) the fglrx drivers with beryl.  So, after borking my first install, I had beryl up and running in about 30 minutes (fresh install included).  It's a beautiful thing.

---

### Post by martintfd on 2007-03-12
Very helpful, thanks fizz!

---

### Post by reidi on 2007-03-16
This method worked great for me:

Feisty ~herd5
ATI Radeon 7000/VE AGP
Athlon 2000+ CPU

- I also believe "killing" fglrx was the solution.
- Direct rendering worked fine after that.  

However... I now have extremely choppy graphics in GoogleEarth, and glxgears, run from Beryl.  (both run okay from the normal Gnome window manager).

I guess this is 'cause I have an "older" AGP card, and CPU ?

This was not an issue before when direct rendering was not working, and I was starting Beryl with:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl

Any ideas on how to improve performance?

---

### Post by ctt1wbw on 2007-03-16
Okay, I got Fedora Core 6 installed on my Thinkpad T30.  The ATI Mobility 7500 worked out of the box, direct rendering enabled and opengl working.  Glxgears gives me about 750 fps and I haven't installed fglrx or aiglx.  Beryl works on this just fine, with no mods to the xorg.conf file.  But for some reason, when I'm running a screensaver along with beryl, the screen locks up and goes haywire.


I might have to add the previous lines about dri and aiglx.

---

### Post by jodokast98 on 2007-03-24
I tried the "fast" xorg.conf and it worked ok, but I was only getting 600-700 fps from glxgears and feisty's desktop effects were slow.

Out of curiousity I loaded up Mandravia One's Gaming DVD 2007.0 and it had an excellent xorg.xonf for my Mobility 7500 on my dell inspiron 5100.  Worked fine with Feisty and Compiz.  Even works well with beryl and emerald.




# File generated by XFdrake (rev 57713)

# **********************************************************************
# Refer to the xorg.conf man page for details about the format of
# this file.
# **********************************************************************

Section "Files"
    # font server independent of the X server to render fonts.
    FontPath "unix/:-1"
    
    # minimal fonts to allow X to run without xfs
    FontPath "/usr/share/fonts/misc:unscaled"
EndSection

Section "Extensions"
    Option "Composite"
EndSection

Section "ServerFlags"
    #DontZap # disable <Crtl><Alt><BS> (server abort)
    #DontZoom # disable <Crtl><Alt><KP_+>/<KP_-> (resolution switching)
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri" # direct rendering
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection

Section "InputDevice"
    Identifier "SynapticsMouse1"
    Driver "synaptics"
    Option "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1400x1050"
    HorizSync 31.5-90
    VertRefresh 60
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_120"  262.44  1400 1520 1672 1944  1050 1051 1054 1125  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_100"  214.39  1400 1512 1664 1928  1050 1051 1054 1112  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_85"  179.26  1400 1504 1656 1912  1050 1051 1054 1103  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_75"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_60"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1400x1050_50"  99.88  1400 1480 1624 1848  1050 1051 1054 1081  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_120"  233.79  1280 1384 1528 1776  1024 1025 1028 1097  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_100"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_85"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_75"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_60"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x1024_50"  89.38  1280 1352 1488 1696  1024 1025 1028 1054  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_120"  217.32  1280 1376 1520 1760  960 961 964 1029  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_100"  178.99  1280 1376 1520 1760  960 961 964 1017  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_85"  149.43  1280 1376 1512 1744  960 961 964 1008  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_75"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_60"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x960_50"  82.99  1280 1344 1480 1680  960 961 964 988  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_120"  176.01  1152 1240 1368 1584  864 865 868 926  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_100"  143.47  1152 1232 1360 1568  864 865 868 915  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_85"  119.65  1152 1224 1352 1552  864 865 868 907  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_75"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_60"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1152x864_50"  66.85  1152 1208 1328 1504  864 865 868 889  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_120"  139.05  1024 1104 1216 1408  768 769 772 823  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_100"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_85"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_75"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_60"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1024x768_50"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_120"  91.20  832 896 984 1136  624 625 628 669  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_100"  74.03  832 888 976 1120  624 625 628 661  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_85"  61.56  832 880 968 1104  624 625 628 656  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_75"  53.20  832 872 960 1088  624 625 628 652  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_60"  41.55  832 864 952 1072  624 625 628 646  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "832x624_50"  33.95  832 856 944 1056  624 625 628 643  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_120"  83.95  800 856 944 1088  600 601 604 643  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_100"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_85"  56.55  800 840 928 1056  600 601 604 630  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_75"  48.91  800 840 920 1040  600 601 604 627  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_60"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "800x600_50"  31.15  800 824 904 1008  600 601 604 618  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_120"  52.41  640 680 744 848  480 481 484 515  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_100"  43.16  640 680 744 848  480 481 484 509  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_85"  35.71  640 672 736 832  480 481 484 505  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_75"  30.72  640 664 728 816  480 481 484 502  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_60"  23.86  640 656 720 800  480 481 484 497  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "640x480_50"  19.40  640 648 712 784  480 481 484 495  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_120"  28.98  480 504 552 624  360 361 364 387  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_100"  23.84  480 504 552 624  360 361 364 382  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_85"  19.59  480 496 544 608  360 361 364 379  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_75"  16.74  480 488 536 592  360 361 364 377  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_60"  12.89  480 480 528 576  360 361 364 373  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "480x360_50"  10.39  480 472 520 560  360 361 364 371  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_120"  12.38  320 328 360 400  240 241 244 258  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_100"  9.79  320 320 352 384  240 241 244 255  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_85"  8.26  320 320 352 384  240 241 244 253  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_75"  6.93  320 312 344 368  240 241 244 251  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_60"  5.26  320 304 336 352  240 241 244 249  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "320x240_50"  4.17  320 304 328 336  240 241 244 248  -HSync +Vsync
EndSection

Section "Device"
    Identifier "device1"
    VendorName "ATI Technologies Inc."
    BoardName "ATI Radeon"
    Driver "ati"
    Option "DPMS"
    Option "XaaNoOffscreenPixmaps" "1"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 16
    
    Subsection "Display"
        Depth 8
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "SynapticsMouse1" "AlwaysCore"
    Screen "screen1"
EndSection

---

### Post by john_navarro on 2007-03-28
I finally have a xorg.conf file that works great on an IBM T30 laptop with Feisty Beta 1. See the attachment for the entire file. I added and removed so many things thtat I don't know what exactly fixed it:

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"

	Load "dbe"                     <-- added this one
	Load "type1"                  <-- and this one
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	Option "XAANoOffscreenPixmaps" "1"
	Option "AGPSize" "32"
	Option "DRI" "true"
	Option "DPMS"
	BusID		"PCI:1:0:0"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite"
EndSection

---

### Post by Cloudy on 2007-03-29
> **john_navarro said:**
> I finally have a xorg.conf file that works great on an IBM T30 laptop with Feisty Beta 1. See the attachment for the entire file.

I don't see any attachment, sir..

---

### Post by martz on 2007-04-10
This is the closest thread I can find for my problem, so maybe someone here can help me.  I've got an IBM T40 and have Edgy Eft installed (fresh installation).

The reason I switched from windows was because windows started giving me quite a number of BSOD whenever I wasn't logged into safe mode.  (Safe mode worked, regular windows wouldn't).

So I switched.  The first time I ran ubuntu after installation it worked fine.  (this was using the ati drivers)  but eventually it froze, or the screen would go completely black (no mouse even).  So I followed the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=187177]("http://ubuntuforums.org/showthread.php?t=187177")

and switched to the vesa drivers.  Now I can stay in ubuntu as long as I want with no crashes (so far as I know) but it's horrendously slow graphics wise.  (even scrolling in firefox is slow).

I've tried several of the xorg.conf's in this thread, and followed some of the other directions, but really nothing works for an extended period of time.  It may work the first run, then after a minute or so in gnome it will give me the black screen where i can't do anything.  The next reboot it won't even show me the gdm... so i have to always go back to the thread above and switch back to vesa.

Anyone have any ideas?

Is my graphics card 'bad' now?

It's a 4 year old laptop.  I'm going to get a macbook pro soon but I'm waiting for leopard to come out.

Thanks for any help...

Martz

---

### Post by BlaineM on 2007-04-11
> **ingo said:**
> Is there any point in running beryl on a t30? I haven't tried on my t41, but if my desktop with an NVidia Geforce 5200 and a faster processor is kind of slow, will a laptop be able to cope at all? be great if you could post your experiences...

these directions opened up aiglx like nothing ever has for my t30... beryl didnt work for junk before, but now it runs quite well.  very smooth. the only thing is setting beryl in the manager to force use of aiglx under the rendering platform option... 

the only thing that I noticed is when scrolling pages in firefox, it slows slightly... but not enough for me to complain about it.  and when maximized screens the edges white out... but I found a fix for that problem.

I think Ill keep my t30 for some time longer now...  I was planning on upgrading, but no need... 

thanks alot for your work in finding this fix for my ati card.. this is great.

---

### Post by theonlyrealperson on 2007-04-12
WOW!!!!!!!!!! 

I honestly can't believe it. Like you ness0216, I've been fighting with my Mobility 7500 and fglrx for about a month now... I was literally about to give up and dual boot with Ubuntu and maybe Sabayon so I could play a little.

Now I have Beryl, and it works!!!!!!!!

I now have the perfect operating system.

THANK YOU NESS0216!!!! I owe you huge!

:guitar: :D

---

### Post by josephus on 2007-04-12
martz,

given that that you are having troubles with your video on both Windows and Linux, it sounds like a safe bet that it is indeed a hardware issue.  I had a T30 not that long ago that I dropped, after which it would only work with an external monitor at 640x480, switching the resolution to anything higher would cause the system to immediately shutdown.  i don't know if this would work in your case, but maybe try running it at a lower resolution.  either way it sounds like the system is near its end of life.

---

### Post by mardawi on 2007-04-14
This is amazing! it totally worked on my T40 :guitar: 

I don't have the water effect working, and it's a little bit slow on animations. But other than that, it's great!

Thanks a lot for posting this!

---

### Post by pasha85 on 2007-05-15
Hey

I've a T41 with the 7500 installed. Beryl installed fine, and the cube works and rotates fine. The problem is that some windows are displayed with gray parts or no parts at all, no text boxes, etc.
Anyone with this problem? 
Thanks,

---

### Post by olterman on 2007-05-18
Hmm I am sitting here with my T40 and I have never had the restricted drivers installed still everytime I try to load desktop-effects I get booted out of X and get my GDM login .... (Running Feisty with compiz, no beryl)

---

### Post by olterman on 2007-05-18
I pasted in this xorg conf and suddenly I had compiz running

> **john_navarro said:**
> I finally have a xorg.conf file that works great on an IBM T30 laptop with Feisty Beta 1. See the attachment for the entire file. I added and removed so many things thtat I don't know what exactly fixed it:


However as I loaded the gl preferences gui It started frantikly killing my gnome bar and reloading it but after a reboot of GDM it seems to work fine thanx for another great thread on ubuntu forums.

---

### Post by olterman on 2007-05-18
After a bit of testing I am really happy with the desktops performance, It runs smooth and great however I can't start games in cedega, might be a Cedega bug tho and when I run neverput and neverball I get abysmal performance ... anyone know if this is to be expected with compiz or if I should keep trying

---

### Post by Nephron on 2007-05-31
Right, after much searching, like many people, I finally got direct rendering to work.
Make sure fglrx has been remove (see above) and then do this:

The new bit is something I found in the "Device" section of an xorg.conf from a guy called "acgarib" from [here]("http://forum.beryl-project.org/viewtopic.php?f=36&t=6099&p=32954").

Enter this in the "Device" section of your xorg.conf rather than any other options:

> Option      "UseFBDev"      "true"
	Option      "ColorTiling"      "true"
	Option      "EnablePageFlip"   "true"
	Option      "AccelMethod"      "XAA"
	Option      "XAANoOffscreenPixmaps" "true"
	Option      "RenderAccel"      "true"
	Option      "AGPMode"      "4"
	Option       "AddARGBGLXVisuals"    "True"
	Option       "DisableGLXRootClipping" "True"

This worked for me (ATI Mobility Radeon 7500 ... I think)

Just to make this idiot proof, make sure you do the other things described above, i.e. add this:

to "ServerLayout":

> Option		"AIGLX"	"true"

to the end:

> Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option  "Composite" "Enable"
EndSection

---

### Post by jazzclubber on 2007-06-30
IBM Thinkpad T42 Beryl Radeon 7500 setup problems.

The man who wrote this thread is pure genius. This has changed all of KDE to run very neatly. Even if I don't use the 3D functions everything menu and window wise behaves itself better. When following the instructions the essential part is to run a search on your package manager and uninstall everything relating to fglrx drivers. I used to run xgl desktop and it would run but the screen seemed to be at the wrong resolution. Fixed now though. Many many many thanks.

Gav.

---

### Post by Ariccanfly on 2007-12-25
it woked for me and my IBM think pad after some tweaking heres my Xorg...

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
#radeon	ati
	Driver		"ati"
	BusID		"PCI:1:0:0"
	#Option "MergedFB" "off"
	#Option "AGPMode" "4" #ok
	#Option "AGPFastWrite" "yes" #ok
	#Option "EnablePageFlip" "on" #ok
	#Option "RenderAccel" "on" #ok
	#Option "AccelMethod" "EXA" # or XXA #ok
	#Option "ColorTiling" "on"
	#Option "OverlayOnCRTC2" "on"


Option "UseFBDev" "true"
Option "ColorTiling" "true"
Option "EnablePageFlip" "true"
Option "AccelMethod" "XAA"
Option "XAANoOffscreenPixmaps" "true"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True" 


EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
	#addedthis
	Option		"XAANoOffscreenPixmaps"
	Option		"AccelMethod" "XXA" #exa
	Option		"DRI" "true"
	Option		"AGPSize"	"32"  #fixes white title bars
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	#addedthistoo	
	Option		"AIGLX"	"true"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"

EndSection #addedthis too

	Section "DRI"
	Mode 0666
	EndSection


Section "Extensions"
	Option  "Composite" "Enable"
EndSection

---

