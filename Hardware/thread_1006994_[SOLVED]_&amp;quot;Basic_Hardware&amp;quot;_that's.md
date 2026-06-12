---
title: "[SOLVED] &amp;quot;Basic Hardware&amp;quot; that's Acceptable"
date: 2008-12-09
forum: Hardware
---

### Post by skwon11 on 2008-12-09
Moderator... please feel free to move this if need be...

I run Ubuntu on an old Compaq Presario (Celeron 2.7 GHz, 256 mgs of RAM) and it's been great after switching over from Windows/Mac.  This was 2 years ago.  In that time I've changed out the hard drive (non SATA), but in a DVD burner and added some 500 more mgs of RAM.

But release after release... now I'm starting to feel like Windows... like my computer is really slow.  My question to the forum is... is it the hardware?  Is it just too old?  My needs are basic... multiple web pages up while some other CD/DVD burning or Office like program is running.  But like I said... the computer is starting to feel blah.

I ran puppy linux into memory off a CD (USB drive wouldn't work... my motherboard is too old to boot off one) and it moves like the wind.  But I like Ubuntu and would like to continue using it if at all possible.

My second question is... what to buy?  What I mean is... memory, motherboard and processor that will last me a few years.  Any comments are welcome.  Thank you.

---

### Post by ajmorris on 2008-12-11
strange, with those specs, you should be able to run ubuntu (with the gnome or kde Desktop Environments) quite comfortably...

Can you paste the ouput of the application 'top' (when your computer is running slowly) You will have to run top from a command line, then press ctrl+c to stop it, then copy the output, and paste it here.

Also, it could be your X11 graphics driver, what version of ubuntu are you using, and can you paste the output of:

```
sudo glxinfo
```  (please put [CODE] envelops around the glxinfo output, as it will be quite long.


AJ

---

### Post by iggykoopa on 2008-12-11
you might want to look into crunchbang linux, it's still ubuntu based but it may run a little faster for you. The link is here [http://crunchbang.org/](http://crunchbang.org/) . It uses openbox for the window manager and is really well done.

---

### Post by skwon11 on 2008-12-11
I'm running 8.04

As requested

```
[skwon11@skwon11-desktop:~$ sudo glxinfo
[sudo] password for skwon11: 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
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
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
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
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

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
0x5e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
skwon11@skwon11-desktop:~$ 
```

---

### Post by markbuntu on 2008-12-11
Put the system monitor on your panel and watch if the cpu or memory is maxing out on a regular basis. Check if turning off the desktop visual effects makes a difference, it usually does for a machine like yours because compiz uses huge resources. 

But anyway, besides that the machine should be fine for running Ubuntu.

---

### Post by ajmorris on 2008-12-11
you're using the 'mesa' X11 graphics driver, so if you have desktop effects or composite effects active, you will experience an overall slow system. You could also try out some of the WMs in the ubuntu repos, such as fluxbox or openbox.


AJ

---

### Post by skwon11 on 2008-12-12
I've installed Fluxbox (which I like... very simple... no frills) and although speeds seem better overall... my hangups are always with multiple tabs/windows open in any web browser.  I realize and agree Ubuntu can work on almost anything... but could it just be my old graphics card (or lack thereof) combined with my non SATA drive?  I'll try X and some other WM's.  Thanks for your help.

---

### Post by ajmorris on 2008-12-14
> **skwon11 said:**
> I've installed Fluxbox (which I like... very simple... no frills) and although speeds seem better overall... my hangups are always with multiple tabs/windows open in any web browser.  I realize and agree Ubuntu can work on almost anything... but could it just be my old graphics card (or lack thereof) combined with my non SATA drive?  I'll try X and some other WM's.  Thanks for your help.

what sort of hangups? I.e do your 'lock' keys (caps lock etc.) flash, or is it just a system hang?

Can you please paste your /var/log/syslog and /var/log/messages files (please use [CODE] envelops as they are very long)

AJ

---

### Post by kerry_s on 2008-12-14
> **skwon11 said:**
> I've installed Fluxbox (which I like... very simple... no frills) and although speeds seem better overall... my hangups are always with multiple tabs/windows open in any web browser.  I realize and agree Ubuntu can work on almost anything... but could it just be my old graphics card (or lack thereof) combined with my non SATA drive?  I'll try X and some other WM's.  Thanks for your help.

you should try the ubuntu custom install, building up from the base with only what you use.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

i use a custom debian lenny on 450mhz 256mb ram, it's a 10 year old laptop, nothing is slow on mine.

---

### Post by skwon11 on 2008-12-14
No... lights don't go flashing... the system just hangs... epiphany seems to have less hang ups... as requested...

```
skwon11@skwon11-desktop:~$ tail -n 500 /var/log/syslog
Dec 14 08:01:24 skwon11-desktop syslogd 1.5.0#1ubuntu1: restart.
Dec 14 08:01:24 skwon11-desktop anacron[21706]: Job `cron.daily' terminated
Dec 14 08:01:24 skwon11-desktop anacron[21706]: Job `cron.weekly' started
Dec 14 08:01:24 skwon11-desktop anacron[21856]: Updated timestamp for job `cron.weekly' to 2008-12-14
Dec 14 08:01:27 skwon11-desktop syslogd 1.5.0#1ubuntu1: restart.
Dec 14 08:01:27 skwon11-desktop anacron[21706]: Job `cron.weekly' terminated
Dec 14 08:01:27 skwon11-desktop anacron[21706]: Normal exit (2 jobs run)
Dec 14 08:17:01 skwon11-desktop /USR/SBIN/CRON[22039]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 08:42:56 skwon11-desktop -- MARK --
Dec 14 09:02:56 skwon11-desktop -- MARK --
Dec 14 09:17:01 skwon11-desktop /USR/SBIN/CRON[22044]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 09:42:56 skwon11-desktop -- MARK --
Dec 14 10:02:56 skwon11-desktop -- MARK --
Dec 14 10:17:01 skwon11-desktop /USR/SBIN/CRON[22050]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 10:42:56 skwon11-desktop -- MARK --
Dec 14 11:02:56 skwon11-desktop -- MARK --
Dec 14 11:17:01 skwon11-desktop /USR/SBIN/CRON[22054]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 11:42:56 skwon11-desktop -- MARK --
Dec 14 12:02:56 skwon11-desktop -- MARK --
Dec 14 12:17:01 skwon11-desktop /USR/SBIN/CRON[22057]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 12:42:56 skwon11-desktop -- MARK --
Dec 14 13:02:56 skwon11-desktop -- MARK --
Dec 14 13:17:01 skwon11-desktop /USR/SBIN/CRON[22060]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 13:42:56 skwon11-desktop -- MARK --
Dec 14 14:02:57 skwon11-desktop -- MARK --
Dec 14 14:17:01 skwon11-desktop /USR/SBIN/CRON[22063]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 14:42:57 skwon11-desktop -- MARK --
Dec 14 15:02:57 skwon11-desktop -- MARK --
skwon11@skwon11-desktop:~$ tail -n 500 /var/log/messages
Dec 14 08:01:27 skwon11-desktop syslogd 1.5.0#1ubuntu1: restart.
Dec 14 08:22:56 skwon11-desktop -- MARK --
Dec 14 08:42:56 skwon11-desktop -- MARK --
Dec 14 09:02:56 skwon11-desktop -- MARK --
Dec 14 09:22:56 skwon11-desktop -- MARK --
Dec 14 09:42:56 skwon11-desktop -- MARK --
Dec 14 10:02:56 skwon11-desktop -- MARK --
Dec 14 10:22:56 skwon11-desktop -- MARK --
Dec 14 10:42:56 skwon11-desktop -- MARK --
Dec 14 11:02:56 skwon11-desktop -- MARK --
Dec 14 11:22:56 skwon11-desktop -- MARK --
Dec 14 11:42:56 skwon11-desktop -- MARK --
Dec 14 12:02:56 skwon11-desktop -- MARK --
Dec 14 12:22:56 skwon11-desktop -- MARK --
Dec 14 12:42:56 skwon11-desktop -- MARK --
Dec 14 13:02:56 skwon11-desktop -- MARK --
Dec 14 13:22:56 skwon11-desktop -- MARK --
Dec 14 13:42:56 skwon11-desktop -- MARK --
Dec 14 14:02:57 skwon11-desktop -- MARK --
Dec 14 14:22:57 skwon11-desktop -- MARK --
Dec 14 14:42:57 skwon11-desktop -- MARK --
Dec 14 15:02:57 skwon11-desktop -- MARK --

```

---

### Post by skwon11 on 2008-12-14
On another note... I just wanted to see out of curiosity how much memory my system is using with Epiphany open and the Terminal open as well... can anybody tell me... why so much?

```
skwon11@skwon11-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           749        646        103          0         62        172
-/+ buffers/cache:        410        338
Swap:         2196         97       2099
```

---

