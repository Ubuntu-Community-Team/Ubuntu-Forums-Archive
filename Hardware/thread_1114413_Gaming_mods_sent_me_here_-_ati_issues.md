---
title: "Gaming mods sent me here - ati issues"
date: 2009-04-02
forum: Hardware
---

### Post by larryfroot on 2009-04-02
Hi, this is at first sight perhaps a question aimed at the gaming section, but as they have their feet firmly planted in the software side of things, they redirect game-specific hardware questions to here.

Basically I have an ati hd4870. Is there a resource or person somewhere that can advise me if (in linux gaming terms) I have an absolute turkey on my hands, or is there something I can do apart from selling it and buying nvidea?

Initial research has left me with a sinking feeling...

And thanks to anyone who can advise me on this one! I would have liked to aim it at the gamers, but hardware questions are hardware questions...

---

### Post by markbuntu on 2009-04-03
What exactly is the problem?

---

### Post by larryfroot on 2009-04-03
Hi, thank you very much for asking! Appreciated.

Basically I downloaded a Cedega trial with a trial for Spore thrown in and the damn thing kept crashing, and throwing up artifacts as it did so, which is slightly worrying. This was with and without compiz running. I am on the current fglrx driver from the repo's. 

My attempts to get anywhere with Cedaga forums was somewhat stymied by the fact that you need to be a paid up member before you can post on it. But reading through the threads that contained 'ati' began to convince me that for (windows) gaming on Linux, I might be in a tight spot.

glx gears are typically - with compiz: 
> 56297 frames in 5.0 seconds = 11259.258 FPS

and without compiz average around:
> 51067 frames in 5.0 seconds = 10213.360 FPS

But then it did climb up a bit to parity with the previous score with compiz running.

so to...

fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release

and glxinfo - at least the first bit - 

> me of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMDX_vertex_shader_tessellator, GL_AMD_performance_monitor, 
    GL_AMD_texture_texture4, GL_ARB_color_buffer_float, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_instanced, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

Anyways, thats what's happening...just fine for five mins playing spore and then boom, frozen screen with artifacts and reisub time. 

I posted in the hope that someone could tell me to persevere with ati on Linux or point out that nvidea are a far better bet re windows games. Anything after that would be a bonus!

thanks again, LF

---

### Post by markbuntu on 2009-04-04
Well glxgears is pretty worthless for one and flgrx seems properly installed and working so you would need to do a backtrace to find where the application is hanging up and then bring that up with the app devs or with ati depending on what is happening.

---

### Post by larryfroot on 2009-04-04
Ok mate, will find out how to do a backtrace, that sounds very promising in getting this one nailed. Thanks!

---

