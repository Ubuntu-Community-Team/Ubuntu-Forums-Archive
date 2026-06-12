---
title: "Direct Rendering..."
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by nsasch on 2005-04-15
(Keep in mind, this is my first post at ubuntuforums.org)
I have had Direct Rendering work perfectly in a previous install(Gentoo 2004)
Here are some important parts of output from things:
lsmod:
drm                    59412  2 radeon
agpgart                31784  2 via_agp,drm
via_agp                 9216  1

scanpci -v:
pci bus 0x0000 cardnum 0x05 function 0x00: vendor 0x1002 device 0x5157
 ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
 CardVendor 0x1002 card 0x013b (ATI Technologies Inc, Card unknown)
  STATUS    0x0290  COMMAND 0x0087
  CLASS     0x03 0x00 0x00  REVISION 0x00
  BIST      0x00  HEADER 0x00  LATENCY 0x20  CACHE 0x08
  BASE0     0xd0000008  addr 0xd0000000  MEM PREFETCHABLE
  BASE1     0x0000e801  addr 0x0000e800  I/O
  BASE2     0xdfff0000  addr 0xdfff0000  MEM
  BASEROM   0xdffc0000  addr 0xdffc0000  not-decode-enabled
  MAX_LAT   0x00  MIN_GNT 0x08  INT_PIN 0x01  INT_LINE 0x00

LIBGL_DEBUG=verbose
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 4.0.1 radeon (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/radeon_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/radeon_dri.so failed (/usr/X11R6/lib/modules/dri/radeon_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: radeon_dri.so
libGL: XF86DRIGetClientDriverName: 4.0.1 radeon (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/radeon_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/radeon_dri.so failed (/usr/X11R6/lib/modules/dri/radeon_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: radeon_dri.so
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
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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

However, in /var/log/Xorg.0.log:
(II) RADEON(0): Direct rendering enabled

Thank you in advance,
~nasch

---

