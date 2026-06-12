---
title: "Going MAD, please help with graphic card."
date: 2009-01-11
forum: Hardware
---

### Post by martuschka on 2009-01-11
Its seems that my system did not install my ATI graphic card properly, i dont know what to do.

I have a HP compaq nx8220 (booting ubuntu 8.04 from usb).

My graphic card should be:
horus@horus-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

But watching films is impossible:

horus@horus-laptop:~$ glxgears
376 frames in 5.3 seconds = 71.007 FPS
534 frames in 5.1 seconds = 105.717 FPS
560 frames in 5.1 seconds = 108.990 FPS
560 frames in 5.1 seconds = 109.537 FPS
520 frames in 5.0 seconds = 103.536 FPS
560 frames in 5.1 seconds = 110.525 FPS
540 frames in 5.1 seconds = 106.227 FPS
560 frames in 5.1 seconds = 110.209 FPS
540 frames in 5.0 seconds = 107.004 FPS
520 frames in 5.2 seconds = 100.128 FPS

Here are some of the error messages i have encountered:
horus@horus-laptop:~$ fglrxinfo
display: :1.0 screen: 0
OpenGL vendor string: Mesa project: [http://www.mesa3d.org](http://www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)


When i try to change something (uninstall or install) in ENVY: (see attachments).

[ATTACH]99560[/ATTACH]

[ATTACH]99561[/ATTACH]

Does anyone have any idea what the **** is going on?
I also have no sound, only when headphones are plugged in it works.

Would be sweet if anyone could help.
I need it badly.

---

### Post by cariboo on 2009-01-11
You have to run in a terminal:

```
sudo dpkg --configure -a
```

Like it says in the output, in order to continue. Once you have run the above command you should be able to install the restricted drivers.

Jim

---

### Post by martuschka on 2009-01-12
WOW !!! THANKS !!!

My computer has never been this nice, although now something strange happend, it cant detect the second screen i am using (plugged in ofcourse) and i cant change the screen resolution.

Any more tips?

---

### Post by martuschka on 2009-01-12
horus@horus-laptop:~$ glxgears
2500 frames in 5.0 seconds = 499.502 FPS
2660 frames in 5.0 seconds = 531.602 FPS
2700 frames in 5.0 seconds = 539.479 FPS

beautiful ;)

---

### Post by martuschka on 2009-01-12
Ok Was asble to change screen resolution with a little help from another swedish thread, but now my computer is acting very strange, its all very slow. I dont know whats wrong.

Ideas?

---

### Post by martuschka on 2009-01-12
> **martuschka said:**
> Ok Was asble to change screen resolution with a little help from another swedish thread, but now my computer is acting very strange, its all very slow. I dont know whats wrong.

Ideas?

Not so beautiful

horus@horus-laptop:~$ glxgears
135 frames in 5.6 seconds = 23.946 FPS
100 frames in 5.1 seconds = 19.439 FPS
115 frames in 5.7 seconds = 20.267 FPS
100 frames in 5.2 seconds = 19.239 FPS
120 frames in 5.7 seconds = 20.979 FPS

---

### Post by binbash on 2009-01-12
glxgears is not a performance benchmark tool.Please write down how you change the resolution, also paste the output of glxinfo | grep render

EDIT : you are probably running glxgears command when compiz is on that is why ur getting low frames

---

### Post by martuschka on 2009-01-12
> **binbash said:**
> glxgears is not a performance benchmark tool.Please write down how you change the resolution, also paste the output of glxinfo | grep render

EDIT : you are probably running glxgears command when compiz is on that is why ur getting low frames

This is glxinfo:

horus@horus-laptop:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon



And this is where i changed the graphic card: or chose the ATI mobility radeon, the other screen i use is kind of big; that i have connected to the laptop that is, maby my graphic card does not support it?
HP w2408h  24'monitor   1920x1200

gksu displayconfig-gtk

now i turned of compiz and its a bit better.

horus@horus-laptop:~$ glxgears
558 frames in 5.1 seconds = 109.315 FPS
560 frames in 5.1 seconds = 110.447 FPS
680 frames in 5.1 seconds = 133.647 FPS
680 frames in 5.0 seconds = 135.811 FPS
680 frames in 5.1 seconds = 132.720 FPS

but it was better before i still cant watch movies,
here is some more info:

horus@horus-laptop:~$ top

top - 17:50:21 up 45 min,  2 users,  load average: 0.28, 0.50, 0.54
Tasks: 128 total,   2 running, 125 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.6%us,  1.3%sy,  0.0%ni, 90.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035244k total,   732552k used,   302692k free,    31168k buffers
Swap:  4000176k total,        0k used,  4000176k free,   433532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7492 root      20   0  311m  36m  10m S  2.3  3.6   1:59.33 Xorg               
 7628 horus     20   0 29076  22m 8984 S  1.3  2.2   0:24.94 Xgl                
 7670 horus     20   0 15292 2612 1752 S  0.7  0.3   0:00.50 gnome-screensav    
 8010 horus     20   0  166m  57m  21m S  0.7  5.7   0:14.91 firefox            
 8555 horus     20   0 73196  19m  10m S  0.7  1.9   0:00.34 gnome-terminal     
 8579 horus     20   0  2308 1124  852 R  0.7  0.1   0:00.04 top                
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.28 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 ksoftirqd/0   

Any ideas? ;)

---

### Post by binbash on 2009-01-12
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

you dont have your drivers installed

---

### Post by martuschka on 2009-01-12
> **binbash said:**
> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

you dont have your drivers installed


Enabled the drivers, in the system menu, restarted, ubuntu opened up in low graphics mode, i had to choose screens and then restart again.

But still very low graphics:


334 frames in 5.1 seconds = 65.737 FPS
320 frames in 5.2 seconds = 61.847 FPS
340 frames in 5.3 seconds = 63.670 FPS
340 frames in 5.0 seconds = 67.689 FPS
320 frames in 5.1 seconds = 63.122 FPS

---

### Post by binbash on 2009-01-12
if glxinfo | grep render output says mesa again, you did not enable it.Re-install the drivers

---

### Post by martuschka on 2009-01-12
> **binbash said:**
> if glxinfo | grep render output says mesa again, you did not enable it.Re-install the drivers

Its checked, but the button is red and it says not in use..
hmm weird.

I'll try restarting again.

---

### Post by martuschka on 2009-01-12
K this is where i am now ;)

I restarted, it came up in low graphics mode again, i choose the screens,
my 24 screen that is plugged in to the laptop goes black and the laptop screen gets a very odd resolution that i cant seem to change in the menus.
But there is a green light in the driver menu so it seems to be working.



horus@horus-laptop:~$ glxgears
2518 frames in 5.0 seconds = 503.463 FPS
2660 frames in 5.0 seconds = 528.487 FPS
2660 frames in 5.0 seconds = 530.114 FPS
2640 frames in 5.0 seconds = 527.785 FPS
2660 frames in 5.0 seconds = 531.686 FPS
2641 frames in 5.0 seconds = 525.283 FPS

---

### Post by martuschka on 2009-01-12
> **martuschka said:**
> K this is where i am now ;)

I restarted, it came up in low graphics mode again, i choose the screens,
my 24 screen that is plugged in to the laptop goes black and the laptop screen gets a very odd resolution that i cant seem to change in the menus.
But there is a green light in the driver menu so it seems to be working.



horus@horus-laptop:~$ glxgears
2518 frames in 5.0 seconds = 503.463 FPS
2660 frames in 5.0 seconds = 528.487 FPS
2660 frames in 5.0 seconds = 530.114 FPS
2640 frames in 5.0 seconds = 527.785 FPS
2660 frames in 5.0 seconds = 531.686 FPS
2641 frames in 5.0 seconds = 525.283 FPS

Does anyone know how i change the screen settings?
I have tried everything i dont have any options to choose from in the menu.

---

### Post by chillnet on 2009-01-25
Hi There, 

I've got a similar laptop and I've installed the ATI drivers for Linux, however after I did that I couldn't get my external screen to work anymore. 

I've got nice 3D effects in Gnome now, but no support for an external monitor. 

Any advice on what I can do? 

> glxinfo | grep rendering
direct rendering: Yes


> cat /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


---

