---
title: "Geforce 7100gs not working after install"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by dcinzona on 2007-08-23
Hey everyone, let me start off with the usual "I'm new to ubuntu"...
k, done.
***EDIT: Running Version: Feisty -
Hardware:
MOBO: Gigabyte GA-8N-SLI ver. 1.1 Bios F6 (latest)
VIDEO: GeForce 7100GS (cheapie) :)
MONITOR: 37 inch Westinghouse LCD (VGA connector - Other pc is using DVI)
Here's the problem: I can get through the install of Ubuntu fine, but for some reason I cant get 3d to work with the card. 
Things i've tried:
-Reinstalling several times... The weird thing was that I would get different results on each install...none of which got me 3D support or a resolution of 1920x1080 (which i want)
-Envy scripts, this actually cause the system to not function anymore and i had to reinstall...
-Enabling restricted drivers for nvidia

lspci results:
```

00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation Unknown device 003f (rev a1)
00:0a.0 ISA bridge: nVidia Corporation Unknown device 0030 (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP04 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.2 USB Controller: nVidia Corporation MCP04 USB Controller (rev a2)
00:0e.0 Bridge: nVidia Corporation MCP04 Ethernet Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation MCP04 IDE (rev f2)
00:10.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:11.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:12.0 PCI bridge: nVidia Corporation MCP04 PCI Bridge (rev a2)
00:13.0 Multimedia audio controller: nVidia Corporation MCP04 AC'97 Audio Controller (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 016a (rev a1)
```

I feel like the problem lies with the Unknown device .... :confused:
is this incompatible hardware? if so, what would be a good cheap configuration?  if i have to buy a new video card i'm going to get a dx10 card and swap out the one on my gaming system and stick it in ubuntu (if a geforce 7800GTX is compatible)
anyone know how to get the install to correctly identify my mobo chipset???
Fedora 7 ID's the video card correctly and beryl functions on it fine.

Thanks guys, any help is really appreciated!

---

### Post by dcinzona on 2007-08-23
oh, one more thing: 
xorg.conf DOES have the correct video card listed...
I have NO idea how it would know but the OS doesnt???
Here's my xorg.conf (important part)
```
Section "Device"
    Identifier    "nVidia Corporation GeForce 7100 GS"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-204
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation GeForce 7100 GS"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "4095x4095" "1280x1280" "1280x1024" "1280x800" "1024x768" "800x600" "720x400" "640x480"
```

like i mentioned before about each install being different...i never saw a resolution of 4095x4095 before...
Thanks again guys, this is messing my head up

---

### Post by dabl on 2007-08-23
Not a digital engineer here, but I'll offer an opinion that there's some hardware issue with your card and mobo -- that lspci output looks crazy to me.  I have a GeForce 7900GS, and here is the TOTAL output of lspci on my rig:

```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

```

As you can see, the video card is all of _1 line_.  That's why I think there's something amiss with your hardware interface (I know, Fedora worked ....)

Also, I can't imagine why the Envy script would disable your system -- I've never heard of that. I've heard a few people say it doesn't work in GUI mode and they have to use it in text mode, but not that it messed with the rest of their system.  So, I dunno -- I guess I'd be looking at BIOS settings for the display adapter, and whether there's video RAM sharing enabled, and stuff like that.  :confused:

---

### Post by tseliot on 2007-08-24
> **dcinzona said:**
> Here's the problem: I can get through the install of Ubuntu fine, but for some reason I cant get 3d to work with the card.
post the output of this command:
```
glxinfo
```

> **dcinzona said:**
> Things i've tried:
-Reinstalling several times... The weird thing was that I would get different results on each install...none of which got me 3D support or a resolution of 1920x1080 (which i want)
-Envy scripts, this actually cause the system to not function anymore and i had to reinstall...
-Enabling restricted drivers for nvidia
There's no need whatsoever to reinstall every time the Xserver crashes. Here's what you should do in such cases:
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

> **dcinzona said:**
> I feel like the problem lies with the Unknown device .... :confused:
is this incompatible hardware? if so, what would be a good cheap configuration?  if i have to buy a new video card i'm going to get a dx10 card and swap out the one on my gaming system and stick it in ubuntu (if a geforce 7800GTX is compatible)
anyone know how to get the install to correctly identify my mobo chipset???
Fedora 7 ID's the video card correctly and beryl functions on it fine.
"Unknown device" doesn't mean that it won't work.

set the driver to "nvidia" in your xorg.conf, reboot and post your /var/log/Xorg.0.log

---

### Post by shekhark on 2007-08-24
Hi I've got a slightly different issue here. After installing the NVIDIA GeForce 7100 GS and twiddling around with drivers and xorg.conf to get things working, I discovered that the drivers that work for this video card are from the package nvidia-glx-legacy and NOT nvidia-glx (which is installed when one activates NVIDIA in "Restricted Drivers Manager"). While everything works fine with nvidia-glx-legacy, I cannot use Beryl/Compiz anymore, nor do I have any 3D acceleration or any other tangible benefits from this video card. Am I doing something wrong here? How can I get visual effects and others things working with the 7100 GS, or did should I get another video card which is newer?

---

### Post by tseliot on 2007-08-24
> **shekhark said:**
> Hi I've got a slightly different issue here. After installing the NVIDIA GeForce 7100 GS and twiddling around with drivers and xorg.conf to get things working, I discovered that the drivers that work for this video card are from the package nvidia-glx-legacy and NOT nvidia-glx (which is installed when one activates NVIDIA in "Restricted Drivers Manager"). 
Actually the right driver is nvidia-glx-new

> **shekhark said:**
> While everything works fine with nvidia-glx-legacy, I cannot use Beryl/Compiz anymore, nor do I have any 3D acceleration or any other tangible benefits from this video card. Am I doing something wrong here? How can I get visual effects and others things working with the 7100 GS, or did should I get another video card which is newer?
nvidia-glx-legacy doesn't work with the desktop effects

---

### Post by dcinzona on 2007-08-24
Hey, sorry for the late response...I was working on it for a while last night and I got it to work!
This is what I did:

-Fresh install of Ubuntu Feisty
-update everything from install ~approx 179 mb
-enabled restricted drivers for nvidia (yeah, they showed up...no idea)
   after doing this and rebooting desktop effects worked! :confused:
-ran through this thread [http://ubuntuforums.org/showthread.php?t=508769]("http://ubuntuforums.org/showthread.php?t=508769")
- after doing this compiz, the compiz icon didnt work...so instead of doing compiz --replace i just went through THIS article: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml")

**dont run compiz --replace **
After you're done with this article, click on the CF icon and it should now work.

Guys, I really have NO idea why it worked this time around...maybe it had to do with the BIOS flash i did last night get me from F3 to F6...no idea, but lspci still displays all those unknowns...
I'll post back more info on all my configs when I get home tonight.
oh, also- got the resolution working on my 37inch at 1920x1080...so beautiful :)
i'll post my xorg.conf monitor section to show what I did to get that - got it from a post on here somewhere and had to modify it a little...but it worked.
Now i'm going to go buy a directX video card because this POS 7100gs sucks at rendering that cube- im at like 20fps...probably cause of my uber resolution

---

### Post by dcinzona on 2007-08-24
Thanks for that tip on xserver crashing! that'll save me hours in the future :-)

---

### Post by dcinzona on 2007-08-24
hey, here's my glxinfo result:
```
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
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7100 GS/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.31
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
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_clear_tag, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

```
Here is my xorg.conf to get full res on the westinghouse lcd monitor:
```
Section "Monitor"

	# 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
    Identifier     "Monitor0"
    VendorName     "WDE Westinghouse"
    ModelName      "LVM-37w3"
    HorizSync       30.0 - 68.0
    VertRefresh     58.0 - 72.0
    ModeLine       "1920x1080_60.00" 172.8 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation GeForce 7100 GS"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7100 GS"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080_60"
    EndSubSection
EndSection
```


hey, regarding compiz fusion...i saw a dodge plugin on a youtube video but i cant seem to find it anywhere...anyone know how to get it?
Thanks guys, i hope my solution helped

---

### Post by shekhark on 2007-08-25
> Actually the right driver is nvidia-glx-new

Neither nvidia-glx or nvidia-glx-new work properly for me, as X keeps sending back an error message about a mismatch between the driver and kernel versions. Any help on how to address this so I can enjoy something better than the legacy driver?

---

