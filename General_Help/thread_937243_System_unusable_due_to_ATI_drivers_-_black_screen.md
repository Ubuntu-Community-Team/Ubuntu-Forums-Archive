---
title: "System unusable due to ATI drivers - black screen"
date: 2008-10-03
forum: General Help
---

### Post by Kinnison on 2008-10-03
Hello.:KS I have been struggling with this issue ever since I began trying to use linux: all the last week.
I am a totally new user to linux, I know no commands, so if you tell me "do this or that" you will probably have to tell me what commands I need to use, too.
:confused:
Since this is such a long story, I am going to copy and paste my post from the related launchpad bug here:
[https://answers.launchpad.net/ubuntu/+question/46500](https://answers.launchpad.net/ubuntu/+question/46500)

:guitar:
Here we go:

I have the same problem. (Black screen of death after installing ati driver: cant do anything, system locks after the reboot, and one is forced to "repair" packages/ x from recovery mode just to get a workable system).

Ubuntu hardy 8.04
Kernel 2.6.24-19 (generic)
Gnome 2.22.3
Pentium 4 3,2Ghz
1GB system RAM
Graphics Card: Sapphire ATI Radeon X1950PRO 512MB AGP
Monitor: A samsung Synmaster 710v. Its lcd and supports up to 1280x1024@72hz.

My first ubuntu experience ever was to see a message about installing ati restricted graphics driver, installed that, got balck screen of death.
Then I reinstalled os (i didnt know of repair options from recovery mode then), tried various fixes, nothing seemed to work.

In the end I used EnvyNG (google it, it is a util that auto-detects and installs nvidia and ati drivers taking care of dependencies, previous rivers uninstallations etc. for you) and although at the start things appeared normal, it turns out there are still many driver-related problems for me.

First off, if I enable desktop effects from system->Preferences->Appearance, they are activated and I can see them, but any video playback or 3d screensaver flickers badly. Disabling them cures the problem.
(This particular issue is supposedly fixed if you change/add a "TexturedVideo=" entry to be false. Not sure what file you are supposed to do that on.

Also, I have noticed that on youtube if I try to open a video in fullscreen then mozilla abrubtly terminates, immediately, before even a single video frame can be rendered on the screen.

if I type lspci I get
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
which looks ok...

running glxgears by typing glxgears in terminal results in:
Segmentation Fault
but, if I run it as "sudo glxgears" I get:
27903 frames in 5.0 seconds = 5580.405 FPS
27885 frames in 5.0 seconds = 5576.956 FPS
27080 frames in 5.0 seconds = 5415.896 FPS
(this while my system is otherwise not especially busy)

I tried to install and run some 3d games to get a better feel for the situation of my 3d acceleration.
Alien Arena 2008 is a popular open source FPS game, and although it is obvious it does not require high-end hardware, it run painfully slow. This same video card can run Unreal Tournament 3 decently on my Windows partition so its not hardware that causes the exteremely low fps, but a driver issue.

I tried to install the demo of another popular game, EnemyTerritory: Quake Wars (ETQW). I only managed to run it once, that time the main menu appeared but it was in a horrible resolution making text almost unreadable. I tried to change res to a higher one (supported by my monitor) and the screen got all meshed up and I couldnt make out anything. Afterwards I have not been able to run it again. Here is the output the game produced while trying to run.

...
...
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
execing 'autoexec.cfg'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1280x768 1280x720 1152x864 1024x768 800x600 640x480 640x400 400x300 320x240
320x200
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082cc6d1]
[0x082bc82f]
[0xb7f8a440]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()

^the above are lines that appeared on my terminal when I tried to start the game with a command.

Now, if I type
$ fglrxinfo I get
Segmentation fault
but if I type:
$ sudo fglrxinfo
[sudo] password for kinnison:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7659 Release

Also, $ glxinfo gives Segmentation fault, but

$ sudo glxinfo
name of display: :0.0
display: :0 screen: 0
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
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7659 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_WIN_swap_hint, WGL_EXT_swap_control

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
0x47 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x48 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x49 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x4a 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
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
0x6f 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x70 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x71 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x72 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x89 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 4 1 Ncon

My curernt xorg.conf file is as follows:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
 Identifier "Default Layout"
 Screen 0 "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
 Load "glx"
 Load "GLcore"
 Load "v4l"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
 VendorName "Generic LCD Display"
 ModelName "LCD Panel 1280x1024"
 HorizSync 31.5 - 64.0
 VertRefresh 56.0 - 65.0
 Gamma 1
 ModeLine "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
 ModeLine "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
 ModeLine "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
 ModeLine "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
 ModeLine "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
 ModeLine "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
 Identifier "monitor1"
 Gamma 1
EndSection

Section "Device"
 Identifier "Configured Video Device"
 Driver "fglrx"
 VendorName "ATI"
 BoardName "ATI Radeon"
 Option "VideoOverlay" "on"
 Option "OpenGLOverlay" "off"
 Option "EnableMonitor" "crt1"
 BusID "PCI:1:0:0"
EndSection

Section "Device"
 Identifier "device1"
 Driver "fglrx"
 BoardName "VESA driver (generic)"
 Option "VideoOverlay" "on"
 Option "OpenGLOverlay" "off"
 BusID "PCI:1:0:1"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "Configured Video Device"
 Monitor "Configured Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
 EndSubSection
EndSection

Section "Screen"
 Identifier "screen1"
 Device "device1"
 Monitor "monitor1"
 DefaultDepth 24
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection

So far, all of the above are, I suppose, similar to what everyone else has experienced, and while there is a huge amount of people going crazy over this, there are some few individuals that changing this or that manage to get things going. However, usually their "fixes" only work on their own machines.

Searching for support or information for gaming in linux in general, I came across the website of linux-gamers.net.
These people have created several versions of "Linux Gamers Live DVDs" which are standalone Linux installments that can run from a dvd with no hard drive interaction, and include various free games that you can launch right from your live session. So I burned one such disk and run it in order to see how they have set up drivers. After all there are a lot of cards affected by this issue, and surely they must have a fault-free system for utilizing graphics cards with their "distributions".

And I am glad that I did this, because it turns out I can play almost all of the 3D games they have in that .iso without problems, with the proprietary ati driver that their installer uses when it detects my card (because, as they say, the open source driver hasnt achieved 3d acceleration in these series of cards yet).
The only problem is that I didnt get sound, which is irelevant since on my normal ubuntu installation I have it working perfectly, its just that I dont know the commands by hard.

I run a few commands while in a linux-gamers live session to try and see where the problem was.
The most important, perhaps, thing is that I didnt have to type sudo before my commands to get things going.
I didnt know how to write a log of these on disk but I wrote them down in a piece of paper. Here is what I wrote down:
glx gears gave me around 5000 fps.
fglrxinfo
display: 0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7873

glxinfo
direct rendering: Yes
glxvendor string: SGI
glx version string: 1.2
client glx: SGI
client glx version: 1.4
clx version: 1.2

lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV750 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display Controller: ATI Technologies Inc RV750 [Radeon X1950 Pro] (Secondary)
.

Am I not right the above lines that I saw in the live sessions of linuxgamers dvd are very similar if not the same with my own current ones? Only some version numbers are a bit diferent (openGL version string 2.1.7873).

So doesn't that mean it has something to do with superuser permissions? Or would that be just for my own individual case?
I saw, before, somewhere on the net, I think it was ubuntuforums.org, a code that would deal with permissions, not sure if it was for xorg.conf or another file, that adressed, supposedly, this issue.

Please, any help? I think I am close to getting at least my own system running correctly. But hopefully, there is something here that will solve the problem for everyone else too???? One can dream :):popcorn:

---

### Post by markbuntu on 2008-10-03
First of all, don't totally despair of the situation. Since amd bought ati they have been making a concerted effort to get their linux drivers up to par with the windows drivers but this takes time. They expect to have this done by about Feb next year. Anyway, the driver from Envy is the 8.6 driver and the newest is 8.9. The best way to install that is to follow these directions very carefully:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here, be very careful with these, some may or may not work with your card, they are not at all official but they will tell you how to configure the ati driver with xorg.conf:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Release notes for 8.9

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)

Release notes for 8.8

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

Release notes for 8.7

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html)

Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

OpenGL updates are included in the driver updates as they can do it.

---

