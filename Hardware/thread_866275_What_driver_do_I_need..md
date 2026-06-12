---
title: "What driver do I need."
date: 2008-07-21
forum: Hardware
---

### Post by tatoniss on 2008-07-21
I would like to enable my graphics card and keep the resolution decent not 800x800 I would like to keep my current resolution of 1024x768

My card is a ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

Here is the output of glxinfo

```
tatoniss@Eric-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Your help would be greatly appreciated
If there is any info you need that I did not post just tell me.

---

### Post by phidia on 2008-07-21
Have you looked at/tried [this thread]("http://ubuntuforums.org/showthread.php?t=515573")? There are also guides at the community docs [here]("https://help.ubuntu.com/community/Video").

---

### Post by tatoniss on 2008-07-21
The first link says there is a database error and I don't know if the instructions will work for this card, its kind of old the computer i am using was bought in 1999 but the card worked fine on xp. If it will work I can try it but the last time I tried it only worked at a really low resolution.

---

### Post by soxs on 2008-07-21
> **phidia said:**
> Have you looked at/tried [this thread]("http://ubuntuforums.org/showthread.php?t=515573")? There are also guides at the community docs [here]("https://help.ubuntu.com/community/Video").

I doubt that fglrx will help you as that card is very old.
You should either try to change your driver in your /etc/X11/xorg.conf in the device section to "ati" or to "radeon" (both builtin kernel drivers) and you should go fine.

Plx post your current xorg.conf, and chek whcih driver is the right one for your card (I don't know which one, sry).

---

### Post by tatoniss on 2008-07-22
I tried it at ati so now I will try radeon, I followed some instructions from the link the other person provided and i think it worked but when i tried to enable basic effects the screen went white and i have a low frame rate

---

### Post by tatoniss on 2008-07-22
```
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"ati card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode"        "8"
        Option          "AccelMethod"    "XAA"  #either XAA or EXA. "XAA" is the default and safe choice
        Option          "ColorTiling"    "on"
        Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
        Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       "64"   #This is the size of the "GART" that xorg will use.

        BusID           "PCI:1:0:0"             #must match your lspci output
EndSection

Section "Monitor"
	Identifier	"dell Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ati card"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768"
                Virtual         1024 768
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by jocko on 2008-07-22
> **tatoniss said:**
> I tried it at ati so now I will try radeon, I followed some instructions from the link the other person provided and i think it worked but when i tried to enable basic effects the screen went white and i have a low frame rate

I'm pretty sure "radeon" will NOT work for an old rage card (it is, as the name implies, written for radeon cards...).
"ati" is, as far as I know, just a wrapper which will automatically select the best open source driver for you (which I guess is "r128").
So stay with "ati" for that card.

For your low frame rate, you do have a VERY old graphics card, so you shouldn't expect anything else than a very poor frame rate if you try to use compiz (I didn't know it would work at all on such an old card).
I'm not sure how to solve the white screen problem. It has happened to me with both ati and nvidia graphics cards (both using restricted drivers), but I don't remember how I fixed it on either of them.

---

### Post by soxs on 2008-07-22
> **tatoniss said:**
> I tried it at ati so now I will try radeon, I followed some instructions from the link the other person provided and i think it worked but when i tried to enable basic effects the screen went white and i have a low frame rate

Don't expect it to get any better. Your card is simply too old. Fglrx doesn't support your card anymore and your graphicscards 3D capabilities are limited though the opensource driver should support your card quite well.

---

### Post by tatoniss on 2008-07-22
OK Thanks for your help Though I once tried to enable the dri by following instructions and all that it did was make some of the checks that compiz check preformed red when they used to be all green but it made the screen saver faster and gave me a higher frame rate but for some reason recently it went back to the old way.

here is what i did

```
DRIVER_VS="6.8.192"

sudo echo "activating sudo rights"

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev  git-core libdrm-dev mesa-common-dev
SRCPATH=`pwd` 
cd $SRCPATH 
if [ -d 'src' ]; then echo -n ""; else mkdir src ; fi
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm ;
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
fi
if [ -f 'xf86-video-ati-$DRIVER_VS.tar.bz2' ]; then echo "already have xf86-video-ati"; else \
	wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-$DRIVER_VS.tar.bz2 ;     \
	tar xvjf xf86-video-ati-$DRIVER_VS.tar.bz2  ;\
fi
cd xf86-video-ati-$DRIVER_VS
./configure --prefix=/usr
make clean
make
sudo make install
cd $SRCPATH/
echo -e "\nsudo /etc/init.d/gdm restart\n"
```

so what exactly did this do when I preformed it and is there a way to speed up the card a little so the screen saver is not so slow, or why did it go back.

---

### Post by soxs on 2008-07-22
> **tatoniss said:**
> OK Thanks for your help Though I once tried to enable the dri by following instructions and all that it did was make some of the checks that compiz check preformed red when they used to be all green but it made the screen saver faster and gave me a higher frame rate but for some reason recently it went back to the old way.

here is what i did

```
DRIVER_VS="6.8.192"

sudo echo "activating sudo rights"

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev  git-core libdrm-dev mesa-common-dev
SRCPATH=`pwd` 
cd $SRCPATH 
if [ -d 'src' ]; then echo -n ""; else mkdir src ; fi
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm ;
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
fi
if [ -f 'xf86-video-ati-$DRIVER_VS.tar.bz2' ]; then echo "already have xf86-video-ati"; else \
	wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-$DRIVER_VS.tar.bz2 ;     \
	tar xvjf xf86-video-ati-$DRIVER_VS.tar.bz2  ;\
fi
cd xf86-video-ati-$DRIVER_VS
./configure --prefix=/usr
make clean
make
sudo make install
cd $SRCPATH/
echo -e "\nsudo /etc/init.d/gdm restart\n"
```

so what exactly did this do when I preformed it and is there a way to speed up the card a little so the screen saver is not so slow, or why did it go back.

This code gets the git mesa code, compiles it, and checks wether a mach64 module was created, and if soit fixes dependencies and tries to load it. afterwards it tries to download xf86-video-ati driver (don't ask me wether this is the correct driver for your card.) and compiles that one and restarts x.

---

### Post by tatoniss on 2008-08-05
Ok That makes since what ever it did it gave me a frame rate speed up but now it has gone back down. I guess I should not really expect any more, thanks for all your help guys.

---

### Post by evets25 on 2008-08-05
IIRC, the ATI Rage Pro is one of the lucky few that has a fully working open source driver. It's so old that they've had time to completely reverse-engineer it and create a new open source driver. :) Actually I have one of those cards at home still, and last time I used it, I plugged it in and it "just worked". No idea what you problem is though, sorry.

---

