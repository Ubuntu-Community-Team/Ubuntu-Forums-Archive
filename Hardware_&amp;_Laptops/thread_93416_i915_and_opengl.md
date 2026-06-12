---
title: "i915 and opengl"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by no1wantdthisname on 2005-11-22
**EDIT: Got it to work.  Check page 2 for fix.**

I have a Sony vaio vgn fs640 and have been trying to get warcraft III to run, but nothing seems to work.  
Using a fresh install:
glxinfo shows dri is working
dmesg shows no errors.  drm was loaded correctly.
lsmod shows agpgart and i915 were loaded.
no errors in xorg.log

When I run warcraft III with -opengl, a black screen shows up, and sometimes the laptop freezes.
Another problem is that sometimes when using xv in video players I see distorted colors or the picture is too bright. 
Running opengl fixes the color, but sometimes half of the picture is cut off.  I have to resize the video to fix.   

So I decided to test other distros to see if this problem shows up.  Suse 10.0 and regular debian works perfectly for Warcraft III, but I've gottten used to Ubuntu and don't really want to switch.  The video bug mentioned before still exists in Suse (haven't tested in debian yet), but I don't really care about resizing a window to fix it. 

So, I tested a bunch of different things.
**Using kernel 2.6.12, I tried drivers from dri.freedesktop:** dri worked on some drivers, but same problem as before.  The black screen despite working dri from glxinfo.
**Compiled kernel 2.6.14:** broken dri.  After some tweaking, dri worked, but again, the black screen.
**Compiled drivers from dri.freedesktop on 2.6.14:** black screen again.
**Compiled entire X.org to 6.9rc2 on kernel 2.6.12:** black screen and sometimes broken graphics.  Also tried drivers from dri.freedesktop.  I was able to get an image in war3, but dri wasn't working, so extremely slow.  After upgrading using other dri.freedesktop snapshots, I got dri back, and tuxracer worked.  The black screen returned though.
**Compiled entire X.org to 6.9rc2 on kernel 2.6.14:** pretty much same as when I compiled on 2.6.12.  The only error I see is that GLcore failed to load.  dri is still working though.  tuxracer doesn't work anymore
**Upgraded wine to the newest from winehq.com on the different kernels and different X.org:** Same problem.  .
**Tried using parts of xorg.conf from debian and suse:** no difference.
**Tried using 915resolution:** no difference.
**Upgraded to dapper and tried everything mentioned above:** same problems and more.

I don't understand what the problem is.  I upgraded the kernel, x.org, wine, and tried a variety of other things, and still it doesn't work.  The fact that it works perfectly on debian is even more confusing.  :???:

So, any solutions or suggestions?  I'm running out of ideas.

---

### Post by Burkey on 2005-11-25
I am in the same situation.. and to make it even worse, it worked fine on Hoary for me.

I just done a fresh install of Breezy Ubuntu in hopes that my Kubuntu Breezy pre-release had a bug... no good.

Actually the process that happened before was..

Enemy Territory would only use 800x600 and would not switch to full screen, would be in the bottom left corner instead.

After adding some Horiz and Vert refresh settings to xorg.conf it started just going black-screen (but working, I can open console and quit fine, and see no errors)

---

### Post by tflovik on 2005-11-26
If you want 3d to work properly on i915 you have to switch to SuseLinux 10. I'm running the OSS version and et works in all resolutions. In Breezy i got only sound and a black screen.

---

### Post by no1wantdthisname on 2005-11-26
Yeah, I know Suse 10.0 works.  Debian unstable works as well.  
There's a lot of other things that bother me about those distros though.  
Debian doesn't have network-manager and I just don't like Suse's package system or the fact that it's kde.  Suse has gnome of course, but the centralized management system depends on using kde.  

I went ahead and tried gentoo, and after many hours of compiling Xorg and kernels, it still doesn't work.  So yeah, any solutions?

Where could the problem possibly be?  Is it X.org, the kernel, wine, or possibly something else?:confused:

---

### Post by MetalMusicAddict on 2005-11-26
[QUOTE=tflovik]If you want 3d to work properly on i915 you have to switch to SuseLinux 10. I'm running the OSS version and et works in all resolutions. In Breezy i got only sound and a black screen.[/QUOTE]
Could you post your xorg?

---

### Post by Burkey on 2005-11-26
Could you also please post the output of glxinfo and some info on you're hardware.

The black screen problem I am pretty sure is related to screen refresh rates or sync rates on LCD's.

I used to be a KDE man, and purchases SuSE, however I am becoming more and more comfortable with Ubuntu now and do not want to switch... however, if I cannot get OpenGL to work right then I will be forced to, not just for World of Warcraft and Enemy Territory but for my own OpenGL programming projects.

---

### Post by no1wantdthisname on 2005-11-27
Eh I don't think it's because of screen refresh.  Debian works perfectly.  I'm using the same xorg.conf file as debian, except for the font paths.  It still shows a black screen.

---

### Post by tflovik on 2005-11-27
I'm using a Dell Inspiron 6000 with the i915 graphics.

Here's the output from glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

Here's my xorg.conf:

# /.../
# SaX generated X11 config file
# Created on: 2005-11-25T18:43:53+0100.
#
# Version: 7.1
# Contact: Marcus Schaefer <sax@suse.de>, 2002
#
# Automatically generated by [ISaX] (7.1)
# PLEASE DO NOT EDIT THIS FILE!
#

Section "Files"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/local"
  FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/URW"
  FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
  FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
  FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/baekmuk:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/japanese:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/kwintv"
  FontPath     "/usr/X11R6/lib/X11/fonts/truetype"
  FontPath     "/usr/X11R6/lib/X11/fonts/uni:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/CID"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc/sgi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/ttyS0"
  InputDevices "/dev/ttyS1"
  InputDevices "/dev/ttyS2"
  InputDevices "/dev/ttyS3"
  InputDevices "/dev/ttyS4"
  InputDevices "/dev/ttyS5"
  InputDevices "/dev/ttyS6"
  InputDevices "/dev/ttyS7"
  InputDevices "/dev/ttyS8"
  InputDevices "/dev/psaux"
  InputDevices "/dev/logibm"
  InputDevices "/dev/sunmouse"
  InputDevices "/dev/atibm"
  InputDevices "/dev/amigamouse"
  InputDevices "/dev/atarimouse"
  InputDevices "/dev/inportbm"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/mouse"
  InputDevices "/dev/usbmouse"
  InputDevices "/dev/adbmouse"
  InputDevices "/dev/input/mice"
  InputDevices "/dev/input/event0"
  InputDevices "/dev/pointer0"
  InputDevices "/dev/pointer1"
  InputDevices "/dev/pointer2"
  InputDevices "/dev/pointer3"
EndSection

Section "ServerFlags"
  Option       "AllowMouseOpenFail"
EndSection

Section "Module"
  Load         "glx"
  Load         "type1"
  Load         "extmod"
  Load         "dbe"
  Load         "freetype"
  Load         "v4l"
  Load         "dri"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "no"
  Option       "XkbModel" "pc104"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "PS/2 Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
  Option       "AccelFactor" "0.1"
  Option       "BottomEdge" "650"
  Option       "CircScrollDelta" "0.1"
  Option       "CircScrollTrigger" "2"
  Option       "CircularScrolling" "1"
  Option       "Device" "/dev/input/mice"
  Option       "EdgeMotionMaxSpeed" "15"
  Option       "EdgeMotionMinSpeed" "15"
  Option       "Emulate3Buttons" "on"
  Option       "EmulateMidButtonTime" "75"
  Option       "FingerHigh" "15"
  Option       "FingerLow" "14"
  Option       "HorizScrollDelta" "20"
  Option       "InputFashion" "Mouse"
  Option       "LeftEdge" "120"
  Option       "MaxSpeed" "1"
  Option       "MaxTapMove" "110"
  Option       "MaxTapTime" "180"
  Option       "MinSpeed" "0.2"
  Option       "Name" "ALPS;Touchpad"
  Option       "Protocol" "auto-dev"
  Option       "RightEdge" "830"
  Option       "SHMConfig" "on"
  Option       "TopEdge" "120"
  Option       "UpDownScrolling" "1"
  Option       "Vendor" "Sysp"
  Option       "VertScrollDelta" "20"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  Option       "CalcAlgorithm" "XServerPool"
  DisplaySize  332 207
  HorizSync    31-100
  Identifier   "Monitor[0]"
  ModelName    "H4700154P1 MONITOR"
  Option       "DPMS"
  VendorName   "SEC"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "915 GM"
  BusID        "0:2:0"
  Driver       "i810"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "Intel"
EndSection


Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
EndSection

Hope this can be of help for you!

---

### Post by Burkey on 2005-11-27
First obvious differences..

You're glxinfo
```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.2.1

```

Mine
```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2

```

So it seems my openGL renderer is newer?  But maybe bugged?

---

### Post by Burkey on 2005-11-28
Updated to latest DRI snapshots.. now I have

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

But nothing else changed, Enemy Territory still gives a black screen with the music goind and able to exit with '~' and quit, World of Warcraft still frightfully slow.

---

### Post by no1wantdthisname on 2005-11-28
I've already tried different kernels, X.org 6.9, the dri snapshots, different versions of wine, and different x.org config files. 

Nothing works.  It has to be another problem.

---

### Post by Burkey on 2005-11-28
Yes, but I post the glxinfo output to hopefully help anyone who may read this and wants to help.

It is very frustrating.

---

### Post by no1wantdthisname on 2005-11-30
Went ahead and tried more things.  I got nothing.  I'm about to give up.

No ideas, huh?...

---

### Post by CarbonPlexus on 2005-12-11
My WoW is also frightfully slow.  I'm a newbie with linux though so I really don't know how to fix it.  Here's my glxinfo in case it helps.

> name of display: :0.0
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


---

### Post by anil_robo on 2005-12-18
I want to play DiabloII:LOD in Ubuntu so that I can dump WIndows XP for ever. I have installed wine and also diablo2, but when I run video configuration utility supplied with diabloII, it says "no graphics hardware found". I have configured wine properly (winecfg) as detailed in a how-to for diabloII. However, when I try to run diabloII using wine, lots of errors come up. I am attaching my system configuration files as well as error output with this post. Please help. Thanks!
[ATTACH]4632[/ATTACH] [ATTACH]4633[/ATTACH] [ATTACH]4634[/ATTACH] [ATTACH]4635[/ATTACH]

---

### Post by no1wantdthisname on 2006-01-08
FINALLY..

I got it to work.

After many tries, war3 finally runs.  

From fresh install, I used the dri snapshot of 20060107 from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).

EDIT: This seems to have fixed some other problems that I had in suse and debian as well.
War3 no longer freezes if I alt tab.  
Video players still freeze if I use opengl for video though.  This is easily fixed by switching to xv.

---

### Post by no1wantdthisname on 2006-02-04
Someone asked me how I installed it so here it is.

To install the dri snapshot you need to go to [http://www.ubuntuforums.org/showthread.php?t=93416&highlight=915gm](http://www.ubuntuforums.org/showthread.php?t=93416&highlight=915gm) and download one of the common and the i915 archives.  Just get the latest dated ones.  Then unpack both archives.  I would recommend that you first
```
sudo apt-get install unp
```
and then just
```
unp (archives)
```
in a terminal.  This just seems much easier than having to type that tar -zxvf command to unpack it.

Enter the common directory and 
```
sudo sh install.sh
```
After that finishes, go to the other directory and
```
sudo sh install.sh
``` 
again.  One small note, I seem to have trouble compling the i915 modules.  Try a different kernel, the 386 or 686 one.  I don't exactly remember, but I think I had to compile my own kernel just to get it to work.  I downloaded a 2.6.15 kernel from [www.kernel.org](www.kernel.org).
There's a guide to compiliing kernels on the tips and tricks page if needed that goes through the process.

---

