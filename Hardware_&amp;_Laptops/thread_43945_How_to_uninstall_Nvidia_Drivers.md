---
title: "How to uninstall Nvidia Drivers?"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by Xc0m on 2005-06-23
Hello all, yesterday i just install the nvidia drivers and my ubuntu just crash every time... it just freeze in the login session with the mouse working but nothing else working... i just realize that my video card is the problem cuz in my windows session the same problem is happening (in windows is a total crash)...

now my question is how to uninstall the nvidia drivers or swicht to the vesa one?

tnx for the help and sorry for my english :(

---

### Post by wylfing on 2005-06-23
1. Shut down X. Edit /etc/X11/xorg.conf and change your driver from 'nvidia' to 'nv'.

2. Run the nvidia installer with the --uninstall option.

Now, if for some reason you don't have the nvidia installer anymore and don't feel like downloading it just to uninstall, you can skip step 2. However, you **MUST** perform step 2 before installing Ubuntu packages that provide nvidia drivers, such as nvidia-glx.

---

### Post by Xc0m on 2005-06-24
ok srry if i didnt tell this at the beggining but im a total newbie at ubuntu... i only can run ubuntu from the recovery (just the terminal) and i dont know the commands to edit that file... i just try to locate the file but it seems like i dont have access to that folder (only home folder in my session and i can only see 2 files from the root session)

---

### Post by afonic on 2005-06-24
[QUOTE=Xc0m]ok srry if i didnt tell this at the beggining but im a total newbie at ubuntu... i only can run ubuntu from the recovery (just the terminal) and i dont know the commands to edit that file... i just try to locate the file but it seems like i dont have access to that folder (only home folder in my session and i can only see 2 files from the root session)[/QUOTE]
 Try:

sudo pico /etc/X11/xorg.conf

Find where it says:

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection
 
(on your PC may differ a bit) and change
 
Driver      "nvidia"
to
Driver      "nv"

Then press Control + O and enter to save the changes, Ctrl + X to exit and sudo reboot to restart.

---

### Post by wylfing on 2005-06-24
My bad. I assumed that since you installed the nvidia driver you had some comfort level with the command line. Post back if you need more help!

---

### Post by polo_step on 2005-06-24
Are nVidia AGP cards usually a nosebleed to get going?  I've seen nothing but installation problems here with them, and I could never even get mine to work in X without frequent bluescreens.  It's just sitting here. 

I'd LOVE to use it on this Ubuntu box, but being new at it, I don't know what I'm doing.

It's one of [these.](http://bfgtech.com/5500OC.html)

---

### Post by wylfing on 2005-06-24
I don't know anything about that card, but in general to get an nVidia card working in Ubuntu, you do this:
1. Install the linux-restricted-modules package for your kernel.
2. Install nvidia-glx and nvidia-settings.

That's it. Very easy.

There's a post here [http://www.ubuntuforums.org/showpost.php?p=100460&postcount=1](http://www.ubuntuforums.org/showpost.php?p=100460&postcount=1) that describes how to compile your own custom kernel with the latest drivers from the nVidia site if that's your thing.

---

### Post by polo_step on 2005-06-24
[QUOTE=wylfing]I don't know anything about that card, but in general to get an nVidia card working in Ubuntu, you do this:
1. Install the linux-restricted-modules package for your kernel.
2. Install nvidia-glx and nvidia-settings.

That's it. Very easy..[/QUOTE]
I just installed it according to the [FAQ thingy](http://ubuntuguide.org/#installnvidiadriver) mentioned in another thread.  It's working, but I have no real idea if it's running correctly.  Looks OK, but what do I know?  :smile: It was working after a fashion before I even installed the driver(s).

There any way to tell if it set up properly?  I get the big honkin' nVidia splash screen when I boot, so that's something.  Is there a video analysis/benchmark program or anything?

This is what I see in xorg.conf:

============================
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
============================

Not terribly reassuring.  Shouldn't that be "AGP"?

Thanks for any help.

[We'll see if it eventually crashes Linux the way it did XP.]

---

### Post by polo_step on 2005-06-25
Hmm.
 
Well, the "nVidia X Server Setings" dialogue comes up OK:

=============================
Graphics Processor:        GeForce FX5500
Bus Type:                       AGP
VBIOS Version:               04.34.20.69.00
Video Memory:               128
IRQ:                                 16
Operating System:           Linux x86
nVidia Driver Version:      1.0-7174
==============================

---

### Post by afonic on 2005-06-25
[QUOTE=polo_step]Hmm.
 
Well, the "nVidia X Server Setings" dialogue comes up OK:

=============================
Graphics Processor:        GeForce FX5500
Bus Type:                       AGP
VBIOS Version:               04.34.20.69.00
Video Memory:               128
IRQ:                                 16
Operating System:           Linux x86
nVidia Driver Version:      1.0-7174
==============================[/QUOTE]
 Type glxinfo and you should see something like that:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3

```
and much more.

The important part is "direct rendering: Yes". If it says Yes you're OK, if it says No you have no 3D acceleration.

And the  BusID "PCI:1:0:0" in the xorg.conf is just fine, it shouldn't say AGP or something like else.

---

### Post by polo_step on 2005-06-25
Well, here's what I get:

I think it looks OK... If this thing's actually 100% up, after spending a month unsuccessfully trying to make it work under XP, I'm speechless.

Is there any test/benchmark/burnin program for this in Linux?  Something like AquaMark, maybe?  If this card is good I want to confirm it before my RMA runs out on it if it's not.

================================================
anonymous@beatdown:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite,
    GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None [etc., etc., etc...]

---

### Post by Xc0m on 2005-06-25
[QUOTE=afonic]Try:

sudo pico /etc/X11/xorg.conf

Find where it says:

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection
 
(on your PC may differ a bit) and change
 
Driver      "nvidia"
to
Driver      "nv"

Then press Control + O and enter to save the changes, Ctrl + X to exit and sudo reboot to restart.[/QUOTE]

ok i just tried that but i dont have access to that folder in the terminal of recovery mode... i tried the root session and my main session but when i type the sudo pico /etc/X11/xorg.conf command.. it just create a new file...

i just feel like an idiot... using windows for so many years have make me an idiot lol

---

### Post by Xc0m on 2005-06-25
i just changed the drivers but using this command: sudo dpkg-reconfigure xserver-xorg...

thxs for the help anyways  :grin:

---

### Post by afonic on 2005-06-26
[QUOTE=polo_step]Well, here's what I get:

I think it looks OK... If this thing's actually 100% up, after spending a month unsuccessfully trying to make it work under XP, I'm speechless.

Is there any test/benchmark/burnin program for this in Linux?  Something like AquaMark, maybe?  If this card is good I want to confirm it before my RMA runs out on it if it's not.

================================================
anonymous@beatdown:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite,
    GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None [etc., etc., etc...][/QUOTE]
 Yes your card works just fine!

There is no benchmark, try running some 3D game. (search for Nexuiz)

---

### Post by polo_step on 2005-06-26
[QUOTE=afonic]Yes your card works just fine![/QUOTE]
And nobody could be more amazed than me!  :) 

It hasn't crashed yet, either.  It wouldn't work in XP on my other box - even on a new, virgin installation - without bluescreening every twenty minutes or so.  None of the other XP problems are happening, either.

> There is no benchmark, try running some 3D game. (search for Nexuiz).
I was just looking for something to wring it out and make sure there is no actual physical defect in the card.  There was some question of this at BFGTech's customer support after the problems in XP.

[This card ](http://bfgtech.com/5500OC.html) isn't the most appropriate choice for my non-gaming, pedestrian use, I'm sure, but Fry's had 'em on sale for $29.99 after rebate, making them the cheapest AGP card available that day.  :-?

Thanks for your help!

---

