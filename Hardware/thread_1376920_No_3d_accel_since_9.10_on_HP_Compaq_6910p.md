---
title: "No 3d accel since 9.10 on HP Compaq 6910p"
date: 2010-01-09
forum: Hardware
---

### Post by dapfy on 2010-01-09
On games like Tux racer, which used to race I get less than 1 fps since of Kubuntu 9.10 (a fresh install).

It did not install an **xorg.conf**, but since the defaults (while working except for 3D accel) complained about not finding the i810 driver, I had the server generate one, but that didn't improve 3D.  Just in case, I added these 1st two options in Device, but Accel gives a warning (see below):

```
Section "Device"
        Option     "Accel"            	"On"
        Option     "DRI"            	"On"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection
```

Some lines of **dmesg** which look relevant:

```
[    1.593893] Linux agpgart interface v0.103
[    1.613476] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.614600] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    1.617581] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.664053] [drm] Initialized drm 1.1.0 20060810
[    1.675403] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.675409] i915 0000:00:02.0: setting latency timer to 64
[    1.677903]   alloc irq_desc for 28 on node -1
[    1.677906]   alloc kstat_irqs on node -1
[    1.677916] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    2.529196] [drm] TV-16: set mode NTSC 480i 0
[    2.666172] [drm] fb0: inteldrmfb frame buffer device
[    2.669881] acpi device:02: registered as cooling_device7
[    2.670463] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    2.670487] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
[    2.670515] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
```

Some lines of /var/log/**Xorg.0.log** which look relevant:

```
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(--) PCI:*(0:0:2:0) 8086:2a02:103c:30be Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xe4400000/1048576, 0xd0000000/268435456, I/O @ 0x00004000/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Option "DRI" "On"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(II) intel(0): Manufacturer: SEC  Model: 4542  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): No DPMS capabilities specified
(WW) intel(0): Unknown vendor-specific block f
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "dri2"
(II) LoadModule: "dri2"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri2.so
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(WW) intel(0): Option "Accel" is not used
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
```

**glxinfo** says:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.6
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_map_buffer_range,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra,
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord,
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB,
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels,
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate,
    GL_ATI_envmap_bumpmap, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader,
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_resize_buffers,
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_fragment_program, GL_NV_light_max_exponent,
    GL_NV_point_sprite, GL_NV_texture_env_combine4, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

72 GLX Visuals
96 GLXFBConfigs:
```

all of which have caveat None or Slow

---

### Post by dapfy on 2010-01-13
Hi Folks!

what's wrong?  Did I stuff you with too many details?  Is it so obvious I should have found it myself?  Is it so inexplicable that nobody has a clue?

I saved the whole /etc from 9.04, before wiping it with 9.10, but the xorg.conf was almost empty.  I should have saved the /var/log/Xorg.0.log to see what was different, i.e. better, before, but alas I didn't.

Please help, thank you!

---

### Post by Yellow Pasque on 2010-01-14
The Xorg log looks fine.
```
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
```

Try:
```
LIBGL_DEBUG=verbose glxinfo
```
Maybe the first few lines will tell you why it's falling back to software 3D.

---

### Post by dapfy on 2010-01-16
That wasn't directly helpful, because it vaguely said it couldn't open the drm device, but strace told me what it was talking about:

```
open("/dev/dri/card0", O_RDWR)          = -1 EACCES (Permission denied)
```

That file needs group "video" which my user didn't have (funny: xine worked fine...)

Thank you very much for your help!
Daniel

---

