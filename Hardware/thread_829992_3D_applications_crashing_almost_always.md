---
title: "3D applications crashing almost always"
date: 2008-06-15
forum: Hardware
---

### Post by Cerberus108 on 2008-06-15
Hello, I'm experiencing, since when I installed Linux (and Ubuntu) my first time, a frustrating problem with my computer (AMD Sempron 3000+ 1.8Ghz, NVidia GeForce 4200 128MB): when I'm working with 3D applications such Blender, or with various 3D games including Glest, Nexuiz etc, very often these programs crash, sometimes making X11 crash too. :mad:

This is a really annoying problem as you can see, and I absolutely don't know why this happens. I have tried to see if it was "nvidia" X11 driver's fault, by changing xorg.conf to use "nv" driver instead, but it didn't load glx module, so 3D apps didn't even open. :confused:

Please, help me solving this problem! Thanks in advance :)

Uh, and I experienced this problem always, with every distribution from Edgy Eft to the latest Hardy Heron.

---

### Post by Odrodzona-Sarmacja on 2008-06-15
1. Disable networking.
2. Detach network cables from you computer.
3. Reboot.
4. Enjoy a 3d game (once i got 2 days without a single freeze)

---

### Post by Cerberus108 on 2008-06-17
that not worked... obviously. please, can you help me?

---

### Post by Odrodzona-Sarmacja on 2008-06-17
Try removing unnecessary networking programs like "remote desktop" or "gnome vpn" and so on and don't boot up with networking connected.

Perhaps you should also check that you are using right nvidia-glx driver for your card (don't use open source alternative, it is even worse at crashing and freezing and doesn't even give any error messages, when crash happens).

Also you can have a look in "var/log/syslog" to see if you get any messages about this errors, when crash occurred.

Freezes for 3d apps happen also because swap is not mounted correctly, and you can check up on that with "sudo swapon -s". That is if this command shows list of none swap drives or more then two drives, then you should fix it down to one. It is a known bug I think.

Also you may have a look into "etc/gamin/gaminrc" and set polling hd values to something like:
fsset ext2 poll 10
fsset ext3 poll 10
fsset vfat poll 10
fsset ntfs poll 10
,because gamin may in some circumstances also cause crashes and freezes.

Also you may like to uninstall one of screen savers if you got two or more of them installed on your computer.

I used to have freezes like every 15 mins after every boot up, but now when i fixed all these issues sometimes for entire days I don't have any freezes. I hope it will help you somehow too.

---

### Post by ar_lav on 2008-06-19
> **Cerberus108 said:**
> Hello, I'm experiencing, since when I installed Linux (and Ubuntu) my first time, a frustrating problem with my computer (AMD Sempron 3000+ 1.8Ghz, NVidia GeForce 4200 128MB): when I'm working with 3D applications such Blender, or with various 3D games including Glest, Nexuiz etc, very often these programs crash, sometimes making X11 crash too. :mad:

This is a really annoying problem as you can see, and I absolutely don't know why this happens. I have tried to see if it was "nvidia" X11 driver's fault, by changing xorg.conf to use "nv" driver instead, but it didn't load glx module, so 3D apps didn't even open. :confused:


Please, help me solving this problem! Thanks in advance :)

Uh, and I experienced this problem always, with every distribution from Edgy Eft to the latest Hardy Heron.


hmmm, I dont see why netwrking shoubld have anything to do with 3d apps. Maybe your graphics card is broken or you dont have the graphics drivers setup correctly? 

try doing a clean installation , install the 3d nvidia drivers, try to see if blender runs , and if it opens go to help>system>benchmark and report the output here.
Also report the output of Help>system>system information here, again from blender: You open a new text window inside blender by clicking on a header and clicking "split" , then change the type of the window by the header icon to text. Then go to the aforementioned  Help>system>system information , which should create a new txt inside the text editor in blender. To see the file just click on the button with the two arrows, select system-info.txt , and the file>save as to save the file. Then open it with a text editor and post here so we can help/

now if the text file does not report any problems then probably the graphics card on your machine gets overheated or is in some way broken unfortunately.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Any idea, how to get that blender feedback on Xubuntu too? I don't have these system settings it seems. I would LOVE to read that blender log on my computer. I installed also nvidia-settings. Can some blender info be obtained through this gui?

Also. I forgot one issue. Bad RAM can cause all kind of corruptions. So checking it with memtest+ would be also advisable, as it is sometimes also source of freezes too.

There is some tool on gnome ubuntu, which is some kind of interface for both wireless devices and nvidia. However after uninstalling jocker from my xubuntu nothing changes.

The only characteristic thing I noticed between versions of os, which didn't crash on 3d apps on my computer and these who do so is that...
image file i do on the root partition is like 3-4 times bigger despite using the same compression settings on the images. Any idea, why length of "/" image file could be connected to Ubuntu crashing on 3D applications?

---

### Post by ar_lav on 2008-06-22
> **Odrodzona-Sarmacja said:**
> Any idea, how to get that blender feedback on Xubuntu too? I don't have these system settings it seems. I would LOVE to read that blender log on my computer. I installed also nvidia-settings. Can some blender info be obtained through this gui?




You can get the same info on every platform that blender runs on, so Xubuntu should not be a problem!
If you have any trouble with it just say s o and I ll try to help!

---

### Post by Odrodzona-Sarmacja on 2008-06-22
I installed blender on Xubuntu and i get following info from it:
draw
0.000905 s/op - 1104.54 ops/s - 5523 iterations
recalc ob
0.000001 s/op - 1299206.41 ops/s - 100000 iterations
recalc data
0.000015 s/op - 68292.75 ops/s - 100000 iterations
system
"system-info.txt.008"

```

=====================================
=  Blender 2.45 System Information  =
=====================================


Platform: linux2
========

Python:
======

- Version: 2.5.2 (r252:60911, Apr 21 2008, 11:29:43) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

- Paths:


/usr/lib/python25.zip
/usr/lib/python2.5
/usr/lib/python2.5/plat-linux2
/usr/lib/python2.5/lib-tk
/usr/lib/python2.5/lib-dynload
/usr/local/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages/Numeric
/usr/lib/python2.5/site-packages/PIL
/usr/lib/python2.5/site-packages/gst-0.10
/var/lib/python-support/python2.5
/usr/lib/python2.5/site-packages/gtk-2.0
/var/lib/python-support/python2.5/gtk-2.0
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode
/usr/bin
/home/eagle/.blender/scripts
/home/eagle/.blender/scripts/bpymodules

- Directories:

 Blender home dir:
  /home/eagle/.blender

 Default dir for scripts:
  /home/eagle/.blender/scripts

 Default "bpydata/" data dir for scripts:
  /home/eagle/.blender/scripts/bpydata

 User defined dir for scripts:
  <NOTICE> -- not found

 Data dir "bpydata/" inside user defined dir:
  <NOTICE> -- not found

 Default config data "bpydata/config/" dir:
  /home/eagle/.blender/scripts/bpydata/config

- Modules: all basic ones were found.

OpenGL:
======

- Renderer:   GeForce FX 5700/AGP/SSE/3DNOW!
- Vendor:     NVIDIA Corporation
- Version:    2.1.2 NVIDIA 169.12

- Extensions:

GL_ARB_depth_texture GL_ARB_fragment_program
GL_ARB_fragment_program_shadow GL_ARB_fragment_shader
GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample
GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object
GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow
GL_ARB_shader_objects GL_ARB_shading_language_100
GL_ARB_texture_border_clamp GL_ARB_texture_compression
GL_ARB_texture_cube_map GL_ARB_texture_env_add
GL_ARB_texture_env_combine GL_ARB_texture_env_dot3
GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle
GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object
GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos
GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra
GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax
GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader
GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord
GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample
GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters
GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil
GL_EXT_packed_pixels GL_EXT_paletted_texture
GL_EXT_pixel_buffer_object GL_EXT_point_parameters
GL_EXT_rescale_normal GL_EXT_secondary_color
GL_EXT_separate_specular_color GL_EXT_shadow_funcs
GL_EXT_shared_texture_palette GL_EXT_stencil_two_side
GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc
GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp
GL_EXT_texture_env_combine GL_EXT_texture_env_dot3
GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod
GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB
GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip
GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square
GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence
GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program
GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage
GL_NV_half_float GL_NV_light_max_exponent
GL_NV_multisample_filter_hint GL_NV_occlusion_query
GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite
GL_NV_primitive_restart GL_NV_register_combiners
GL_NV_register_combiners2 GL_NV_texgen_reflection
GL_NV_texture_compression_vtc GL_NV_texture_env_combine4
GL_NV_texture_expand_normal GL_NV_texture_rectangle
GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3
GL_NV_vertex_array_range GL_NV_vertex_array_range2
GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2
GL_NV_vertex_program2_option GL_SGIS_generate_mipmap
GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
GL_SUN_slice_accum 


- Simplistic almost useless benchmark:

Redrawing all areas 10 times took 0.0800 seconds.

..

(*) Found 2 notices, documented in the text above.

```

I have Nvidia GF FX 5700.

Also when my networking is down I don't have now any crashes. Only when networking is active my system immediately freezes with any 3d app or game (and even with audacious and with firefox) and from time of freeze i get only these errors in syslog only from nvidia module.

But when networking is down I also get 3d games crashed, but more simple like game just crashes to desktop. Then there are usually far more of these nvidia error messages and my Xubuntu doesn't freeze either...


When I use open drive for nvidia instead of nvidia-glx-new binary, then I get freezes no matter if I have networking on or off.

I am not wiser on this, but It looks to me like some hidden rootkit is hooking into kernel to correct old networking issues with networking failing altogether and messing with dbus&nvidia somehow, when doing patching networking into working order. It just looks that way. I will be happy if these freezes can be fixed.

Does this information from blender give any clue how to deal with these freezes? Or should I do now something more to trace this issue down? To be honest blender thing doesn't give me any clues.

---

### Post by ar_lav on 2008-06-23
Are you sure that it is not a hardware issue? from the blender output everything seems to be working fine, openGL and all. 

Is your network card on board the motherboard? does it work with other distributions ? I think you should try another network card or another distribution (try a live cd ) to see whether the problem persists! 

(Iwould also suggest that you start a new thread on the topic so as many more will help. I am almost certain that this is a problem with the network card and not the graphics card!)

---

### Post by Odrodzona-Sarmacja on 2008-06-23
Indeed despite all system freezes on video applications (players like vlc for example or amarok), 3d games (open arena) and firefox (where flash freezes too, but I think there is yet another flash bug involved) related I think some longer time now that this is networking issue related, as when I boot without networking I don't have any freezes any more. However to get over these frequent freezes to relative stability I needed to fix few independent Ubuntu bugs, which also give freezes on their own and uninstall lots of network related applications like gnome vpn for example.

I use network card, which is integrated in the motherboard. It works on Debian 4.0 and Xubuntu (non-upgraded) 7.04 without freezes and on 7.04 I need to do just "sudo ifup eth0" (in Xubuntu 8.04 it doesn't work, as it uses roaming mode), when networking drops. However I need to upgrade Xubuntu 7.04 to latest Xubuntu 7.04 software and kernel or install Xubuntu 8.04 to get these freezes, when using any graphic application.

Yes, indeed I think I will go about starting my own thread soon. I want just to be sure I don't have some already recognized bug, which causes freezes on 3d games (and so on) when Xubuntu 8.04 is network connected.

---

### Post by Odrodzona-Sarmacja on 2008-06-25
I found a solution. It is crude but it works, which makes me extremely happy ;)

[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)

Removing network-manager and then by hand setting eth0 interface did the trick for me. Though I don't have any network-manager any more, which was so handy I must admit ;)

---

