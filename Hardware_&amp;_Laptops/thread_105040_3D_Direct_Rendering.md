---
title: "3D Direct Rendering"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by Dynotrick on 2005-12-17
I have an ATI 300X card.    I thought that I had the ATI drivers installed correctly, but all 3D programs run VERY slow (tuxracer, GL screensavers, ect)  

Here is the results of glxinfo: 

```
justin@justinubuntu:~$ /usr/bin/glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
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

fgl_glxgears:

```
justin@justinubuntu:~$ /usr/X11R6/bin/fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

and finally :

```
justin@justinubuntu:~$ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f23000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7ead000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e83000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e61000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d33000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c73000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c66000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c54000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c50000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b6a000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b5f000)
        /lib/ld-linux.so.2 (0xb7fd3000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b5c000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b58000)

```

I have read through the various HOW TOs and other threads, but can't seem to figure out what to do in my case.

---

### Post by Dynotrick on 2005-12-31
no help guys?  I really can't figure this one out.

---

### Post by Selmi on 2005-12-31
check lsmod if fglrx module is running when you are in X

if not then try to find why - now i don't use fglrx drivers but before i had to insert 'modprobe fglrx' to startup scripts or to modules.conf

if fglrx module is available and it still doesn't work you will have to look to kernel logs and X server log, you may find something interesting there (on my old computer i had to set fglrx to not use built-in agp driver but agpgart - nforce2 chipset)

maybe some of these will help...

---

