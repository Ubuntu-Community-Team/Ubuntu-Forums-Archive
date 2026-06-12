---
title: "Make Notebook 8600M GT work with 3D-Accel in Ubuntu."
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by asus-G2S-7R024C on 2007-09-04
Hello everybody,

im a little frustrated, because nvidia officially claims to support the Nvidia 8600M GT of my ASUS G2S-7R024C Laptop (which is also in few other Laptops from Dell and even some MacBooks), but I cant seem to get it running properly.

What I have tried so far:

First I installed blindly nvidia-glx plus dependecies. When I saw that it didnt work I search google for tutorials and found different approaches.
Then I uninstalled all the nvidia modules, init-scripts and drivers and tried Envy.
Envy installed buidl-essentials among other tools, which are needed for kernel-module compilation and after that it downloaded the latest official nvidia drivers for my graphics card, Version 100.14.11.

From what I can see the kernel module loads up without problems.
The problems come when I set xorg.conf to use nvidia driver and actually start X.

Then the System freezes. I always have to manually shutdown and restart the laptop, because not even ctrl-alt-del reacts.

From what I am concerned by the links I have read on other sites I strongly suggest that its a serious driver bug, not a miss-configuration in xorg.conf.

But then again, nvidia officially claims drivers are working, so my question is:

Has anybody a working 8600M GT with 3D-acceleration (not "nv" or "vesa"!) on his ubuntu desktop or laptop?

There's got to be a way making this work, otherwise why does it even claim being sopported.

Thanks for help.

PS: there is another thread in this forum claiming this exact problem is "solved". Please dont point me there, because in that thread they just used "vesa", that not really what I'd call "solved", IMHO. ;-)

---

### Post by ntt on 2007-09-04
Hi,

with Geforce series 8 boards (like your 8600, or my 8400) you must install the "nvidia-glx-new" driver, and not the usual "nvidia-glx" (which silently fails to recognize the newer models).

at the moment (Ubuntu Gutsy ONLY, I think) the nvidia-glx-new driver installs the latest 100.14.xx Nvidia, good for Geforce 8*.

NOTE: the above is true only if you're using one of the Gutsy Tribe versions; for Feisty and earlier, you must download and install by hand the nvidia driver; The README file on the nvidia website is well done and should give you sall of the needed info.

From your problem description, I think you might be using Feisty...

hope this helps.

--ntt

---

### Post by Zheng on 2007-09-05
> **ntt said:**
> Hi,

with Geforce series 8 boards (like your 8600, or my 8400) you must install the "nvidia-glx-new" driver, and not the usual "nvidia-glx" (which silently fails to recognize the newer models).

at the moment (Ubuntu Gutsy ONLY, I think) the nvidia-glx-new driver installs the latest 100.14.xx Nvidia, good for Geforce 8*.

NOTE: the above is true only if you're using one of the Gutsy Tribe versions; for Feisty and earlier, you must download and install by hand the nvidia driver; The README file on the nvidia website is well done and should give you sall of the needed info.

From your problem description, I think you might be using Feisty...

hope this helps.

--ntt

No,[COLOR="SeaGreen"] nVidia 100.14 driver works for my Geforce 8400M G on Feisty[/COLOR],the only problem is that its sluggish when I use Beryl due to bugs in driver. Other than that, it works fair good with default compiz engine on Woody moving window, 3D cube, Kiba-dock.

How to:
1. Download & install Envy.
2. Run Envy and choose "Install the NVIDIA driver".
3. After installation complete, you can use nVidia settings program. "Applications -> System Tools -> Nvidia Settings" to adjust your screen resolution, OpenGL settings (not much option though)

Hope this help!

---

### Post by asus-G2S-7R024C on 2007-09-06
Hello,

I tried a new installation. this time I installed gutsy amd64 with nvidia-glx-new drivers from apt. This time, when X starts, the system does not crash.

But it still is not working properly, because now I get screwed up graphics. 4 colors black, red, green, blue. Very strange effect, like detect-edges or so. Hard to explain.

I tried different resolutions and color depths. Nothing.

Same Xorg.conf like under feisty.

Then I installed Arch Linux (x86 32bit) and the nvidia pacman package (also 100.14.11).
When booting up the init messages say: could not load module nvidia.ko: no such device.

I give it up for the moment. To me it seems to be not a good combination at the moment, using Linux with my Asus-G2S-7R024C. :( :( :( :( :( :(

---

### Post by lordmundi on 2007-09-06
i also have an asus g2s, and I can't get the nvidia driver to work, no matter what i do.

for some reason, I also don't appear to be getting error messages in the Xorg.0.log.  I think it is because the failsafe X server that runs un Ubuntu Gutsy is overwriting it... but I'm not sure.

If anyone gets the G2S to work with the nvidia driver, please post your xorg.conf and other settings here!

---

### Post by asus-G2S-7R024C on 2007-09-07
Hello again,

I think im a little further now.

I read from 3 independend sources, that people with the exact same problem solved this issue, by disabling frame buffer support in the kernel completely.

This is what I want to try now as the last thing before I give up.

But, how do you compile a custom ubuntu kernel?

I can see the kernel image and the kernel headers installed when running dpkg -l.
So far so good. But to recompile the kernel completely I need the exact kernel-sources
with all the patches included in my ubuntu (either feisty or gutsy), but I cant find no kernel sources with apt-cache search.

My plan is to somehow retrieve the ubuntu-sources+patches, zcopy the /proc/config.gz to the appropriate /usr/src directory and run make menuconfig.
Because I dont want to change the kernel config completely I prefer using the official existing (working) .config and only disable framebuffer support.
Every other kernel settings should be like in the official kernel. I'd also like to have an initramfs automatically generated to that custom kernel.

How do I do that?

I dont want to open a separate thread for this, because its somehow related to this very special problem/case.

---

### Post by martinrandau on 2007-09-10
Just wanna say I'm having the same problem with the same card on an Zepto Znote 3415, running Gutsy amd64.

edit:
I managed to solve this: Starting with a fresh install of Gutsy, I did all available updates and so got the 2.6.22-11 kernel. Then I installed nvidia-glx-new. This didn't activate the nvidia driver automatically, so I did ctrl-alt-f1, killed gdm by /etc/init.d/gdm stop, and edited xorg to use the nvidia driver. Upon restarting X I saw the nvidia logo and exloded of joy. 3d effects work but, as mentioned elsewhere, is quite sluggish. This will hopefully be fixed soon.

---

### Post by kukathe on 2007-09-12
> **martinrandau said:**
> Just wanna say I'm having the same problem with the same card on an Zepto Znote 3415, running Gutsy amd64.

edit:
I managed to solve this: Starting with a fresh install of Gutsy, I did all available updates and so got the 2.6.22-11 kernel. Then I installed nvidia-glx-new. This didn't activate the nvidia driver automatically, so I did ctrl-alt-f1, killed gdm by /etc/init.d/gdm stop, and edited xorg to use the nvidia driver. Upon restarting X I saw the nvidia logo and exloded of joy. 3d effects work but, as mentioned elsewhere, is quite sluggish. This will hopefully be fixed soon.

> and edited xorg to use the nvidia driver
How?
replace 'nv' with 'nvidia' ?
like this?
```
Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		'nvidia'
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by martinrandau on 2007-09-12
Yes, like that. :)

---

### Post by shador on 2007-09-15
So is it "confirmed" that 3D effects will work slow with the drivers mention in this thread? If so any news on an update?

---

### Post by Mongoose.wa on 2007-09-18
I have a Sager NP2090 with an 8600M GT. From what I've understood, Nvidia's current driver sucks, so it's not a problem with hardware or Linux. Hopefully Nvidia or Nouveau will release a driver that lets stuff run smoothly.

In my opinion, this is absolutely ridiculous. If I can play Bioshock with reasonable frame rates at full settings, I'm pretty sure I should be able to switch tabs in Firefox without lag...

---

### Post by Mongoose.wa on 2007-09-19
The new 100.14.19 driver seems to be helping a bit. Anyone else seeing a difference?

EDIT: Just kidding. Tabs are still annoyingly slow, even with the new driver.

---

### Post by rammstein2133 on 2007-09-30
I have an 8600M GS and I currently am having issues with the driver. I tried to install 100.14.19 and had no success at all. Every time it tries to start X, the screen just goes blank and we have to revert to the backup file we created. My friend who has done most of the attempting to install it has done everything he can think of and says all the help the forums have given has just been what he's been trying already. So we don't really know what to do about it now.

---

### Post by Glenn-Japan on 2007-12-11
i did the automatic install of Unbuntu and the latest updates.:guitar:

However I am unable to play games.  I ahve activated the restricted driver and the "New glx driver from Unbuntu update was installed.


I have never used Linux before so please bare with my adventure away from the Vista garbage that came OEM on this System :lolflag:


Can anyone help me with trouble shooting this driver?

---

### Post by ntt on 2007-12-12
Hi,

with Ubuntu 7.10 (Gutsy) Nvidia driver handling is much better than it used to be, so it's a bit strange it doesn't work out of the box...

Anyway, if you run the command   "glxinfo" (no quotes of course) in a console do you see something like this at the beginning of the text blurb?

server glx vendor string: nvidia

This would show that the nvidia driver is actually up and running.

If you don't see the vendor as "Nvidia" (but perhaps something like "SGI"), you may try running this command in a console:

sudo nvidia-glx-config enable

This should force the Nvidia driver enabled; afterwards, run again glxinfo and see if that made a difference.

If all of the above fails, last chance: Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

hope this helps.

--
ntt



> **Glenn-Japan said:**
> i did the automatic install of Unbuntu and the latest updates.:guitar:

However I am unable to play games.  I ahve activated the restricted driver and the "New glx driver from Unbuntu update was installed.


I have never used Linux before so please bare with my adventure away from the Vista garbage that came OEM on this System :lolflag:


Can anyone help me with trouble shooting this driver?

---

### Post by Glenn-Japan on 2007-12-13
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600M GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19
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
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon

---

### Post by ntt on 2007-12-14
So it seems the Nvidia driver _is_running, after all...

May be some of the OpenGL components got screwed up by an X update; it happened to me in the past after some X updates.

Try forcing reinstallation of the nvidia driver: just select the nvidia-glx-new package in Synaptic (or Adept, or what you've got as a package manager) and set its status to reinstall, then apply.

Try also to temporary disable Compiz - if you have it active - and see if this helps; some OpenGL applications may still have subtle misbehavior with it, especially when leaving full-screen mode.

Compiz can be enabled/disabled from the advanced settings of the themes, if I recall.

Or else, try using ENVY: I've seen reports stating it solved difficult nvidia situations.

--
ntt

---

### Post by Glenn-Japan on 2007-12-15
im currently running envy, but unable to have the same performance as i had in Windows vista. Both current unbuntu and envy are pointing to the same drivers FYI.


the Nvidia screen freeze still exists with both Win Vista,  Unbuntu and Envy for linux.

From what i see its a ASus Bios issue and limited linux drivers for the 8600m GT

---

### Post by ntt on 2007-12-15
All I can say is that my 8400GS works well with the nvidia-glx-new driver which comes with ubuntu Gutsy (release). But I have a different video card, and from a different manufacturer, so it makes no sense to compare apples and oranges...

No clues about performance comparison between Vista and Linux, though, because the preinstalled Vista only lasted the time needed to scratch the disk by installing ubuntu Gutsy :-)

sorry, I fear I can't be of more support. good luck!

--
ntt

---

### Post by asus-G2S-7R024C on 2008-01-12
Yesterday, ( 11.01.2008 )

I installed the BIOS Update Version 212 for my ASUS G2S 7R024C.

The latest Nvidia Drivers aswell as xorg's "nv" driver now work perfectly well
without any glitches or system freezes.

However, Im not sure what brought the real difference, the bios update or the driver.

I dont care really, because after 4 Months, it was about time for it to work.

Bye,
case closed.

---

### Post by Jerry [2eme R.E.P.] on 2008-02-22
In my case situation was the following:
1. Delete all nvidia.ko files from system
2. Disable loading of nv, nvidia_new modules
3. Downloadng drivers from nvidia.com 169.09
4. getting in text mode
5. installing them
6. allowing nvidia-config to modify my xorg.conf
7. rebooting
xserver craches
but then i've rebooted in recovery mode and everything got work!!!
i've tested 3d accel in "open arena" and "nexuiz"... All was perfect.
More of that-- my bluetooth apater suddenly began to work (it didn't start during normal boot)
I've studied, how recovery differ from normal boot and in fact have found no differnce in global.. same parameters, expet splash... Somethign strange in fact...

---

### Post by ntt on 2008-02-22
That's strange, because Geforce series 8xxx should properly work with the stock nvidia_new set of drivers (which are just Nvidia drivers with version >100); but then again, video board BIOSes do differ and some of them are quite nasty.

I've had a similar problem when using the previous version of Ubuntu (7.04) on a recent laptop, but since v7.10 everything (sound apart, but that's another story) begun working fine.

This is just wild guessing, but I think you're experiencing some sort of hardware conflict, most probably with IRQ's or memory addresses.

Things that have helped me in the past: booting with ACPI off, setting some kernel parameters like "pci=routeirq" or the like. Have a look to dmesg output, and try to see if there are any evident problems shown there.

Unfortunately there are so many kernel parameters, and every PC is a case on its own, so it's impossible to predict beforehand what will work and what will instead bring even more havoc...

The only downside to booting in "recovery mode" (or to setting some exotic kernel command line options, for that matter) is that you're likely killing some features while making some other work.

--
ntt

---

### Post by feynman on 2008-03-08
I have been struggling with this problem as well for approximately 1 week.  All attempts to install drivers either directly through NVIDIA's installer, or using Envy failed.  The Nvidia installer always stopped after being unable to compile the kernel header files.  The Envy installer wouldn't yield anything but low res vesa drivers.  Thankfully, after much pain and suffering, I have found the solution.  First: reflash bios with latest version.  Second: Install all Ubuntu updates.  Third, Install GLX through "restricted driver" manager.  Fourth: Run envy to install 169.12.  Now I have all driver options available in the Nvidia tool.  I hope this helps someone.  I just spent the past week trying to figure out how to recompile ubuntu kernel header files to no avail!

Gear:
Laptop: ASUS F8SV
BIOS Version: 300
GPU: NVIDIA 8600M GT
OS: Vista / Ubuntu dual boot.

---

### Post by FargenDog on 2008-04-24
Any loving for the Asus G2S and/or nVidia 8600GTS with the new 8.04 release?  I tried installing the video drivers but I'm getting errors - I guess the nvidia-glx-new are not supported in 8.04 last I read.  Is there a new supported version coming out since 8.04 is the current release?  Unfortunately I'm a newbie to all this and I'm limping along just trying to get the system up and running so I can learn the system.  I guess bashing your head against a wall is a form of learning....  fortunately the 4965 wireless is working with this kernel....  baby steps....

---

