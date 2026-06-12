---
title: "XUbuntu 15.10 - AMD R7 240"
date: 2016-04-26
forum: Hardware
---

### Post by unrealpg on 2016-04-26
Hi,
I am desperately trying to resolve my final issue with my media center set-up. 
Essentially, it appears that my graphics card is not functional with Ubuntu.

I have the following card:
[http://www.sapphiretech.com/productdetial.asp?pid=E717FBC3-11C2-43E3-A216-291B8BCBC5F4&lang=eng](http://www.sapphiretech.com/productdetial.asp?pid=E717FBC3-11C2-43E3-A216-291B8BCBC5F4&lang=eng)

The rest of the hardware:
[http://www8.hp.com/uk/en/products/proliant-servers/product-detail.html?oid=5379860#!tab=specs](http://www8.hp.com/uk/en/products/proliant-servers/product-detail.html?oid=5379860#!tab=specs) (the celeron processor)

I have attempted to install fglrx via 'Additional Drivers' this simply results in a black screen (then I am forced to purge fglrx) - I have attempted this several times.

Partial glxinfo:
```

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float,
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample,
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent,
    GLX_MESA_query_renderer, GLX_OML_swap_method, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_make_current_read
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
OpenGL version string: 3.0 Mesa 11.0.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:

```

lspci | grep VGA
```

07:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340]

```

Please let me know if you require further information and I will reply ASAP.
I am very keen to resolve this, however I have run out of ideas and could really use a hand (Kodi is unusable with software emulation, and its driving me crazy!)

Thank you.

P:S - I have also tried running 16.04 on a live USB and found that it also uses software emulation. The difference is - Obviously I don't have the option to use fglrx, so I guess I'll stick with 15.10 for now.

---

