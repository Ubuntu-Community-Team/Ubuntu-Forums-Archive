---
title: "graphics drivers and tweaks for old Intel chips/cards"
date: 2014-06-20
forum: Hardware
---

### Post by squakie on 2014-06-20
[Moved to a separate thread focusing on old Intel graphics]

I know that was one of the things I mentioned, but......I don't know how to update mine ;)   How did you update to a newer version of opengl?

Thanks!

---

### Post by sudodus on 2014-06-20
I think it comes with the graphics driver. A proprietary driver might have a higher version number. A newer Ubuntu version might to have a higher version number.

---

### Post by squakie on 2014-06-20
I may by out of luck......I ruined my 4 month old laptop and it's not covered by the warranty, so I'm using an OLD laptop that has Intel 900/910 graphics.  The laptop has xubuntu 14.04 with what seems to be the latest xorg file for the graphics and additional drivers comes up empty.  Do you know if there is somewhere I might be able to grab a driver for graphics this old that has OpenGL 2?  The Intel site really does say much for their Linux support.

Thanks!

---

### Post by sudodus on 2014-06-20
I'm not sure you can get any good graphics with it. Maybe it helps a little with UXA acceleration according to

> John Hupp <lubuntu@prpcompany.com> wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format, should be a tab before each line except the first and the last).

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```
Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.

-o-

Nio Wiklund wrote:

This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.


---

### Post by sudodus on 2014-06-20
@squakie,                        

By the way, I [s]think we should make[/s] made a new thread for you about this issue.

---

### Post by squakie on 2014-06-20
Woops - just saw you actually created the new thread, so I can skip doing so ;)

An update:  I downloaded the newest deb from the Intel site for the Intel Linux graphics driver.  The deb installed via the Software Center, and then I rebooted.  glxinfo still shows OpenGL at version 1.4 ;(

Is it possible to download and build the OpenGL 2.0 source from mesa or sgi and some how build it into the driver?

I think it's actually a 910/915 adapter as well.  The glxinfo is showing 915.

---

### Post by squakie on 2014-06-20
I did find that the mesa site had a newer set of downloads to get OpenGL2, etc..  I downloaded and extracted the files, but the make fails.  Went back to the [instructions]("http://www.mesa3d.org/install.html") and found there are 3 things that need to be on my system but aren't in the repos.  Can someone take a look at those instructions and see if it should be safe, in xubuntu 14.04, to download and install them?  I *really* don't want to mess up my current installation ;)

EDIT:  The libxml-python shows as an exe file, so I didn't download it.  I downloaded the newest dri2proto-2.8.  I was able to configure, but make said nothing to make.  I then did sudo make install and it did something, so I guess that's what I needed there.  I then downloaded libdrm-2.4.54.  When I try to configure, I get this error:```
checking for PTHREADSTUBS... no
configure: error: Package requirements (pthread-stubs) were not met:

No package 'pthread-stubs' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PTHREADSTUBS_CFLAGS
and PTHREADSTUBS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
me@oldlap:~/Downloads/libdrm-2.4.54$ .
```

I have no idea what pthread-stubs is or where to get it.  

So I got around the dri2proto problem in config by downloading and installing the driproto .deb.  The config now fails because of the libdrm "stuff", that's why I downloaded the libdrm .deb file and tried to configure it so I could make and make install.

Any ideas on this would be greatly appreciated.

---

### Post by Yellow Pasque on 2014-06-20
The default driver should give OpenGL 2.x: [http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTA](http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTA)

Can you give output of glxinfo?:
```
glxinfo
```

Note that building your own mesa is not fun and probably not what you really want to do (you can get most recent mesa from xorg-edgers or oibaf PPA). If you are going to have a go at it, you need appropriate -dev packages (like libpthread-stubs0-dev). In general, this will help:
```
sudo apt-get build-dep mesa
```

---

### Post by squakie on 2014-06-20
Well, a few steps further:

- in package manger, installed libpthread-stubs0-dev, libevent-pthread-2.0-5, libpthread-workqueue-dev and libpthread-workqueue0

The configure then went further but said glproto wasn't installed.

- in package manager, installed x11proto-gl-dev

Then configure went a litle further and then said libdrm >= 2.4.38 required.

Back to trying to figure that out.

It would have been EXTREMELY nice of Mesa to post somewhere the instructions for Ubuntu - install xxxx packages, etc..

---

### Post by Yellow Pasque on 2014-06-20
Again, you need the **-dev** packages. Still, building your own mesa is not a good idea because it will interfere with the packaged version and probably not have intended effect. Give output of glxinfo.

---

### Post by squakie on 2014-06-20
Ok, had to install libdrm-dev to get around that error.

Then configure errored out on needing dri3proto.

Installed x11proto-dri3-dev via the package manager.

Then configure errored out on presentproto.

Installed x11proto-present-dev via the package manager.

Now I get this mess:```
configure: error: Package requirements (x11 xext xdamage xfixes x11-xcb xcb-glx >= 1.8.1 xcb-dri2 >= 1.8 xcb-dri3 xcb-present xcb-sync xshmfence >= 1.1) were not met:

No package 'x11' found
No package 'xext' found
No package 'xdamage' found
No package 'xfixes' found
No package 'x11-xcb' found
No package 'xcb-glx' found
No package 'xcb-dri2' found
No package 'xcb-dri3' found
No package 'xcb-present' found
No package 'xcb-sync' found
No package 'xshmfence' found
```

so now I get to go hunting again and see if I can figure all of those out.  oh how I wish Mesa had shown the dependencies for all this (I suppose I missed them somewhere).

---

### Post by Yellow Pasque on 2014-06-20
```
sudo apt-get build-dep mesa
```

---

### Post by squakie on 2014-06-20
Trying with just having installed x11proto-xext-dev via the package manager.

Didn't change the error message - so while the package said xext - it isn't the one needed.

Back to more hunting.

Installing libx11-dev via package manager.

That only removed x11 from the error message.


Sorry this is getting like this - I'm trying to document what I am doing as I go along in case I miss something.   Hopefully I'll get this configure to work, at which time I'll create a summary for it.

Installing x11proto-damage-dev via package manager.  Didn't fix the xdamage in the error message. 
Installing libxdamage-dev via package manager - package manager gives fatal errors, not sure what to do now.

---

### Post by squakie on 2014-06-20
> **Temüjin said:**
> ```
sudo apt-get build-dep mesa
```

I don't know why I didn't think of that on the mesa package - I guess I was too caught up in what I downloaded.  At any rate, that did get rid of that string of error messages.

Now on to the newest:  libdrm_radeon >= 2.4.54.  The one in the repos is installed, but it's only 2.4.52.  Guess I need to see if I can find 2.4.54 somewhere on the net.

Downloaded libdrm-radeon1 (= 2.4.54-1 from packages/debian.org/sid/libdrm-dev) and opened it software center - gives an error saying it would break dependencies on the installed libdrm-radeon1 at 2.4.52.

Well, I'm out of my knowledge base by a LONG way now.  I'll need some guidance on whether or not there's a way to get around this error.  If not, then I'm hosed.

Thanks Temujin for the input!

---

### Post by squakie on 2014-06-21
> **Temüjin said:**
> The default driver should give OpenGL 2.x: [http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTA](http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTA)

Can you give output of glxinfo?:
```
glxinfo
```

Note that building your own mesa is not fun and probably not what you really want to do (you can get most recent mesa from xorg-edgers or oibaf PPA). If you are going to have a go at it, you need appropriate -dev packages (like libpthread-stubs0-dev). In general, this will help:
```
sudo apt-get build-dep mesa
```

Sorry - I got so busy working on it that I didn't see this earlier.  I looked at that link, but they don't say where to get the driver.  I already downloaded the latest from Intel.

here's the glxinfo:```
me@oldlap:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 915GM x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 10.1.3
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_shader_trinary_minmax, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_object_purgeable, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_clear_buffer_object, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_storage, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_vertex_array, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

12 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x079 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x061 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x064 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x067 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x069  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x072  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x073 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x074 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

me@oldlap:~$ 
```

Right now I'm stuck at needing the new lib but the software center won't let me install as it says there are other packages dependent on the old version.

I also found something in system settings about installing intel graphics driver.  I clicked on that and it took quite a while - said it was downloading the latest driver, then installing it.  I've rebooted since but it still show glx at 1.4

---

### Post by squakie on 2014-06-26
bump

---

### Post by Yellow Pasque on 2014-06-28
As I said earlier:
> Note that building your own mesa is not fun and probably not what you really want to do (you can get most recent mesa from xorg-edgers or oibaf PPA).

If xorg-edgers PPA doesn't give you OpenGL 2.x, then building your own mesa isn't going to help...

---

### Post by Frogs Hair on 2014-06-28
Closed per OP request .

---

