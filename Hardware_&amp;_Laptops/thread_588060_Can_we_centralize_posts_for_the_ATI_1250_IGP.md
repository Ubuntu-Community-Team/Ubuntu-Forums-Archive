---
title: "Can we centralize posts for the ATI 1250 IGP?"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by Nikos.Alexandris on 2007-10-23
Hi all!

Could we try to unify posts for the ATI 1250 IGP graphic card for laptops (...which is actually a "tough" one) ? If I am not wrong, there are several machines with this graphic card. And there are several threads waiting for a solution upon this device.

Details about the graphic card: [http://ati.amd.com/products/Radeonxpress1250mob/index.html](http://ati.amd.com/products/Radeonxpress1250mob/index.html)

Some threads related with ATI 1250 IGP (and with the laptop Samsung R20):

[http://ubuntuforums.org/showthread.php?t=396751](http://ubuntuforums.org/showthread.php?t=396751)

[http://ubuntuforums.org/showthread.php?t=551046&highlight=r20+ati+1250](http://ubuntuforums.org/showthread.php?t=551046&highlight=r20+ati+1250)

[http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+1250](http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+1250)

[http://ubuntuforums.org/showthread.php?t=503695&highlight=ati+1250](http://ubuntuforums.org/showthread.php?t=503695&highlight=ati+1250)


Greetings... !:guitar:

---

### Post by Nikos.Alexandris on 2007-10-24
Well,

I will reply to myself (again!)... !

I upgraded to gutsy. No troubles ;)

The fglrx driver supports the ATI 1250 IGP.

Although I am not sure about 3D acceleration... I will check it.

.

Now, trying to attach an external DELL monitor (analog connection) is a bit of a headache.

---

### Post by Nikos.Alexandris on 2007-10-25
In the end there were more problems... trying to set the proper screen resolution for the laptop monitor and the external lcd monitor.

I found on a post that the new ATI driver (8.42.somethiing) works... but I couldn't trace the 1250 model anywhere. I gave it a shot anyway and... it works!

Currently I can't bring the system to recognize that there is a laptop lcd monitor and it works as if there is an external lcd panel connected!

The ATI Catalyst doesn't work also.

---

### Post by Nikos.Alexandris on 2007-10-25
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

It works... allthough the fglrxinfo command gives the following output:

nik@vertical:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress **1200** Series **[COLOR="Red"](and not 1250!)[/COLOR]**
OpenGL version string: 2.0.6958 Release

---

### Post by Nikos.Alexandris on 2007-10-25
Well,

maybe there is no really need to centralize posts for the 1250 IGP graphic card. Still, I read many different threads seeking the same solution !

In any case the unofficial ATI wiki guide seems to be reliable.

---

### Post by Nikos.Alexandris on 2007-10-27
A quite new external link... [https://groups.google.com/group/x1250/](https://groups.google.com/group/x1250/)

For those who own 1250!

---

### Post by Nikos.Alexandris on 2007-10-27
Last update:[COLOR="Red"][SIZE="3"]**Well... look in the last post!**[/SIZE][/COLOR]

---

### Post by browner12 on 2007-10-28
I have the same card (integrated to the motherboard) and the exact same problem.

I have fglrx working with just one monitor. whenever i get the second monitor working correct, I cannot log into X anymore.  just lags and sends me back to login.

just to mess around, i added this single line to my device section of xorg.conf
OPTION "desktoplayout" "horizontal"

logged out, dual monitors worked great! but couldn't log into X again.  how can this one line of code change enough to stop X?

is this a limitation of our card? or of the current driver? or is there actually a solution somewhere out there?

---

### Post by Nikos.Alexandris on 2007-10-29
Hi browner12!

I am really no expert. Reading stuff in the net is what I do and I suppose it has to do with the driver! I just keep on reading...

---

### Post by Nikos.Alexandris on 2007-10-30
**[SIZE="4"][COLOR="Red"]THIS IS NOT A HOW-TO! ---*[SIZE="2"][B][COLOR="Blue"]Because it doesn't fix everything![/COLOR]**[/SIZE]*

It's a collage of information spreaded in the forum and elsewhere to setup dual monitor for ATI 1250 (of course) tested om Samsung R20 laptop.[/COLOR][/SIZE][/B]

**[SIZE="2"]Attached is a *functional*****[COLOR="Red"](?)[/COLOR]** **xorg.conf** (mainly generated automatically using the aticonfig command)[/SIZE]**[COLOR="Blue"][SIZE="2"]in case you have messed up your X (like me) and care only for a dual monitor setting without 3D effects, yet with the option to enable effects if using only your laptop.[/SIZE][/COLOR]**[U]

**[COLOR="Black"]In addition, attached are the results of the fglrxinfo, glxinfo and the FramesPerSeconds demos... in the end of this post.[/COLOR]**(**[COLOR="Red"][SIZE="2"]VERY LONG TEXT![/SIZE][/COLOR]**)

**[SIZE="4"]Pre-requisities:[/U][/SIZE]**

[B]. Access to the internet :)

.The new ATI driver 8.42.3 (!)

. Follow the Unofficial ATI wiki page [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

. **Read the aticonfig help file ** ```
aticonfig --help | less
```


[SIZE="4"]_Result:_[/SIZE]
[B]
+ Dual Monitor support (External monitor on top) [COLOR="Red"]without 3D effects[/COLOR]

- A bit slower than normal and the message (whenever run the **fglrxinfo** command) "*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062068 *** ... ... ... ... Aborted (core dumped)" 

+ With 3D effects enabled when using only laptop monitor at full speed!.[/B] ---[COLOR="Blue"]** Video is a bit strange at full screen sometimes. The same with googleearth...**[/COLOR] (it uses OpenGL -- doesn't it?)


[SIZE="4"]Implementation:[/SIZE]

1. Uninstall everything according to the **[COLOR="Red"]post #8[/COLOR]** (of michael37) entitled: [SIZE="3"]If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before[/SIZE] in the thread [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+1250[/COLOR]]("http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+1250")

**Apply steps 1 to 4 ** ( and [SIZE="3"][COLOR="Red"]Don't install xserver-xgl[/COLOR][/SIZE][/B] )  and   **steps 8 to 10**

2. Kill X (Alt+Ctrl+Backspace) and try to login (...before you try to shutdown violently your system try all alternative tty's... that is **Alt+Ctrl+[COLOR="Red"]F7[/COLOR]** or ...+**[COLOR="Red"]F8[/COLOR]** or ...+**[COLOR="Red"]F9[/COLOR]** -- It happened that **gdm** was starting in tty9). If your system doesn't react... then try to shut it down just by pressing the famous **[COLOR="Blue"][COLOR="Red"]Alt+Ctrl+Del[/COLOR][/COLOR]**. If it's frozen then... shut it somehow down! (The latter is sure not the best way of course).

**** In case you can't login in GDM just boot in recovery mode ****

3. Follow the 2nd method as described in [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

4. **[COLOR="Red"]Don't forget to add fglrx in compiz's whitelist![/COLOR]**

5. Login and and try various commands to enable/ disable on the fly your monitors.

***** It's all written in the help. -- READ IT and try out. *****

...

[SIZE="3"]Here is the **xorg.conf** (I excluded the non-video related sections!)[/SIZE]

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" Above "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "v4l"
	Load  "dbe"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "lvds,crt1"
#	Option	    "UseFastTLS" "2"
	Option	    "DesktopSetup" "clone"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"

#	Option	    "XaaNoOffscreenPixmaps"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection
```


I copy-paste also a very long text with the result of **fglrxinfo**, **glxinfo** and the respectice **FPS** demos **when both monitors work with the correct resolution** **and without the effects working.**

[SIZE="4"]**[COLOR="Blue"]WHERE IS THE PROBLEM?[/COLOR]**[/SIZE]

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062068 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d25d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d29800]
/usr/lib/dri/fglrx_dri.so[0xb79d0c92]
/usr/lib/libGL.so.1[0xb7f35c61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7e347d5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7e40df6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7e2deea]
fglrxinfo[0x8048a3b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cd2050]
fglrxinfo[0x80488f1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:02 1720470    /usr/bin/fglrxinfo
0804b000-0804c000 rw-p 00002000 08:02 1720470    /usr/bin/fglrxinfo
0804c000-08916000 rw-p 0804c000 00:00 0          [heap]
950b2000-950b3000 rw-p 950b2000 00:00 0 
95ef5000-95ef7000 rw-s 00002000 00:0e 19343      /dev/dri/card0
95ef7000-a5ef7000 rw-s 00003000 00:0e 19343      /dev/dri/card0
a5ef7000-a5f0b000 rwxp a5ef7000 00:00 0 
a5f0b000-a61cd000 rw-p a5f0b000 00:00 0 
a61cd000-a61d2000 rwxp a61cd000 00:00 0 
a61d2000-a654d000 rw-p a61d2000 00:00 0 
a654d000-a655e000 rwxp a654d000 00:00 0 
a655e000-a65d1000 rw-p a655e000 00:00 0 
a65d1000-a6cd1000 rw-s 00005000 00:0e 19343      /dev/dri/card0
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6cb0000-b6cba000 r-xp 00000000 08:02 2146366    /lib/libgcc_s.so.1
b6cba000-b6cbb000 rw-p 0000a000 08:02 2146366    /lib/libgcc_s.so.1
b6cd1000-b6cf4000 r-xp 00000000 08:02 2146329    /lib/tls/i686/cmov/libm-2.6.1.so
b6cf4000-b6cf6000 rw-p 00023000 08:02 2146329    /lib/tls/i686/cmov/libm-2.6.1.so
b6cf6000-b6cfd000 r-xp 00000000 08:02 2146341    /lib/tls/i686/cmov/librt-2.6.1.so
b6cfd000-b6cff000 rw-p 00006000 08:02 2146341    /lib/tls/i686/cmov/librt-2.6.1.so
b6cff000-b7ab8000 r-xp 00000000 08:02 2131074    /usr/lib/dri/fglrx_dri.so
b7ab8000-b7b3d000 rw-p 00db9000 08:02 2131074    /usr/lib/dri/fglrx_dri.so
b7b3d000-b7c98000 rw-p b7b3d000 00:00 0 
b7c98000-b7c9a000 r-xp 00000000 08:02 2146328    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9a000-b7c9c000 rw-p 00001000 08:02 2146328    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9c000-b7ca0000 r-xp 00000000 08:02 1725446    /usr/lib/libXdmcp.so.6.0.0
b7ca0000-b7ca1000 rw-p 00003000 08:02 1725446    /usr/lib/libXdmcp.so.6.0.0
b7ca1000-b7ca3000 r-xp 00000000 08:02 1721860    /usr/lib/libXau.so.6.0.0
b7ca3000-b7ca4000 rw-p 00001000 08:02 1721860    /usr/lib/libXau.so.6.0.0
b7ca4000-b7cb8000 r-xp 00000000 08:02 2146339    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cb8000-b7cba000 rw-p 00013000 08:02 2146339    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cba000-b7cbc000 rw-p b7cba000 00:00 0 
b7cbc000-b7e00000 r-xp 00000000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7e00000-b7e01000 r--p 00143000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7e01000-b7e03000 rw-p 00144000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7e03000-b7e06000 rw-p b7e03000 00:00 0 
b7e06000-b7e13000 r-xp 00000000 08:02 1730965    /usr/lib/libXext.so.6.4.0
b7e13000-b7e14000 rw-p 0000d000 08:02 1730965    /usr/lib/libXext.so.6.4.0
b7e14000-b7e15000 rw-p b7e14000 00:00 0 
b7e15000-b7f02000 r-xp 00000000 08:02 1721904    /usr/lib/libX11.so.6.2.0
b7f02000-b7f06000 rw-p 000ed000 08:02 1721904    /usr/lib/libX11.so.6.2.0
b7f06000-b7f8c000 r-xp 00000000 08:02 1754459    /usr/lib/xorg/libGL.so.1.2
b7f8c000-b7f8e000 rw-p 00086000 08:02 1754459    /usr/lib/xorg/libGL.so.1.2
b7f8e000-b7f90000 rw-p b7f8e000 00:00 0 
b7f90000-b7f94000 rwxp b7f90000 00:00 0 
b7f94000-b7fa4000 rw-s 00004000 00:0e 19343      /dev/dri/card0
b7fa6000-b7fa8000 rw-p b7fa6000 00:00 0 
b7fa8000-b7fc2000 r-xp 00000000 08:02 2146430    /lib/ld-2.6.1.so
b7fc2000-b7fc4000 rw-p 00019000 08:02 2146430    /lib/ld-2.6.1.so
bffa9000-bffbd000 rwxp bffa9000 00:00 0          [stack]
bffbd000-bffbe000 rw-p bffbd000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

**[COLOR="Blue"][SIZE="4"]glxinfo[/SIZE][/COLOR]**
```
$ glxinfo 
name of display: :0.1
display: :0  screen: 0
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0xe7 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


display: :0  screen: 1
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x86 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x87 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x88 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x89 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x8a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8d 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8e 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x8f 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x90 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x91 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x92 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x93 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x94 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x95 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x96 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x97 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x98 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x99 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x9a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9b 24 tc  0 Don't install xserver-xgl32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x9d 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x9e 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x9f 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xa0 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xa1 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xa2 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa3 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa4 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xa5 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xa6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xa7 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xa8 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xa9 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xaa 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xab 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xac 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xad 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xae 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xaf 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xb0 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xb1 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xb2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb3 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb5 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb6 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xb7 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xb8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xb9 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xba 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbb 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbc 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbd 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbe 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xbf 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xc0 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xc1 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xc2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc3 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc5 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc6 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xc7 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xc8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xc9 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xca 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xcb 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xcc 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xcd 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xce 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xcf 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0xd0 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xd1 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xd2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xd3 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xd4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd5 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe8 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
*** glibc detected *** glxinfo: double free or corruption (!prev): 0x08063068 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e5dd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e61800]
/usr/lib/dri/fglrx_dri.so[0xb7a08c92]
/usr/lib/libGL.so.1[0xb7f6dc61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7d217d5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7d2ddf6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7d1aeea]
glxinfo[0x8049891]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e0a050]
glxinfo[0x8048d51]
======= Memory map: ========
08048000-0804c000 r-xp 00000000 08:02 1725625    /usr/bin/glxinfo
0804c000-0804d000 rw-p 00004000 08:02 1725625    /usr/bin/glxinfo
0804d000-08917000 rw-p 0804d000 00:00 0          [heap]
95f2c000-95f2e000 rw-s 00002000 00:0e 19343      /dev/dri/card0
95f2e000-a5f2e000 rw-s 00003000 00:0e 19343      /dev/dri/card0
a5f2e000-a5f42000 rwxp a5f2e000 00:00 0 
a5f42000-a6204000 rw-p a5f42000 00:00 0 
a6204000-a6208000 rwxp a6204000 00:00 0 
a6208000-a6583000 rw-p a6208000 00:00 0 
a6583000-a6589000 rwxp a6583000 00:00 0 
a6589000-a65fc000 rw-p a6589000 00:00 0 
a65fc000-a6cfc000 rw-s 00005000 00:0e 19343      /dev/dri/card0
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6cdb000-b6ce5000 r-xp 00000000 08:02 2146366    /lib/libgcc_s.so.1
b6ce5000-b6ce6000 rw-p 0000a000 08:02 2146366    /lib/libgcc_s.so.1
b6cfc000-b6d1f000 r-xp 00000000 08:02 2146329    /lib/tls/i686/cmov/libm-2.6.1.so
b6d1f000-b6d21000 rw-p 00023000 08:02 2146329    /lib/tls/i686/cmov/libm-2.6.1.so
b6d21000-b6d27000 rwxp b6d21000 00:00 0 
b6d27000-b6d37000 rw-s 00004000 00:0e 19343      /dev/dri/card0
b6d37000-b7af0000 r-xp 00000000 08:02 2131074    /usr/lib/dri/fglrx_dri.so
b7af0000-b7b75000 rw-p 00db9000 08:02 2131074    /usr/lib/dri/fglrx_dri.so
b7b75000-b7cd0000 rw-p b7b75000 00:00 0 
b7cd0000-b7cd2000 r-xp 00000000 08:02 2146328    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cd2000-b7cd4000 rw-p 00001000 08:02 2146328    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cd4000-b7cd8000 r-xp 00000000 08:02 1725446    /usr/lib/libXdmcp.so.6.0.0
b7cd8000-b7cd9000 rw-p 00003000 08:02 1725446    /usr/lib/libXdmcp.so.6.0.0
b7cd9000-b7cdb000 r-xp 00000000 08:02 1721860    /usr/lib/libXau.so.6.0.0
b7cdb000-b7cdc000 rw-p 00001000 08:02 1721860    /usr/lib/libXau.so.6.0.0
b7cdc000-b7ce9000 r-xp 00000000 08:02 1730965    /usr/lib/libXext.so.6.4.0
b7ce9000-b7cea000 rw-p 0000d000 08:02 1730965    /usr/lib/libXext.so.6.4.0
b7cea000-b7cfe000 r-xp 00000000 08:02 2146339    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cfe000-b7d00000 rw-p 00013000 08:02 2146339    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d00000-b7d02000 rw-p b7d00000 00:00 0 
b7d02000-b7def000 r-xp 00000000 08:02 1721904    /usr/lib/libX11.so.6.2.0
b7def000-b7df3000 rw-p 000ed000 08:02 1721904    /usr/lib/libX11.so.6.2.0
b7df3000-b7df4000 rw-p b7df3000 00:00 0 
b7df4000-b7f38000 r-xp 00000000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7f38000-b7f39000 r--p 00143000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7f39000-b7f3b000 rw-p 00144000 08:02 2146325    /lib/tls/i686/cmov/libc-2.6.1.so
b7f3b000-b7f3e000 rw-p b7f3b000 00:00 0 
b7f3e000-b7fc4000 r-xp 00000000 08:02 1754459    /usr/lib/xorg/libGL.so.1.2
b7fc4000-b7fc6000 rw-p 00086000 08:02 1754459    /usr/lib/xorg/libGL.so.1.2
b7fc6000-b7fc8000 rw-p b7fc6000 00:00 0 
b7fc8000-b7fd2000 rwxp b7fc8000 00:00 0 
b7fd4000-b7fdb000 r-xp 00000000 08:02 2146341    /lib/tls/i686/cmov/librt-2.6.1.so
b7fdb000-b7fdd000 rw-p 00006000 08:02 2146341    /lib/tls/i686/cmov/librt-2.6.1.so
b7fdd000-b7fe0000 rw-p b7fdd000 00:00 0 
b7fe0000-b7ffa000 r-xp 00000000 08:02 2146430    /lib/ld-2.6.1.so
b7ffa000-b7ffc000 rw-p 00019000 08:02 2146430    /lib/ld-2.6.1.so
bfc31000-bfc45000 rwxp bfc31000 00:00 0          [stack]
bfc45000-bfc46000 rw-p bfc45000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

[SIZE="4"]**[COLOR="Blue"]FPS?[/COLOR]**[/SIZE]
```

$ fgl_glxgears -display :0
Using GLX_SGIX_pbuffer
3995 frames in 5.0 seconds = 799.000 FPS
4977 frames in 5.0 seconds = 995.400 FPS
5226 frames in 5.0 seconds = 1045.200 FPS
5230 frames in 5.0 seconds = 1046.000 FPS
5233 frames in 5.0 seconds = 1046.600 FPS
5238 frames in 5.0 seconds = 1047.600 FPS
5257 frames in 5.0 seconds = 1051.400 FPS
5191 frames in 5.0 seconds = 1038.200 FPS
5243 frames in 5.0 seconds = 1048.600 FPS
5229 frames in 5.0 seconds = 1045.800 FPS

$ fgl_glxgears -display :1
Error: couldn't open display :1

$ glxgears -display :0
18153 frames in 5.0 seconds = 3630.542 FPS
17424 frames in 5.0 seconds = 3484.730 FPS
18536 frames in 5.0 seconds = 3707.167 FPS
18459 frames in 5.0 seconds = 3691.746 FPS
18382 frames in 5.0 seconds = 3676.232 FPS
18528 frames in 5.0 seconds = 3705.527 FPS
18378 frames in 5.0 seconds = 3675.579 FPS
18316 frames in 5.0 seconds = 3663.027 FPS
18358 frames in 5.0 seconds = 3671.470 FPS
18374 frames in 5.0 seconds = 3674.786 FPS

$ glxgears -display :1
Error: couldn't open display :1

$ glxheads :0
Name: :0
  Display:     0x805e008
  Window:      0x3600003
  Context:     0x82c5378
  GL_VERSION:  2.0.6958 Release
  GL_VENDOR:   ATI Technologies Inc.
  GL_RENDERER: ATI Radeon Xpress 1200 Series

$ glxheads :1
Error on display :1 - Unable to open display
```

---

