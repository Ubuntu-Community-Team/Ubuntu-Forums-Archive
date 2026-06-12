---
title: "Ati 9200 SE :) and Edgy"
date: 2009-07-08
forum: Hardware
---

### Post by gregg128 on 2009-07-08
I am trying to set up an old PC with an ATI 9200 SE. The only ubuntu distro to support ati's 8.28.8 drivers (the last driver to support 9200) is edgy  6.10. So i installed it (mint bianca version) and tried to install fglrx driver with no success:

```
root@mint2:/home/grigory# dpkg -l |grep fglrx
ii  fglrx-control                              8.28.8+2.6.17.9-12.4                 Control panel for the ATI graphics accelerators
ii  xorg-driver-fglrx                          7.1.0-8.28.8+2.6.17.9-12.4           Video driver for ATI graphics accelerators
```
 ```
dpkg -l |grep restr
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1                        Non-free Linux 2.6.17 modules on x86_64 generic
ii  linux-restricted-modules-common            2.6.17.7-10.1                        Non-free Linux 2.6.17 modules helper script
ii  linux-restricted-modules-generic           2.6.17.10                            Restricted Linux modules for generic kernels
```

```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```


```
root@mint2:/home/grigory# glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
```

```
# modprobe fglrx
FATAL: Error running install command for fglrx
```

Xorg.conf and xorg log are attached.

[SIZE="3"]_Please help! Tnx in advance._[/SIZE]

---

### Post by ajgreeny on 2009-07-08
I run a computer with an ati 9200SE card and it is well supported by the open source ati/radeon driver that comes with jaunty, running compiz without a problem, and also did with hardy, if I remember correctly.  Is there a good reason for using edgy?  It is no longer supported and there will be no updates for it in future.  See if you can get jaunty to try instead and you may find that the graphics card is as good as you need without installing any drivers for it.

---

### Post by gregg128 on 2009-07-08
i have a jaunty installation on the same PC in mulitboot. But I can not get enough fps from the open source driver to play UrbanTerror :) 
Jaunty seem to run too slow on this machine too. So i would like to set up proprietary driver.

---

### Post by csyckad on 2009-07-22
> **ajgreeny said:**
> I run a computer with an ati 9200SE card and it is well supported by the open source ati/radeon driver that comes with jaunty, running compiz without a problem, and also did with hardy, if I remember correctly.  Is there a good reason for using edgy?  It is no longer supported and there will be no updates for it in future.  See if you can get jaunty to try instead and you may find that the graphics card is as good as you need without installing any drivers for it.


can u post the xorg.conf and tell me how to install it. Thanks

---

