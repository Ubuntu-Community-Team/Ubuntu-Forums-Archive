---
title: "Nvidia GPU Acceleration not working 100% for decoding HD video on Ubuntu 14.04"
date: 2015-01-14
forum: Hardware
---

### Post by Smokin Whale on 2015-01-14
Hey guys,

I have a few older systems (socket 775, socket 754 and socket 939) which are struggling with decoding 720p and 1080p video in both Chrome (YouTube) and VLC. I am using an Nvidia Geforce 210 GPU with the latest Nvidia drivers installed from the Nvidia repository. GPU acceleration is enabled in VLC and is forced to be enabled in Chrome through chrome://flags. Chrome struggles in 720p, whilst VLC can handle 720p but struggles on 1080p. Firefox can do 720p okay, but drops frames on 1080p. The exact same systems have no trouble doing 1080p in Windows 8.1.

I've tried both Ubuntu Gnome 14.04 32bit and 64bit on all three systems with the same results.  I have tried newer systems using G31 graphics and they seem to decode the video fine. I also have system with an AMD HD3000 series integrated graphics card that has no issues either.

Specs of one machine I have here:

AMD Athlon 64 3800+
2GB DDR RAM
OEM MSI 7184 motherboard
Nvidia Geforce GT210 512mb

Some guidance on getting this issue sorted would be appreciated!

---

### Post by Yellow Pasque on 2015-01-14
What version of Ubuntu are you using?
Are you using VDPAU output for VLC?

This may help with VLC if you're using 2.1.x or earlier:
```
sudo apt-get install vdpau-va-driver
```

---

### Post by Smokin Whale on 2015-01-14
Using the latest up to date Ubuntu Gnome 14.04, both 32bit and 64bit. Yes using VDPAU with the latest VLC.

---

### Post by Yellow Pasque on 2015-01-15
Check vdpauinfo just to make sure it's working:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by Smokin Whale on 2015-01-19
Thanks for the response. The odd thing is that I installed Kodi over the weekend and that decoded video buttery smooth at only around 40% CPU usage, whilst Chrome will suck 100% CPU usage and get choppy. I get the odd jitter in VLC but it seems to be working, on average around 50-60% CPU usage. Chrome is particularly bad and struggles to decode 720p.

Here is the output as requested: 

```
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  331.113  Mon Dec  1 20:28:22 PST 2014


Video surface:


name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 


Decoder capabilities:


name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8192  2048  2048
H264_HIGH            41  8192  2048  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048
MPEG4_PART2_SP        3  8192  2048  2048
MPEG4_PART2_ASP       5  8192  2048  2048
DIVX4_QMOBILE         0  8192  2048  2048
DIVX4_MOBILE          0  8192  2048  2048
DIVX4_HOME_THEATER    0  8192  2048  2048
DIVX4_HD_1080P        0  8192  2048  2048
DIVX5_QMOBILE         0  8192  2048  2048
DIVX5_MOBILE          0  8192  2048  2048
DIVX5_HOME_THEATER    0  8192  2048  2048
DIVX5_HD_1080P        0  8192  2048  2048


Output surface:


name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 


Bitmap surface:


name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192


Video mixer:


feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -


parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4


attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  



```

Here is the output from Chrome's chrome://gpu page

```
[COLOR=#000000][FONT=sans-serif][h=3]Graphics Feature Status[/h]
[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#FF0000]Disabled[/COLOR]
[*]Rasterization: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Threaded Rasterization: [COLOR=#008000]Enabled[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Encode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Driver Bug Workarounds[/h]
[LIST]
[*]clear_uniforms_before_first_program_use
[*]disable_post_sub_buffers_for_onscreen_surfaces
[*]init_gl_position_in_vertex_shader
[*]init_vertex_attributes
[*]scalarize_vec_and_mat_constructor_args
[*]use_current_program_after_successful_link
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Problems Detected[/h]
[LIST]
[*]Always call glUseProgram after a successful link to avoid a driver bug: [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]use_current_program_after_successful_link[/COLOR]*
[*][I]Program link fails in NVIDIA Linux if gl_Position is not set: [286468]("http://crbug.com/286468")
*Applied Workarounds: [COLOR=#808000]init_gl_position_in_vertex_shader[/COLOR]*[/I]
[*][I][I]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*[/I][/I]
[*][I][I][I]Linux NVIDIA drivers don't have the correct defaults for vertex attributes: [351528]("http://crbug.com/351528")
*Applied Workarounds: [COLOR=#808000]init_vertex_attributes[/COLOR]*[/I][/I][/I]
[*][I][I][I]Disable partial swaps on linux drivers: [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]*[/I][/I][/I]
[*][I][I][I]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]*[/I][/I][/I]
[*][I][I][I]Raster is using a single thread.
*Disabled Features: [COLOR=#FF0000]multiple_raster_threads[/COLOR]*[/I][/I][/I]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Version Information*[/I][/I][/h][TABLE="width: 1889"]
[TR]
[TD]**Data exported**[/TD]
[TD]20/01/2015 01:33:15[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/39.0.2171.99[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 3.13.0-44-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list version**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Driver bug list version**[/TD]
[TD]7.10[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]04ab0eb41f1b[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia[/TD]
[/TR]
[TR]
[TD]**Command Line Args**[/TD]
[TD]--flag-switches-begin --ignore-gpu-blacklist --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Driver Information*[/I][/I][/h][TABLE="width: 1889"]
[TR]
[TD]**Initialization time**[/TD]
[TD]671[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]true[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x10de, DEVICE= 0x0a65[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]NVIDIA[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]331.113[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]3.30[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]3.30[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]NVIDIA Corporation[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]GeForce 210/PCIe/SSE2[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]3.3.0 NVIDIA 331.113[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_clear_buffer_object GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_instanced GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KHR_debug GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_ES1_1_compatibility GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_gpu_program4_1 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_path_rendering GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum[/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]NVIDIA Corporation[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_EXT_buffer_age GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_NV_multisample_coverage[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]GNOME Shell[/TD]
[/TR]
[TR]
[TD]**XDG_CURRENT_DESKTOP**[/TD]
[TD]GNOME[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]gnome[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8252[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Log Messages*[/I][/I][/h]
[LIST]
[*]*[I][I][3574:3574:0119/153205:ERROR:gpu_video_decode_accelerator.cc(301)] : Not implemented reached in void content::GpuVideoDecodeAccelerator::Initialize(const media::VideoCodecProfile, IPC::Message *)HW video decode acceleration not available.*[/I][/I]
[*]*[I][I][3574:3574:0119/153258:WARNING:file_descriptor_set_posix.cc(30)] : FileDescriptorSet destroyed with unconsumed descriptors: 0/1*[/I][/I]
[/LIST]
[/FONT][/COLOR]

```

---

### Post by Yellow Pasque on 2015-01-19
If you're using a site that uses Flash for video , maybe this will help (or not):
```
sudo mkdir -p /etc/adobe
echo "EnableLinuxHWVideoDecode=1" | sudo tee /etc/adobe/mms.cfg
echo "OverrideGPUValidation=1" | sudo tee -a /etc/adobe/mms.cfg
```

For playing video in Chromium using HTML5, it's going to take some hacking to get GPU decode acceleration: [http://www.kelvinblog.tk/enable-chromium-vaapi-hardware-decode-acceleration-linux/](http://www.kelvinblog.tk/enable-chromium-vaapi-hardware-decode-acceleration-linux/)

---

### Post by Smokin Whale on 2015-01-20
Wait what, no GPU decoding for HTML5 video on Ubuntu with Chrome at all? :( I guess it's time to switch back to Windows...

---

### Post by Yellow Pasque on 2015-01-20
Hmm, maybe the link I found only refers to chromium *Shrug*

You can try starting Chrome like this. If that doesn't help, I'm out of ideas...
```
google-chrome --ignore-gpu-blacklist --enable-vaapi
```


EDIT: Oh, you should check vainfo just to make sure va-api is working:
```
sudo apt-get install vainfo
vainfo
```

---

### Post by Smokin Whale on 2015-02-06
Thanks for the help, but didn't make any difference. Just going to accept the fact I need a faster CPU for HD Youtube.

---

