---
title: "compiz crash on alt-tab"
date: 2009-01-24
forum: Hardware
---

### Post by xdevnull on 2009-01-24
on my averatec 1050 which has an 855GM video card compiz keeps crashing, which is irritating, because it has been rock solid in previous ubuntus.  I'm using 8.10.

Basically, when I alt-tab and switch to a window on another desktop (not another monitor) compiz crashes to metacity and piles all my apps on desktop one.  I then either restart X, which restarts compiz or use this little compiz-fusion tray icon which lets me switch between managers.

Anyway.  Sometimes compiz just crashes, though it's hard to nail down what might be happening.  The alt-tab makes it crash everytime.

I can't figure out which video-driver I'm actually using.  With the changes to xorg.conf I'm not sure how to find out or make changes.

Any help?

---

### Post by ajmorris on 2009-01-25
hi there,
to check what X11 driver you are using, you can run ```
sudo glxinfo
```(if you cant see what driver you are using, paste your glxinfo output here also (with ```
 envelops as it is long) and i can tell you :))

in order to try to debug your compiz issue, run compiz from a terminal:
[CODE]compiz --replace
```

then use alt+tab and paste the whole output from your terminal when compiz crashes.


AJ

---

### Post by xdevnull on 2009-01-28
Thanks for the info.  I'm assuming this is the relevant stuff from glxinfo:

```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061102 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.2

```

I'm assuming this means I'm using the Mesa Driver?  Which is the suckiest?  So how would I get it to use the i810/910 or the more usual driver?

Let me know if I'm totally off base and should go ahead and post the crash data or more from glxinfo.

Thanks again for the help.

---

### Post by ajmorris on 2009-01-29
heh, ok, now this is where it gets a bit iffy. The X configuration in intrepid has kinda been ruined lately, and needs fixing. It is basically running off a complete automatic detection via HAL, so it seems that HAL has not correctly detected and configured your card. Firstly, make sure that your have the i810 graphics drivers installed:
```
sudo apt-get install xserver-xorg-video-i810
``` 
you could also try:
```
sudo apt-get install xserver-xorg-intel
``` If a restart of X, does not configure X with the new intel driver, check in the restricted hardware tool in your menus. If this doesnt work, short of manually configuring entries in /etc/X11/xorg.conf to add a driver for your video card, i think your only option is running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Hopefully that will give you the option to change your display driver.


AJ

---

### Post by xdevnull on 2009-07-07
So I was hoping this would go away with Jaunty, but no such luck (though I do find it faster).  Don't get the crash as often, but I still easily recreate it when I use alt-tab between apps on different workspaces.  If they are on the same workspace, it's fine, but if on different ones - crash.

```
glxinfo:
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 

```

Then lots of tables:

Here's the output of running compiz --replace from the command line

```
bg@slim:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1360x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
I/O warning : failed to load external entity "/home/bg/.compiz/session/10d4997a0df9d4d058124700326723270800000029550004"
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

And after I alt-tab..
```
Segmentation fault
Window manager warning: Failed to read saved session file /home/bg/.config/metacity/sessions/10d4997a0df9d4d058124700326723270800000029550004.ms: Failed to open file '/home/bg/.config/metacity/sessions/10d4997a0df9d4d058124700326723270800000029550004.ms': No such file or directory

```

I hope this is helpful in some way to figuring out why compiz crashes in this one instance.

It will sometimes crash when I am closing a big program (read open-office) and switch to a different workspace before it is completely closed.  I have also noticed that in this version and the previous I think compiz or maybe X is crashing during shutdown.  Basically my computer would hang and not actually shutdown (not fun if you don't notice and put the laptop in a bag for a couple of hours).  

When I upgraded to jaunty I noticed that the hang would happen before the ubuntu spalsh-shutdown graphic would come up, and occasionally happened when I was logining off, not just shutting down.  So that is a bit of a pain.

Anyway - any help would be appreciated.

---

