---
title: "[SOLVED] No Desktop effects - Not the usual issue."
date: 2008-11-12
forum: General Help
---

### Post by pdescham49 on 2008-11-12
Hi all, I hope someone can point me in the general direction here. 

[LIST]
[*]Clean Install intrepid
[*]Installed Nvidia 177.80 driver
[*]Installed CCSM
[*]Installed Emerald
[*]I had emerald / Compiz CCSM working beautifully.
[*]Started to DL install different themes / screenlets looking awesome
[*]Desktop 3d Cube works, Wicked. everything was perfect. 
[*]I went into System->Preferences->Appearence Then to the Visual Effects tab
[*]Noticed no raido button was selected so I then clicked on "extra"
[*]KABOOM no more effects
[/LIST]

Now when I try to enable the desktop effects I get a message "Desktop Effects Could not be enabled"

if i run: 
compiz --replace

i get this: 

```
$ compiz -- replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```


Xgl not present. 

so then i tried:

```
$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

```

check for nvidia-glx-177

```
$ sudo apt-get install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-177 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Here's my Xorg.conf

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

glxinfo
```
glxinfo | more
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, 
    GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro NVS 110M/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.80
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 

```

Any assistance is greatly appreciated.

---

### Post by pdescham49 on 2008-11-12
Ok here's what i did already since no-one has yet replied :( 

[LIST]
[*]reinstalled nvidia 177.80 driver
[*]reinstalled compiz
[*]removed emerald
[*]installed Fusion.icon
[/LIST]

---

### Post by eternalnewbee on 2008-11-12
> Ok here's what i did already since no-one has yet replied

    * reinstalled nvidia 177.80 driver
    * reinstalled compiz
    * removed emerald
    * installed Fusion.icon

Hi pdescham49.
Did it work?

---

### Post by pdescham49 on 2008-11-12
nope.

---

### Post by spinstartshere on 2008-11-12
I was having a problem with desktop effects, but I don't know if it's the same problem as I have completely different hardware.  Are there still some visible effects when you have Compiz disabled, such as shadows under menus or thumbnail previews when you Alt-Tab?

---

### Post by pdescham49 on 2008-11-12
Yes with out compiz running you still get "drop shadows" when you have selected "none" in System->Preferences->appearence and "visual effects"

---

### Post by spinstartshere on 2008-11-12
Open the Configuration Editor (Alt-F2 and run "gconf-editor") and untick /apps/metacity/general/compositing_manager, then try enabling Compiz effects again.  I *think* this fixed it for me, but I'm not completely sure to be honest.  Let me know if it helps, though.

---

### Post by pdescham49 on 2008-11-12
> **SVT said:**
> Open the Configuration Editor (Alt-F2 and run "gconf-editor") and untick /apps/metacity/general/compositing_manager, then try enabling Compiz effects again.  I *think* this fixed it for me, but I'm not completely sure to be honest.  Let me know if it helps, though.

Excellent Yup that was it. OMG is there a bug on this? i unclicked that restarted compiz and presto. all back. 

Thank you.

---

