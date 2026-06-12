---
title: "ATI driver updates"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by RedSingularity on 2009-03-09
How do i know if i have the most recent version of my ATI drivers?

---

### Post by RedSingularity on 2009-03-09
Bump........anyone?

---

### Post by Neo_The_User on 2009-03-09
fglrxinfo. I can't remember the latest fglrx version ATM its above 8.555 right now. Tell me the version and I'll tell you if its the latest one.

---

### Post by RedSingularity on 2009-03-10
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 1.4 (2.1.8087 Release)
```

---

### Post by Neo_The_User on 2009-03-10
No the whole thing. I can't tell just by the OpenGL version.

---

### Post by RedSingularity on 2009-03-10
Thats all i get

---

### Post by Neo_The_User on 2009-03-10
hmm..

glxinfo | grep fglrx && dmesg | grep fglrx

WAIT! 2.1.8087 IS 8.54.X meaning its old. You have a very old ATi driver running.

---

### Post by RedSingularity on 2009-03-10
Nope, that doesnt give me anything.

---

### Post by Neo_The_User on 2009-03-10
Yeah your driver is way out of date.

---

### Post by RedSingularity on 2009-03-10
Where to the newest one?  ATI website?

---

### Post by Neo_The_User on 2009-03-10
Yeah but build it by hand. buildpkg. If you need help I can write you a kickass guide on building fglrx specifically for Ubuntu. It'll be so wicked kick that your graphics will scream! You doing this on a custom kernel or an ubuntu kernel that you installed via repos? Either way, I can be of great assistance! XD

---

### Post by RedSingularity on 2009-03-10
It is a kernel i got with repos, no mods.  I would appreciate any help though!!

---

### Post by Neo_The_User on 2009-03-10
You using AMD64 or X86?

---

### Post by RedSingularity on 2009-03-10
Amd64

---

### Post by Neo_The_User on 2009-03-10
Do all this in a terminal in your home directory. Keep in mind that this is against the Ubuntu way (what you want if you don't want slow graphics)

```

mkdir ati && cd ati && wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run
sh ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/intrepid
sudo apt-get update && sudo apt-get dist-upgrade 
sudo apt-get install cdbs dkms libstdc++5 libstdc++6 build-essential fakeroot debconf debhelper ia32-libs dh-make
sudo dpkg -i xorg-driver-fglrx_8.582-0ubuntu1_amd64.deb fglrx-kernel-source_8.582-0ubuntu1_amd64.deb fglrx-amdcccle_8.582-0ubuntu1_amd64.deb fglrx-mod*

```

There should be 2 more deb packages in your ATi folder. sudo dpkg -i them too. If you get errors with the dpkg -i command do this

```

sudo apt-get install -f
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.582-0ubuntu1_amd64.deb fglrx-kernel-source_8.582-0ubuntu1_amd64.deb fglrx-amdcccle_8.582-0ubuntu1_amd64.deb fglrx-mod*

```

Now before you reboot, run this command:

```

sudo aticonfig --initial -f

```

And put the other 2 files in the --force-overwrite command. Be sure to run sudo dpkg -i on all the deb packages in the ati folder of your home directory if you want further optimization, better preformance, and a lower risk of your monitors saying "Out of Range" or something like that. Hope this works. Report all errors here and I will help you best I can. I've pretty much seen every possible error with fglrx.

---

### Post by RedSingularity on 2009-03-10
Sounds Good!!  Thanks alot :) :) :)

---

### Post by Neo_The_User on 2009-03-10
> **Shadow121 said:**
> Sounds Good!!  Thanks alot :) :) :)

No problem. I do lots of fglrx hacking.

---

### Post by RedSingularity on 2009-03-10
Ok, installing now.  What do you mean its against the ubuntu way?

---

### Post by Neo_The_User on 2009-03-10
> **Shadow121 said:**
> Ok, installing now.  What do you mean its against the ubuntu way?

It's not the normal way of installing the drivers but it works much better.

---

### Post by RedSingularity on 2009-03-10
While its installing i have a question.  Before i installed these drivers the "normal" way and had a problem.  I noticed that when i locked the screen and then tryed to log back into ubuntu, by moving the mouse or typing, the login box wouldnt come up.  All i could see was a black screen and the mouse.  I could still login though by typing my password into the "blackness".  Any idea what that was about?

---

### Post by Neo_The_User on 2009-03-10
> **Shadow121 said:**
> While its installing i have a question.  Before i installed these drivers the "normal" way and had a problem.  I noticed that when i locked the screen and then tryed to log back into ubuntu, by moving the mouse or typing, the login box wouldnt come up.  All i could see was a black screen and the mouse.  I could still login though by typing my password into the "blackness".  Any idea what that was about?

The one in the ubuntu repos are so incredibly old it was most likely just a flaky version. You'd love the new version much better. Also if you really want to get fast graphics in addition to the latest drivers, check out rovclock. You can overclock and underclock your GPU. its in the 8.10 repos.

```

sudo apt-get install rovclock

```

Careful, set too quick and you might have to do a hard reset.

---

### Post by RedSingularity on 2009-03-10
Well how bout that......works great!  Thanks a lot for this!!  :)

---

### Post by Neo_The_User on 2009-03-10
> **Shadow121 said:**
> Well how bout that......works great!  Thanks a lot for this!!  :)

Check fglrxinfo and make sure its using it. Oh shoot I almost forgot, I am so sorry.

Do this as well:

```

gksudo gedit /etc/default/linux-restricted-modules-common

```

In between the quotes type in fglrx with all lowercase letters.

It should look like this:

```

DISABLED_MODULES="fglrx"

```

If you experience screen flickering or problems with Compiz, let me know and I can help you out again.

After editing /etc/default/linux-restricted-modules-common reboot your computer.

---

### Post by RedSingularity on 2009-03-10
Here is the new drivers in use,

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 2.1.8494 Release

```And i just edited that text file.

Thanks again!

PS:  I ever have any problems with my graphics i know who i am goin to.

---

### Post by Neo_The_User on 2009-03-10
> **Shadow121 said:**
> Here is the new drivers in use,

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 2.1.8494 Release

```

And i just edited that text file.

Thanks again!

Looks good! No problem. If you have any questions, just let me know! ;)

This is going to sound kind of silly but I've been using the open source ATi drivers with Mesa for the last 3 months. hahaha.

---

### Post by chemamar on 2009-03-12
> **Neo_The_User said:**
> It's not the normal way of installing the drivers but it works much better.

Hi Neo_the_user, I have a Radeon 9800 PRO, I tried the propietary drivers but they did not work nicely for me, now I am trying the open source drivers that are not running well either playing DVD (I have installed Medibuntu), could you please teach me how to install both propietary drivers and open source drivers for x86 in your way?

Thanks a lot!

---

### Post by Neo_The_User on 2009-03-12
The guide is on page 2 of this thread. I have a 9800 PRO as well. I think its the top selling AGP graphics card. For DVD playback enhancement add this to your xorg.conf file in /etc/X11/xorg.conf by doing this command in the terminal:

```

gksudo gedit /etc/X11/xorg.conf

```

Add these lines into your Section "driver"

```

        Option     "AGPMode"                    "4"
        Option     "AGPFastWrite"               "True"
        Option     "AGPSize"                    "8"
        Option     "DMAForXv"                   "True"

```

DMAForXv is for DVD playback enhancement (less CPU usage) and the others do general GPU performance enhancement. XD

VLC utilizes XVideo the most when configured correctly. Use VLC with the DMAForXv option and your DVDs will be really smooth and fast.

---

### Post by chemamar on 2009-03-12
> **Neo_The_User said:**
> The guide is on page 2 of this thread. I have a 9800 PRO as well. I think its the top selling AGP graphics card. For DVD playback enhancement add this to your xorg.conf file in /etc/X11/xorg.conf by doing this command in the terminal:

```

gksudo gedit /etc/X11/xorg.conf

```

Add these lines into your Section "driver"

```

        Option     "AGPMode"                    "4"
        Option     "AGPFastWrite"               "True"
        Option     "AGPSize"                    "8"
        Option     "DMAForXv"                   "True"

```

DMAForXv is for DVD playback enhancement (less CPU usage) and the others do general GPU performance enhancement. XD

Thanks but after doing that I reboot and the graphics went wrong, I had to go again to default xorg.conf.
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I think that I have installed something wrongly, I don't know either if I have the latests open source drivers, if Mesa is OK, DRM, etc... (by the way it is obvious that I am a newbie in this:D)
```

jose@jose-desktop:/etc/X11$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6e 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x71  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x73  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x79  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7b  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7e  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

I am afraid I need a tutorial to install properly the latests open source drivers:biggrin:

DVD is playing also awful, with vertical lines all over the screen. I havbe installed medibuntu by the way.

I appreciate your help.

---

### Post by Neo_The_User on 2009-03-15
Yes I can surely help you. I haven't been online much recently, sorry. Run this command in the terminal as it seems you forgot to do this:

```

sudo aticonfig --initial -f

```

If you need to compile the open source drivers I'd recommend following these 3 guides (they are all a bit different and mine is out of date. I will re-write the whole guide after 9.04 comes out.)

[http://ubuntuforums.org/showthread.php?t=1036456](http://ubuntuforums.org/showthread.php?t=1036456) - Mine. Best suited for those who really know what they are doing.
[http://dri.freedesktop.org/wiki/Building#head-1d3236b8fe603a3ecc41c7295609f538aca9b38c](http://dri.freedesktop.org/wiki/Building#head-1d3236b8fe603a3ecc41c7295609f538aca9b38c) - Official guide. Best suited for new users.
[http://www.x.org/wiki/Development/git](http://www.x.org/wiki/Development/git) - Xorg's version. Best suited for the intermediate level of experience.

---

### Post by reverseninja on 2009-03-15
Good sir!  I followed your install instructions on page 2 (and the addendum on page 3) and rebooted but I'm still using the old 8.54.3 release.  I also am 8.10 x64.  Any hints or suggestions?  I'll owe you a coke!  Thanks!

---

### Post by Neo_The_User on 2009-03-16
> **reverseninja said:**
> Good sir!  I followed your install instructions on page 2 (and the addendum on page 3) and rebooted but I'm still using the old 8.54.3 release.  I also am 8.10 x64.  Any hints or suggestions?  I'll owe you a coke!  Thanks!

Use the -force--overwrite command or something at the lower part of the guide.

Check my new guide out.

[http://ubuntuforums.org/showthread.php?t=1097993](http://ubuntuforums.org/showthread.php?t=1097993)

---

