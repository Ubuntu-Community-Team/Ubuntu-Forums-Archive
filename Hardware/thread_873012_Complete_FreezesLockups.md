---
title: "Complete Freezes/Lockups"
date: 2008-07-28
forum: Hardware
---

### Post by Yoeri on 2008-07-28
I just installed Ubuntu on an older desktop pc. All went fine, except the PC experiences complete freezes from time to time. The longest I used the pc without freezing is about 30 minutes.

Hardware configuration:
- AMD Athlon XP2000+
- 1024MB Memory
- ATI Radeon 9000 Pro (Hercules prophet)
- Wireless network card (not used but detected)
- Wired network card (working)
- Firewire card (not used).

I initially thought it was the video-card so I followed [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) to install the opensource radeon drivers. All outputs from the troubleshooting section are fine. Does anyone has any suggestions? Can it be something else?

I also tried another distro with this machine, Fedora 9. In fedora, normal desktop use was fine. Freezes occured during a Warzone2100 game ... OpenGL related?

Below are some outputs (for the video card).

Thanks!!
Yoeri

**$ glxinfo | grep vendor**
```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```


**glxinfo | grep "direct rendering"**
```
direct rendering: Yes
```

**LIBGL_DEBUG=verbose glxinfo**
```

    name of display: :0.0
    libGL: XF86DRIGetClientDriverName: 5.3.0 r200 (screen 0)
    libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
    drmOpenDevice: node name is /dev/dri/card0
    drmOpenDevice: open result is 4, (OK)
    drmOpenByBusid: Searching for BusID pci:0000:01:00.0
    drmOpenDevice: node name is /dev/dri/card0
    drmOpenDevice: open result is 4, (OK)
    drmOpenByBusid: drmOpenMinor returns 4
    drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
    libGL error:
    Can't open configuration file /etc/drirc: No such file or directory.
    libGL error:
    Can't open configuration file /home/yoeri/.drirc: No such file or directory.
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
    OpenGL vendor string: Tungsten Graphics, Inc.
    OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
    OpenGL version string: 1.3 Mesa 7.0.3-rc2
    OpenGL extensions:
        GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
        GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp,
        GL_ARB_texture_compression, GL_ARB_texture_cube_map,
        GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
        GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
        GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
        GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
        GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,

        GL_EXT_blend_color, GL_EXT_blend_equation_separate,
        GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
        GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
        GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
        GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters,
        GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
        GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
        GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
        GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
        GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
        GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
        GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
        GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
        GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
        GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
        GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
        GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square,
        GL_NV_light_max_exponent, GL_NV_texture_rectangle,
        GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
        GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
        GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
```

---

### Post by DenzilS on 2008-07-28
Sudden and complete freezes are often a sign of an overheating CPU. Are the fans working? If you are happy to take the cover off, have a look at the heatsink on the processor. They often get clogged with dust, so remove it and give it a good blow out with compressed air/car footpump etc. while you're there, consider getting some new heat transfer paste to go between the heatsink and the processor. "Arctic Silver" is often recommended.

---

### Post by Yoeri on 2008-07-29
I checked the fan (cleaned it), also checked the heat sensors in the bios and enabled a shutdown when reaching 70°C (minimum option). I have an extra case cooler installed too.

It is strange that I don't see any message in log-files of the freeze. 

Fedora runs fine for office work and only crashes when playing games ...

---

