---
title: "HD4650 Dual Monitor issues"
date: 2009-06-17
forum: Hardware
---

### Post by Domino3 on 2009-06-17
I have a  ATI Radeon 4650 Video card and have several problems. I use the drivers from the hardware drivers thing from the administration panel. First off It makes my secondary monitor on the right the main one and the one on the left is just a clone. I have no idea how to change this as the ATI CCC says unknown for the dual monitors and also has the independent option with xinerama which I want with dual monitors. So, how would I fix the issue with the two screens and Xinerama?

---

### Post by Domino3 on 2009-06-19
bump.

---

### Post by configt on 2009-08-07
You are lucky to be getting even one monitor running.  

I just bought a XFX HD 4650 AGP 8X 1G DDR2 card for my 7 year old P4 mobo.

I have tried the open drivers, the canonical drivers, and the drivers from ATI all with terrible results (the screen just garbles with proprietary drivers, and the card in unable to be detected by all other drivers).

I originally had a Radeon 9800 Pro (also AGP) before this, and it worked very well except for the 2048x1024 3D limitation that prevented dual monitor compiz (1280x1024 x 2 = 2560x1024).  I then tried an Nvidia 8400GS, which also worked but was very low performance, worse than the 9800, and just unbearable.  The 4650 was to be the solution, but apparently not.  I have read that others are also having issues with the 4650.  

If anyone knows how to get the 4650 running in jaunty, please do tell.  Also, I am open to suggestions on the video card to use.  I need the performance of the 9800 which suited me just fine, but with 2560x1024 minimum 3D resolution support for dual monitor configuration to drive two 1280x1024 monitors.

The thought of spending $1500+ to build a new rig that supports PCI-E just to get 2560x1024 3D makes me shudder.  There has to be an AGP card that will do this in linux, and that isn't slower than a Radeon 9800 Pro.

:confused:

---

### Post by The Jinx on 2009-08-18
bump? anyone have any luck with the 4650, I was planning to update my old system from a 7600GS to a HD4650

---

### Post by Maddmaxx on 2009-08-23
I have also been trying to use an XFX HD 4650 (AGP 8X) which is based on the RV730 GPU. It seems that this card, though extremely good in xp and vista, is not supported by either the open source or the proprietary drivers, tried with all ATI Linux versions 8.10 through 9.8, to no avail... WHAT GIVES?

My post in [http://ubuntuforums.org/showthread.php?t=1190433](http://ubuntuforums.org/showthread.php?t=1190433)

I as well have been having the same issues with my Radeon HD 4650. Through every method found by forum posts, tutorials, guides, to no avail... I was able to successfully install the driver that was listed as both compatible and recommended in EnvyNG. Upon first reboot, I am able to get everything working PERFECTLY, Compiz, video playback and so on... BETTER THAN EVER! Granted I do have that "AMD Unsupported hardware" watermark on the bottom right hand corner of the screen. My performance isn't even suffering! 2500+ frames per second in GLXGears...

Now, the problem lies in the fact that it only works on that first reboot, then it never works again... the second, and every subsequent reboot/startup results in a blank screen, to which I am unable to login, or drop to shell from... It works only once though.

It just seems like AMD/ATI has blocked my ability to use the proprietary ATI linux driver. How can I bypass this? I have been running this time with this configuration, for several hours, and have not cooked anything... as soon as I reboot I will have to reinstall the drivers again...

This is sooooo frustrating... It works perfect, even plays 1080p perfectly, xinerama, dual monitor, etcetera... only on the first reboot... Any suggestions?

Running 9.04 i386

dmesg | tail
[ 58.771034] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[ 58.771036] [fglrx] Reserved FB block: Unshared offset:fd89000, size:277000
[ 58.771039] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000
[ 59.156411] eth1: link down
[ 59.156617] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 59.157374] skge eth0: enabling interface
[ 59.164304] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 60.844262] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 60.844442] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 71.816005] eth0: no IPv6 routers present

glxinfo
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample,
GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating,
GLX_MESA_allocate_memory, GLX_MESA_swap_control,
GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method,
GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group,
GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.4
GLX extensions:
GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample,
GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating,
GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method,
GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series
OpenGL version string: 2.1.8673
OpenGL shading language version string: 1.30
OpenGL extensions:
GL_AMDX_vertex_shader_tessellator, GL_AMD_draw_buffers_blend,
GL_AMD_performance_monitor, GL_AMD_texture_texture4,
GL_ARB_color_buffer_float, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float,
GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_instanced,
GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
GL_ARB_fragment_shader, GL_ARB_framebuffer_object,
GL_ARB_framebuffer_sRGB, GL_ARB_half_float_pixel,
GL_ARB_half_float_vertex, GL_ARB_instanced_arrays,
GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture,
GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow,
GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
GL_ARB_texture_buffer_object, GL_ARB_texture_compression,
GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map,
GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
GL_ARB_texture_rg, GL_ARB_texture_snorm, GL_ARB_transpose_matrix,
GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object,
GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc,
GL_ATI_texture_env_combine3, GL_ATI_texture_float,
GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra,
GL_EXT_bindable_uniform, GL_EXT_blend_color,
GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_draw_buffers2,
GL_EXT_draw_instanced, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,
GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB,
GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4,
GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters,
GL_EXT_rescale_normal, GL_EXT_secondary_color,
GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D,
GL_EXT_texture_array, GL_EXT_texture_buffer_object,
GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc,
GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer,
GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB,
GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm,
GL_EXT_texture_swizzle, GL_EXT_transform_feedback, GL_EXT_vertex_array,
GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
GL_NV_conditional_render, GL_NV_copy_depth_to_color,
GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap,
GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays,
GL_WIN_swap_hint, WGL_EXT_swap_control

81 GLX Visuals
visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x24 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x25 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x26 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x27 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x28 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x29 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2a 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2b 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2c 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2d 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2e 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2f 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x30 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x31 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x32 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x33 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x34 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x35 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x36 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x37 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x38 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x39 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3a 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3b 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3c 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3d 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3e 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3f 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x40 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x41 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x42 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x43 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x44 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x45 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x46 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x47 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x48 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x49 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x4a 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x4b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4f 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x50 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x51 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x52 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x53 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x54 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x55 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x56 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x57 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x58 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x59 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5a 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5f 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x60 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x61 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x62 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x63 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x64 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x65 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x66 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x67 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x68 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x69 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6a 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6f 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x70 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x71 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x72 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0xad 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 4 1 Ncon

87 GLXFBConfigs:
visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x24 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x25 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x26 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x27 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x28 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x29 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2a 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2b 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2c 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2d 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2e 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2f 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x30 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x31 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x32 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x33 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x34 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x35 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x36 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x37 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x38 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x39 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3a 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3b 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3c 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3d 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3e 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3f 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x40 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x41 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x42 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x43 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x44 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x45 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x46 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x47 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x48 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x49 0 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x4a 0 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x4b 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4c 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4d 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4e 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4f 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x50 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x51 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x52 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x53 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x54 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x55 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x56 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x57 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x58 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x59 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5a 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5b 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5c 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5d 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5e 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5f 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x60 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x61 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x62 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x63 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x64 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x65 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x66 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x67 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x68 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x69 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6a 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6b 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6c 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6d 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6e 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6f 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x70 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 8 1 None
0x71 0 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0x72 0 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 8 1 None
0xad 0 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 4 1 Ncon
0xad 0 tc 0 128 0 y . 32 32 32 32 0 24 0 0 0 0 0 0 0 Ncon
0xad 0 tc 0 128 0 . . 32 32 32 32 0 24 0 0 0 0 0 0 0 Ncon
0xad 0 tc 0 64 0 y . 16 16 16 16 0 24 0 0 0 0 0 0 0 None
0xad 0 tc 0 64 0 . . 16 16 16 16 0 24 0 0 0 0 0 0 0 None
0xad 0 tc 0 32 0 y . 11 11 10 0 0 24 0 0 0 0 0 0 0 None
0xad 0 tc 0 32 0 . . 11 11 10 0 0 24 0 0 0 0 0 0 0 None
Last edited by Maddmaxx; 10 Minutes Ago at 06:57 PM..

---

### Post by grandpaken on 2009-10-07
I'm on my Mythbuntu install attempt #26...I guess I'm persistent.   Attempts 1-20 were with an ATI X1600pro AGP card and the best I could do was get a higher resolution display using the radeonHD driver but could not watch live tv using my HDHomerun as I would get about 5 fps due to the lack of hardware acceleration.   
  
Everyone knows now that ATI dropped support for the older cards so I bit the bullet and picked up a HD4650 AGP which is one of the few choices available to us AGP diehards.   It works great in XP for gaming which is one of the reasons I bought it but can not get Mythbuntu drivers to work other than the default at 640x480.  The ATI driver installed but my system locks up right after the Myth progress bar Finishes loading.   My first two attempts were by choosing the ATI drivers instead of Open Source during the install once with 1080i then again with 480i and component video.  Installing the 
fglrx drivers from the ATI site resulted in the same lockup.  

 I've now moved on to the RadeonHD driver and it does not detect my AGP card.  The logs show EE error "no devices detected" and another line shows it attempting to load the PCI 1:0:0:0  bus instead of AGP.  I then get a screen that I'm in "Low Graphics" mode and when exiting out of Myth get a blank desktop and can only run an application using alt-F2.  Does anyone have the commands for xorg.conf for setting the device to AGP?  


P.S.  My 25 installs does not include attempts at installing Mythdora or LinuxMCE.  I'm really trying hard to ween myself off of Windows but these driver issues are driving me crazy.  

> **configt said:**
> You are lucky to be getting even one monitor running.  

I just bought a XFX HD 4650 AGP 8X 1G DDR2 card for my 7 year old P4 mobo.

I have tried the open drivers, the canonical drivers, and the drivers from ATI all with terrible results (the screen just garbles with proprietary drivers, and the card in unable to be detected by all other drivers).

I originally had a Radeon 9800 Pro (also AGP) before this, and it worked very well except for the 2048x1024 3D limitation that prevented dual monitor compiz (1280x1024 x 2 = 2560x1024).  I then tried an Nvidia 8400GS, which also worked but was very low performance, worse than the 9800, and just unbearable.  The 4650 was to be the solution, but apparently not.  I have read that others are also having issues with the 4650.  

If anyone knows how to get the 4650 running in jaunty, please do tell.  Also, I am open to suggestions on the video card to use.  I need the performance of the 9800 which suited me just fine, but with 2560x1024 minimum 3D resolution support for dual monitor configuration to drive two 1280x1024 monitors.

The thought of spending $1500+ to build a new rig that supports PCI-E just to get 2560x1024 3D makes me shudder.  There has to be an AGP card that will do this in linux, and that isn't slower than a Radeon 9800 Pro.

:confused:

---

### Post by MIJ-VI on 2010-06-19
Unresolved issue *bump*.

---

