---
title: "Direct Rendering and Intel x3100"
date: 2008-11-18
forum: Hardware
---

### Post by jimreynold2nd on 2008-11-18
Hi guys,

Ubuntuforums have been really helpful in the past, so helpful that I didnt even have to post anything, just google and help came. But this time I got no luck...

I have a ThinkPad T61 with Intel graphic (GMA965 or x3100).
I have been trying to run [Stepmania]("http://www.stepmania.com/") with no luck. it said that  (look at bottom of the output where it says no direct rendering);
```
StepMania 3.9
Log starting 2008-11-18 12:31:14
Loading window: gtk
OS: Linux ver 020624
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.7
Threads library: NPTL 2.7
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
ALSA Driver: 0: HDA Intel [Intel], device 0: AD198x Analog [AD198x Analog], 1/1 subdevices avail
ALSA Driver: 0: HDA Intel [Intel], device 1: AD198x Digital [AD198x Digital], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 44100hz
Sound driver: ALSA-sw

(stepmania:7826): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
SDL version: 1.2.12
Got 32 bpp (8888), 24 depth, 8 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: Tungsten Graphics, Inc
OGL Renderer: Mesa DRI Intel(R) 965GM 4.1.3002
OGL Version: 1.4 Mesa 7.0.3-rc2
OGL Extensions: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays 
OGL Max texture size: 2048
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: no
X server vendor: The X.Org Foundation [1.4.0.90]
Server GLX vendor: SGI [1.2]
Client GLX vendor: SGI [1.4]
Mixing 465.484123 ahead in 1795 Mix() calls
Language: english
Current renderer: OpenGL
Theme: default
Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
**[COLOR="Red"]Your system is reporting that direct rendering is not available.[/COLOR]**  Please obtain an updated driver from your video card manufacturer.

```

```

glxinfo outputs: 
name of display: :0.0
display: :0  screen: 0
**[COLOR="Red"]direct rendering: No[/COLOR]** (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
..............
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:
..............

```

When I did ```
sudo displayconfig-gtk
``` I saw that the driver being used is mesa and not intel. I tried to change the driver to 'intel' but after I reboot it got changed back to mesa.

This is weird because I have CompizFusion running smoothly with a lot of effects on. glxgears is 1000+ windowed (default) and around 130fps maximized. HD video (mkv) plays smoothly with compiz on too.

I tried all ideas in [http://ubuntuforums.org/showthread.php?t=843052&highlight=x3100+direct]("http://ubuntuforums.org/showthread.php?t=843052&highlight=x3100+direct") and [http://ubuntuforums.org/showthread.php?t=583081]("http://ubuntuforums.org/showthread.php?t=583081") but still no help

EDIT: I am running Hardy 64bit, kernel 2.6.24-21-generic (which is latest for hardy), with all updates. Google Earth runs without direct rendering flickers whenever I click the mouse but is usable.

Any idea?
Thanks

---

### Post by jimreynold2nd on 2008-11-19
UPDATE:
This is getting weird. I did a fresh install of Kubuntu, KWin and its effects work, though not as smoothly as compiz's but usable (i.e. not as slow as with an nvidia card).
This time, glxinfo shows "direct rendering: yes" but I still cannot play stepmania, it kept saying that I don't have direct rendering (note that stepmania works on XP and on my desktop computer which uses a 9500GT and Hardy).
I attached output of glxinfo in kubuntu for you guys to look at.

---

### Post by jimreynold2nd on 2008-11-20
UPDATE:
Kubuntu doesn't have this problem: Direct Rendering is yes in glxinfo, KWin effect is good, mkv HD video in fullscreen with Kwin is smooth and is composited (i.e. "video on cube face" analogy), BUT stepmania doesn't run no matter whether KWin composition is on or off - it keeps saying that I don't have direct rendering. Besides, DEFCON crashes KDE. (It doesn't crash compiz in gnome)
:confused:
What is going on here?

---

### Post by jimreynold2nd on 2008-11-21
uhh... bump?

---

### Post by jimreynold2nd on 2008-11-21
Hmm.. .this problem is rarer than I thought... I found a couple of posts on google but no real solution. Might as well wait for some update

---

### Post by jimreynold2nd on 2008-11-23
bump?

---

### Post by jimreynold2nd on 2008-12-02
hmm... bump again o.o

---

### Post by logari81 on 2008-12-13
How did you open the terminal in which you run glxinfo?

Ensure that you have done it over the menu Applications--Accessories--Terminal. It sounds silly but if you start a terminal using an accelerator (key shortcut) the environment variable LIBGL_ALWAYS_INDIRECT is set to 1 and glxinfo gives the false output.

---

### Post by _serenity on 2008-12-16
Do you have the following in your /etc/X11/xorg.conf? If not, try to add it. 

```

Section "DRI"
   Mode 0666
EndSection

```

---

