---
title: "flightgear grinds system to a halt - ATI card issue?"
date: 2008-11-24
forum: General Help
---

### Post by rawlins02 on 2008-11-24
Running 7.10 Gutsy Gibon. I installed flightgear through add/remove.  When I start, the splash screen comes up, but the cursor barely responds...seems like something is dragging heavily on resources (?)  

My machine is a Lenova T60.  ATI Mobility Radeon X1300 card. Intel Core Duo processor T2400, 1.83GHz, 667MHz FSB, 2MB. 

In the past I've add good success with Flightgear on a machine with an NVIDIA card.  I've got Flightgear working on my Windows partition, but prefer to have it running on linux side.  Any ideas?  Something maybe to do with direct rendering (glxinfo says no).

Thanks. 

> glxgears
6020 frames in 5.0 seconds = 1195.771 FPS
6102 frames in 5.1 seconds = 1199.728 FPS

> glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbo
se)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:

<snipped rest of glxinfo>

---

### Post by rawlins02 on 2008-11-25
Not many views of this thread and no replies. Hum..???

I notice that when FG starts, top command shows Xorg using 99% of CPU. Should that be so?

I played around with System -> Preferences -> Appearance -> Visual Effects

It is set to None, and Normal and Extra both result in an error about "Desktop Effects Could Not Be Enabled"

Does this suggest a problem with graphics setup needed to run FG ?

---

### Post by the.scarecrow on 2009-01-05
Have you tried looking in System>Administration>Hardware Drivers to see if Ubuntu is giving you the choice of using proprietary drivers for your graphics card?

You may have had to add restricted-extras to Synaptic to get the choice of using ATI rather than Linux default drivers.

---

