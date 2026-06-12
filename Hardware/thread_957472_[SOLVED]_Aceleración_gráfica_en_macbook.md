---
title: "[SOLVED] Aceleración gráfica en macbook"
date: 2008-10-24
forum: Hardware
---

### Post by jajajavi on 2008-10-24
Hola, me quedé sin aceleración gráfica.

```
$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

```
$ LIBGL_DEBUG=verbose glxinfo 
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Restauré el xorg.conf desde un backup y sigue pasando lo mismo. La placa de video es 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03). 

Agradezco todo tipo de ayuda.

---

### Post by hictio on 2008-10-24
Hola,
Un poco mas de info, por favor :)

Actualizaste el kernel?
Tuviste un crash?
Instalaste drivers nuevos?

---

### Post by sajnox on 2008-10-24
Es Intel, no tendrias que tener problema alguno.

Probaste con reconfigurar el xorg.conf?

Te vas a una consola ctrl + alt + f1 y te logueas

Paras al entorno grafico

```
sudo /etc/init.d/gdm stop
```

Reconfiguras el xorg (en el proceso te genera un backup del existente)

```
sudo dpkg-reconfigure -phigh xorg.conf
```

Reinicias gdm

```
startx
```

---

### Post by niko_3100 on 2008-10-24
es intel pero es mac :P  jajaj!! nah mentira, proba reinstalando los drivers de intel desde synaptics.

---

### Post by sajnox on 2008-10-24
> **niko_3100 said:**
> es intel pero es mac :P  jajaj!! nah mentira, proba reinstalando los drivers de intel desde synaptics.

Que drivers?? de Synaptic??

---

### Post by jajajavi on 2008-10-24
> **sajnox said:**
> 
Reconfiguras el xorg (en el proceso te genera un backup del existente)
```
sudo dpkg-reconfigure -phigh xorg.conf
```


y me dice

El paquete 'xorg.conf' no está instalado y no hay ninguna información disponible.

El kernel es el último, crash no hubo y no instalé drivers nuevos pero la cosa se complicó cuando instalé algo que modificó el xorg.conf, aunque lo restauré de un backup la aceleración gráfica jamás volvió. Los efectos de escritorio funcionan pero de una forma intermitentemente molesta.

Gracias a todos por la ayuda, buen fin de semana.

---

### Post by juanman on 2008-10-24
Deberia ser:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jajajavi on 2008-10-25
> **juanman said:**
> Deberia ser:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

gracias!

Pero sigue andando raro, incluso peor. No termina de hacer el barrido horizontal, por ejemplo en firefox al cambiar de tabs no las redibuja completamente, lo mismo pasa con menúes desplegables, la trasparentación de ventana es lenta pero puedo hacer rotar y sacudir el cubo perfectamente.

Restauro el xorg.conf del backup que hizo, reinicio y hago un LIBGL_DEBUG=verbose glxgears y me da alrededor de 90/100 FPS, repito el proceso que decía sajnox y me da como 180 FPS pero el cubo ahora es lentísimo. Entonces desactivo los efectos de escritorio pero hacer scroll sigue siendo tedioso.

Tal como lo contaba en [la lista de correo]("http://www.nabble.com/-ubuntu-ar--dibujado-de-pantalla-lento-td19982672.html") esto empezó cuando instalé algo que actualizó xserver-xorg-input-synaptics.

---

### Post by hictio on 2008-10-25
> **jajajavi said:**
> gracias!
Tal como lo contaba en [la lista de correo]("http://www.nabble.com/-ubuntu-ar--dibujado-de-pantalla-lento-td19982672.html") esto empezó cuando instalé algo que actualizó xserver-xorg-input-synaptics.

Hace cuantos dias fue?
Podes chequear el log '/var/log/dpkg.log' y ve que mas se puede haber instalado, aparte de lo de Synaptics?
Ya chequeate el log de X Window ('/var/log/Xorg.0.log'), a ver si tiene algo que aportar?
Haceles un less en un Terminal, o abrilos con gedit.

---

### Post by sajnox on 2008-10-25
> **juanman said:**
> Deberia ser:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Gracias, eso me pasa por escribir comandos desde otros sistemas operativos

---

### Post by faktorqm on 2008-10-27
```
sudo displayconfig-gtk
```

---

### Post by jajajavi on 2008-10-27
> **faktorqm said:**
> ```
sudo displayconfig-gtk
```

se abre el menú para configurar las pantallas pero no veo nada que aporte soluciones para este problema. gracias de todos modos.-

---

### Post by faktorqm on 2008-10-27
Se supone que mediante ese programa tenes que estar seguro de que estas usando el driver correcto, la resolucion correcta y que tu monitor "es soportado" por ubuntu.
Posteame tu xorg.conf por favor y la salida del comando " cat /var/log/Xorg.0.log". Salu2!!

---

### Post by hictio on 2008-10-27
jajajavi, chequeaste estos logs?

> **hictio said:**
> Hace cuantos dias fue?
Podes chequear el log '/var/log/dpkg.log' y ve que mas se puede haber instalado, aparte de lo de Synaptics?
Ya chequeate el log de X Window ('/var/log/Xorg.0.log'), a ver si tiene algo que aportar?
Haceles un less en un Terminal, o abrilos con gedit.

Otro mas para revisar que se puede haber instalado que trajo problemas es '/var/log/aptitude'.

---

### Post by jajajavi on 2008-10-28
> **faktorqm said:**
> Se supone que mediante ese programa tenes que estar seguro de que estas usando el driver correcto, la resolucion correcta y que tu monitor "es soportado" por ubuntu.
Posteame tu xorg.conf por favor y la salida del comando " cat /var/log/Xorg.0.log". Salu2!!

Sí, el driver es el correcto, tuve aceleración 3d hasta hace poco. Acá pego el **xorg.conf**:

```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
        Option          "SHMConfig"             "true" # nuevo
#	Option		"HorizScrollDelta"	"0"
        Option          "LeftEdge"              "10" # modificado
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "370"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "1.10"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.08"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0

# extender monitor no funca
# 	Identifier	"Configured Video Device"
#     	Option		"FramebufferCompression" "off

EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

Y esto me dió **cat /var/log/Xorg.0.log**:

```
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 70 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 71 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) I810(0): Failsafe Monitor: Using hsync range of 31.50-50.00 kHz
(II) I810(0): Failsafe Monitor: Using vrefresh range of 56.00-65.00 Hz
(II) I810(0): Not using mode "1280x720@60" (no mode of this name)
(II) I810(0): Not using mode "1280x768@60" (no mode of this name)
(II) I810(0): Not using mode "800x600@60" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(**) I810(0): Virtual size is 1280x800 (pitch 2048)
(**) I810(0): *Built-in mode "1280x800@60"
(**) I810(0): *Built-in mode "800x600@56"
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "640x480"
(**) I810(0): Display dimensions: (290, 180) mm
(**) I810(0): DPI set to (112, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x90400000 - 0x9043ffff (0x40000) MS[B]
	[1] 0	0	0x80000000 - 0x8fffffff (0x10000000) MS[B]
	[2] 0	0	0x90380000 - 0x903fffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[8] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[9] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[10] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[11] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[12] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[13] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[14] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[15] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[16] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[17] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 0	0	0x000020e0 - 0x000020e7 (0x8) IS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[25] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[26] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[27] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[28] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[29] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[30] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[31] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[37] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[38] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[39] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[40] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16064 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 12288 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xdfff000 (0x3710b000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xdffb000 (0x371ac000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xdffa000 (0x3710e000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xdfea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) I810(0): [drm] Using the DRM lock SAREA also for drawables.
(II) I810(0): [drm] framebuffer handle = 0x80020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): Allocated 32 kB for the logical context at 0xdfe2000.
(II) I810(0): Allocated 6400 kB for the back buffer at 0xd000000.
(II) I810(0): Allocated 6400 kB for the depth buffer at 0xc800000.
(II) I810(0): Allocated 40192 kB for textures at 0xc20000
(II) I810(0): 0x821e9d0: Memory at offset 0x00020000, size 12288 kBytes
(II) I810(0): 0x821f878: Memory at offset 0x0dfff000, size 4 kBytes
(II) I810(0): 0x821f9c8: Memory at offset 0x0dffb000, size 16 kBytes
(II) I810(0): 0x821f8a4: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x821ea10: Memory at offset 0x0dfea000, size 64 kBytes
(II) I810(0): 0x821fae8: Memory at offset 0x0dffa000, size 4 kBytes
(II) I810(0): 0x821eba8: Memory at offset 0x0dfe2000, size 32 kBytes
(II) I810(0): 0x821ebc8: Memory at offset 0x0d000000, size 6400 kBytes
(II) I810(0): 0x821ebe8: Memory at offset 0x0c800000, size 6400 kBytes
(II) I810(0): 0x821ec08: Memory at offset 0x00c20000, size 40192 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0x90380000
(II) I810(0): [drm] ring buffer = 0x80000000
(II) I810(0): [drm] init sarea width,height = 1280 x 800 (pitch 2048)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0x20004000
(II) I810(0): [drm] Back Buffer = 0x8d000000
(II) I810(0): [drm] Depth Buffer = 0x8c800000
(II) I810(0): [drm] textures = 0x80c20000
(II) I810(0): [drm] Initialized kernel agp heap manager, 41156608
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0x80000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x00fbf000 (pgoffset 4031)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0dfff000 (pgoffset 57343)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0dffb000 (pgoffset 57339)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0dfea000 (pgoffset 57322)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0dffa000 (pgoffset 57338)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0dfe2000 (pgoffset 57314)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0d000000 (pgoffset 53248)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0c800000 (pgoffset 51200)
(WW) I810(0): PGTBL_ER is 0x00000102
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 61 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 912 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(II) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): [DRI] installation complete
(II) I810(0): [drm] dma control initialized, using IRQ 17
(II) I810(0): direct rendering: Enabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "10"
(**) Option "RightEdge" "1200"
(**) Option "TopEdge" "10"
(**) Option "BottomEdge" "370"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "50"
(**) Option "FingerLow" "10"
(**) Option "FingerHigh" "20"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "MaxDoubleTapTime" "180"
(**) Option "VertEdgeScroll" "0"
(**) Option "HorizEdgeScroll" "0"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "LockedDrags" "off"
(**) Option "RTCornerButton" "0"
(**) Option "RBCornerButton" "0"
(**) Option "LTCornerButton" "0"
(**) Option "LBCornerButton" "0"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(**) Option "SingleTapTimeout" "100"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

```

Siguiendo las recomendaciones de hictio, en **/var/log/aptitude** encontré una referencia al cambio que produjo el problema:

```
mar, oct 14 2008 16:26:03 -0300

[ACTUALIZA] xserver-xorg-input-synaptics 0.14.7~git20070706-1ubuntu4 -> 0.14.7~git20070706-mactel1

```

En los otros logs no encontré nada sobre 'xserver-xorg-input-synaptics', de todos modos los pongo como adjuntos por si alguien los quiere revisar. Y muchas gracias a todos por la ayuda.

---

### Post by faktorqm on 2008-10-29
Fijate de dejarlo asi el archivo. Cambié algunas cosas aunque sea para probar. Tiene (mejor dicho, tenia) muchos errores sintacticos. 

```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
        Option          "SHMConfig"             "true" # nuevo
#	Option		"HorizScrollDelta"	"0"
        Option          "LeftEdge"              "10" # modificado
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "370"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "1.10"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.08"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection

Section "Device"
	Identifier	"Device0"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
EndSection
# extender monitor no funca
# 	Identifier	"Configured Video Device"
#     	Option		"FramebufferCompression" "off

#EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

#Section "device"   
#	Identifier	"device1"
#	Boardname	"vesa"
#	Busid		"PCI:0:2:0"
#	Driver		"i810"
#	Screen	1
#EndSection

#Section "screen" #   
#	Identifier	"screen1"
#	Device		"device1"
#	Defaultdepth	24
#	Monitor		"monitor1"
#	SubSection "Display"
#		Depth	24
#		Modes		"640x480@60"
#	EndSubSection
#EndSection

#Section "monitor"  
#	Identifier	"monitor1"
#	Vendorname	"Plug 'n' Play"
#	Modelname	"Plug 'n' Play"
#  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -#hsync
#	Gamma	1.0
#EndSection

Section "ServerFlags"
EndSection

```

Cómo extender el escritorio: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/26807](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/26807)

Quizá debas leer esto tambien: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Salu2!!!

---

### Post by jajajavi on 2008-10-31
Hola de nuevo! Probé los cambios en el xorg.conf y al reiniciar X el problema de "redibujado lento" desaparece aunque pierdo la configuración del touchpad (es lo de menos) y no puedo activar los efectos de escritorio.

direct rendering: No

Sigo sin aceleración gráfica pero puedo hacer scroll fluidamente.

Usé el tutorial community/MacBook para la instalación y siempre lo consulto, aunque no siempre lo entiendo.

Gracias por la ayuda!

---

### Post by faktorqm on 2008-10-31
Proba en la primera seccion de comentar GLCore, por que yo me acabo de dar cuenta que no lo tengo, capaz te esta molestando eso.
Si sigue, podrias probar de hacer 

```
sudo apt-get install xserver-xorg-video-i810 xserver-xorg-video-intel
```

y si ya tenes todo instalado y andando, tambien podes probar de hacer:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_anda_maso
```

```
sudo dpkg-reconfigure xserver-xorg-video-i810
```

```
sudo dpkg-reconfigure xserver-xorg
```

Éste último te genera un xorg.conf nuevo. cuando terminas apretas ctrl + alt + backspace (borrar) y reinicias el servidor X.
Cualquier cosa que no te ande postea el xorg "sin tocar" éste que te genera. Salu2!

---

### Post by jajajavi on 2008-11-01
Comenté la linea de GLCore y siguió haciendo lo mismo, xserver-xorg-video-i810 y xserver-xorg-video-intel están en su versión más reciente. 

> **faktorqm said:**
> Cualquier cosa que no te ande postea el xorg "sin tocar" éste que te genera.

Con esta configuración andan los efectos de escritorio pero el scroll, desplazamiento de ventanas y la transparentación siguen tartamudeando. Nuevamente muchas gracias por la ayuda!

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Ahí va el xorg sin tocar:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by faktorqm on 2008-11-03
Hola, disculpa la tardanza, pero me fui el finde afuera.

Ahora si, con el xorg.conf "limpio" ejecuta "sudo displayconfig-gtk" y ahi elegi el monitor y el driver de la placa de la video. Si sigue sin andar chiflá, pero lo vamos a solucionar quedate tranca.

Si sigue sin andar, para probar lo que te dice ahi hace:

```
export LIBGL_DEBUG=verbose
```

y despues ejecuta el comando. Salu2!

---

### Post by jajajavi on 2008-11-04
> **faktorqm said:**
> Hola, disculpa la tardanza, pero me fui el finde afuera.

Ahora si, con el xorg.conf "limpio" ejecuta "sudo displayconfig-gtk" y ahi elegi el monitor y el driver de la placa de la video. Si sigue sin andar chiflá, pero lo vamos a solucionar quedate tranca.

Todo bien, esto lo vemos nos pinta y hay tiempo. El displayconfig me reconoce 3 pantallas, como preterminada autodetecta un *Plug 'n play* genérico 1280x800 en 60Hz. En tarjeta gráfica pongo *i810 - Intel* arriba y *vesa generic* abajo (probé poniendo "intel" en ambos campos al reiniciar x pero saltaba un cartel de "Ubuntu se está ejecutando en baja resolución"). Direct rendering sigue dando No, los efectos de escritorio no se pueden activar pero mover ventanas, hacer scroll, o sea el "redibujado" anda perfecto. El  [FONT="Comic Sans MS"]export LIBGL_DEBUG=verbose[/FONT] no devuelve ningún mensaje. 

El xorg.conf actual quedó modificado en la parte de video, el resto es como el que está posteado antes:

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"vesa"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

Nuevamente gracias por la onda, seguimos probando.

---

### Post by faktorqm on 2008-11-04
La verdad ni idea, la opcion del export es que tenes que hacer, export blbla y abajo glxinfo de vuelta. Posteame de vuelta el xorg.log a ver si cambio en algo que me de una pista. Salu2!

---

### Post by jajajavi on 2008-11-04
[B]Xorg.0.log
[/B]

```

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux tosh 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  5 01:38:48 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 8086,7270 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 8086,7270 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 8086,7270 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:07:0: chip 8086,27a3 card 0000,0000 rev 03 class 11,01,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,27d8 card 8384,7680 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 8086,7270 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 8086,7270 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 8086,7270 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 8086,7270 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c4 card 8086,7270 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 8086,7270 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 11ab,4362 card 11ab,5321 rev 22 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 168c,0024 card 0000,0000 rev 01 class 02,80,00 hdr 00
(II) PCI: 03:03:0: chip 11c1,5811 card 11c1,5811 rev 61 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x90500000 - 0x905fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x90100000 - 0x901fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0x900fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x90380000/19, 0x80000000/28, 0x90400000/18, I/O @ 0x20e0/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x90300000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[2] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[3] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[4] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[5] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[6] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[7] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[8] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[9] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[13] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[14] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[15] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[16] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[17] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[18] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[24] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[25] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[26] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[27] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[2] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[3] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[4] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[5] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[6] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[7] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[8] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[9] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[13] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[14] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[15] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[16] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[17] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[18] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[24] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[25] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[26] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[27] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[12] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[19] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[20] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[21] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[22] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[23] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[24] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[30] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[31] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[32] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[33] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[12] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[19] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[20] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[21] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[22] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[23] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[24] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[30] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[31] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[32] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[33] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[12] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[22] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[23] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[24] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[25] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[26] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[27] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[33] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[34] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[35] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[36] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16064 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: APP  Model: 9c5f  Serial#: 0
(II) VESA(0): Year: 2006  Week: 8
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 29  vert.: 18
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.590 redY: 0.346   greenX: 0.327 greenY: 0.546
(II) VESA(0): blueX: 0.160 blueY: 0.147   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 71.0 MHz   Image Size:  286 x 179 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) VESA(0):  LP133WX1-TLA1
(II) VESA(0):  Color LCD
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0006105f9c00000000
(II) VESA(0): 	08100103801d12780a2f309758538b29
(II) VESA(0): 	25505400000001010101010101010101
(II) VESA(0): 	010101010101bc1b00a0502017303020
(II) VESA(0): 	36001eb3100000180000000100061020
(II) VESA(0): 	00000000000000000a20000000fe004c
(II) VESA(0): 	503133335758312d544c4131000000fe
(II) VESA(0): 	00436f6c6f72204c43440a20202000c2
(II) VESA(0): EDID vendor "APP", prod id 40031
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 161 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 162 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 169 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 170 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 14d (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 15c (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 13a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 49
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 49
	LinNumberOfImagePages: 49
	LinRedMaskSize: 0

	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 26
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x80000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 26
	LinNumberOfImagePages: 26
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 251 64KB banks (16064kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-59.91 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(--) VESA(0): Virtual size is 1280x800 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x800"
(**) VESA(0): Display dimensions: (290, 180) mm
(**) VESA(0): DPI set to (112, 112)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x800" (14d)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[12] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[22] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[23] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[24] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[25] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[26] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[27] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[33] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[34] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[35] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[36] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16064 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0x80000000, size: 0xfb0000
(II) VESA(0): Splitting WC range: base: 0x80800000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0x80c00000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0x80e00000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0x80f00000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0x80f80000, size: 0x30000
(==) VESA(0): Write-combining range (0x80fa0000,0x10000)
(==) VESA(0): Write-combining range (0x80f80000,0x30000)
(==) VESA(0): Write-combining range (0x80f00000,0xb0000)
(==) VESA(0): Write-combining range (0x80e00000,0x1b0000)
(WW) VESA(0): Failed to set up write-combining range (0x80c00000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0x80800000,0x7b0000)
(WW) VESA(0): Failed to set up write-combining range (0x80000000,0xfb0000)
(II) VESA(0): virtual address = 0xb69bb000,
	physical address = 0x80000000, size = 16449536
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "macintosh"
(**) Generic Keyboard: XkbModel: "macintosh"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
SetClientVersion: 0 9
```

---

### Post by faktorqm on 2008-11-05
Che sos de capital? mas facil que me la lleves al festival de cultura libre en la tribu... por que estoy buscando y no encuentro nada... y ya estoy perdiendo mucho tiempo :( Salu2!

---

### Post by jajajavi on 2008-11-05
> **faktorqm said:**
> Che sos de capital? mas facil que me la lleves al festival de cultura libre en la tribu... por que estoy buscando y no encuentro nada... y ya estoy perdiendo mucho tiempo :( Salu2!

No, de Rosario, aunque me gustaría ir a lo de la tribu, en fin, voy a seguir experimentando. Muchas gracias por la mano. Saludos!

**novedades:**
Probé actualizando a 8.10 y me parece que me la mandé. No arranca X, inicia en tty1, probé restaurando el xorg desde backups pero no pasa naranja.

---

### Post by faktorqm on 2008-11-05
uhhhh bueno, ahora si tenes que arrancar con el driver vesa si o si aunque sea para ver 800x600... eso lo haces con "sudo nano /etc/X11/xorg.conf", una vez ahi, buscas la seccion driver, le pones vesa (como lo tenes vos ahora), salis y reinicias de vuelta, si podes entrar a la parte grafica, apreta alt + f2 y escribis "sudo displayconfig-gtk" y configuras, a ver que hace. Si sigue sin hacer nada, al menos ponele una resolucion copada y fijate si estan los paquetes que te dije antes. Si estan bueno, sera cuestion de encontrarle la vuelta. En el bios no aparece ninguna opcion "rara" con respecto al video? Nunca tuve una mac... no se si tienen bios en realidad... 

y para venirte un dia estaria bueno que sea el domingo, asi no te clavas una noche aca... va hace como quieras! Salu2!

---

### Post by jajajavi on 2008-11-06
Hice lo que supongo es una reconfiguración del xorg.conf
```
sudo dpkg-reconfigure xserver-xorg
```
y **arrancó Ubuntu 8.10 con aceleración gráfica!!**, aunque sin wifi, supongo que tendré que reinstalar los drivers de la placa con ndiswrapper (además de las configuraciones del touchpad que cayeron en la volteada cuando modifiqué el xorg).

---

### Post by faktorqm on 2008-11-06
BIEN AHI!!!!!!!! abro otro thread por la placa wifi. solo hay con ndiswrapper? quiza ya haya un driver mejor. Salu2!

---

### Post by jajajavi on 2008-11-06
**Falsa alarma:** reinicio y tengo wifi.
Lo que me sorprende es lo corto que quedó el xorg.conf actual, sólo están las secciones "Device", "Monitor" y "Screen". Intenté agregarle "Input Device" de un xorg.conf anterior en la que estaba configurado el touchpad para usar hacer scroll con dos dedos pero no va. Ahora que veo en la PC el xorg también quedó escueto, parece que es algo nuevo de Ubuntu 8.10. Leyendo la [documentación oficial]("https://help.ubuntu.com/community/MacBook#touchpadtweaks") para macbook veo que hay que crear un archivo para que funque:

you will need to create a new HAL .fdi file (in /etc/hal/fdi/policy/) 

Bueno, esto va mejorando. Gracias a todos los que ayudaron!!

---

### Post by Hei Ku on 2008-11-06
Lo del xorg.conf es porque las nuevas versiones de xorg detectan mas cosas automaticamente. Ya no es necesario especificar tantas cosas a mano.

---

