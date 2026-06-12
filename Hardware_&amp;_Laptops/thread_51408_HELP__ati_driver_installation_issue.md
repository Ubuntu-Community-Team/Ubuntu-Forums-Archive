---
title: "HELP:  ati driver installation issue"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by martz on 2005-07-23
greetings,

i've read 4 tutorials and none of them seem to address my problem (i think).  i download the ati drivers, and run the installer, looks like everything is going well and...

"There were errors during installation.  Details can be found:"  and the details are:

```
(Message) Kernel Module : Trying to install a precompiled kernel module.
(Message) Kernel Module : Precompiled kernel module version mismatched.
(Error) Kernel Module:  No Kernel module build environment - please consult readme
```

What do i do to fix this?  I've got an ati 9800 256 mb card, with an amd processor.  I'm very new to linux but am good with computers in general (quick learner).  I use unix at work and program in PV-Wave.  Earlier i tried using the fglrxconfig but it didn't work.  The linux kernel headers are installed.

I'm screwing with this so that I can get dual monitors up and running.  thanks for your help

---

### Post by PeP on 2005-07-23
[QUOTE=martz]greetings,
 i download the ati drivers, and run the installer[/QUOTE]

I switched from debian because I did not want to do this anymore

you should use the ati drivers provided in the linux-restricted-modules package:

1.make sure you have restricted sources in /etc/apt/sources.list

2. what kernel do you have
%uname -a


3. search for the linux restricted modules and verify that one match  your kernel version
%sudo apt-cache search linux-restricted-modules

4. if not get a kernel with compiled restricted modules just change !
%sudo apt-get install linux-image-2.6.10-5-686
(replace 686 with yor architecture in case you have an older pc)

5. get the corresponding restricted-modules
%sudo apt-get install linux-restricted-modules-2.6.10-5-686

6. you can alos get the control panel (useful to config your dual screen)
%sudo apt-get install  fglrx-control

7. check your /etc/X11/xorg.conf or /etc/X11/XF86config-4
look for MonitorLayout an set it to AUTO,AUTO :
    Option "MonitorLayout"              "AUTO, AUTO"

this enables dual display.

do not forget to reboot if you changed the kernel.


---------------------------------------------------------------------------------------
here is the ATi part of mine# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000100"
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified"
    Option "VRefresh2"                  "unspecified"
    Option "ScreenOverlap"              "0"
# === TV-out Management ===
    Option "NoTV"                       "no"
    Option "TVStandard"                 "NTSC-M"
    Option "TVHSizeAdj"                 "0"
    Option "TVVSizeAdj"                 "0"
    Option "TVHPosAdj"                  "0"
    Option "TVVPosAdj"                  "0"
    Option "TVHStartAdj"                "0"
    Option "TVColorAdj"                 "0"
    Option "GammaCorrectionI"           "0x05d15c57"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "on"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e54
    Screen 0
EndSection

---

### Post by martz on 2005-07-23
```
martz@ubuntu:~$ uname -a
Linux ubuntu 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

martz@ubuntu:~$ sudo apt-cache search linux-restricted-modules
linux-restricted-modules-386 - Restricted Linux modules on 386.
linux-restricted-modules-2.6.10-5-386 - Non-free Linux 2.6.10 modules on 386
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.10-5-686 - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.10-5-686-smp - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules-2.6.10-5-k7 - Non-free Linux 2.6.10 modules on AMD K7
linux-restricted-modules-2.6.10-5-k7-smp - Non-free Linux 2.6.10 modules on AMD K7 SMP
linux-restricted-modules-686 - Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules-686-smp - Restricted Linux modules on PPro/Celeron/PII/PIII/PIV SMP.
linux-restricted-modules-k7 - Restricted Linux modules on AMD K7.
linux-restricted-modules-k7-smp - Restricted Linux modules on AMD K7 SMP.
nvidia-kernel-source - NVIDIA binary kernel module source

```

no idea what most of that means... from "2.6.10-5-386" i would assume that's the kernel, but my computer is not old... and it also goes on to say "i686"  then it looks like i ahve both 686 and 386 restricted-modules going on...

and i had already gotten the fglrx-control but don't know how to run it (like i said, new to linux)

any thoughts?

---

### Post by PeP on 2005-07-24
[QUOTE=martz]```
martz@ubuntu:~$ uname -a
Linux ubuntu 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

martz@ubuntu:~$ sudo apt-cache search linux-restricted-modules
linux-restricted-modules-386 - Restricted Linux modules on 386.
linux-restricted-modules-2.6.10-5-386 - Non-free Linux 2.6.10 modules on 386
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.10-5-686 - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.10-5-686-smp - Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules-2.6.10-5-k7 - Non-free Linux 2.6.10 modules on AMD K7
linux-restricted-modules-2.6.10-5-k7-smp - Non-free Linux 2.6.10 modules on AMD K7 SMP
linux-restricted-modules-686 - Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules-686-smp - Restricted Linux modules on PPro/Celeron/PII/PIII/PIV SMP.
linux-restricted-modules-k7 - Restricted Linux modules on AMD K7.
linux-restricted-modules-k7-smp - Restricted Linux modules on AMD K7 SMP.
nvidia-kernel-source - NVIDIA binary kernel module source

```

no idea what most of that means... from "2.6.10-5-386" i would assume that's the kernel, but my computer is not old... and it also goes on to say "i686"  then it looks like i ahve both 686 and 386 restricted-modules going on...

and i had already gotten the fglrx-control but don't know how to run it (like i said, new to linux)

any thoughts?[/QUOTE]
 apt-cache search shows you available packages,
just download linux-restricted-modules-2.6.10-5-386 these will work with your kernel.

---

### Post by martz on 2005-07-24
[QUOTE=PeP]apt-cache search shows you available packages,
just download linux-restricted-modules-2.6.10-5-386 these will work with your kernel.[/QUOTE]

i already have those installed... and ati still gives me the same error

---

### Post by PeP on 2005-07-24
[QUOTE=martz]i already have those installed... and ati still gives me the same error[/QUOTE]
if you have those installed you don need to get it twice : you don't need the driver ou get from ati you already have it!

> and i had already gotten the fglrx-control but don't know how to run it (like i said, new to linux)

type 
fireglcontrol
in a terminal

can you give the result of  glxinfo

---

### Post by martz on 2005-07-24
ok, i've gotten a lot farther than i was before.

i've been using the: "HOW TO: ATI Drivers v0.2 (Revised)" thread and now instead of showing fglrxinfo stuff as mesa... it shows my correct ati card info

when i goto the applications menu there is ATI control, once i go in there i can (supposedly) setup my dual monitors... but when I make change the settings and then ctrl-alt-backspace it's still the same

to get mesa to stop showing up i had to stop X, and reinstall the restricted modules and fglrx and that's when the ati showed up.

when i type fireglcontrol, it's not there, though i know i have the control installed

i will post glxinfo in a sec (i'm on two comps)

---

### Post by martz on 2005-07-24
```
root@ubuntu:~ # glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ATI_draw_buffers,
    GL_ATI_element_array, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_texgen_reflection,
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_EXT_vertex_shader,
    GL_HP_occlusion_test, GL_NV_texgen_reflection, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_SGI_color_matrix, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_lod,
    GL_SGIS_generate_mipmap, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```

---

### Post by PeP on 2005-07-24
[QUOTE=martz][code]
direct rendering: Yes
...
client glx vendor string: ATI[/QUOTE]
ati drivers are installed and working

try 
/usr/X11R6/bin/fireglcontrol or /usr/bin/X11/fireglcontrol

as normal user  with wich you logged in X, not as root

---

### Post by martz on 2005-07-24
neither of those worked

so i reinstalled the control using synaptic and then tried fireglcontrol

it worked, and it brings up the same gui that the applications menu' ATI Control does

now the problem is it still won't accept any changes that i make to the dual screen options.  I have two lcds that are connected to the same card (one to DVI, one to analog)

here is my xorg.conf file... maybe it's something in there:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load    "GLcore"
	Load	"glx"
	Load	"dri"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"

# You don't actually need this next BusID bit - unless maybe you have dual monitors?
# I've removed it from mine (single monitor only) and all is well.
# I think it's a leftover from fxglrconfig - doh!
	BusID		"PCI:1:0:0" 
                           
EndSection

Section "Monitor"
	Identifier	"R710E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"R710E"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by PeP on 2005-07-24
[QUOTE=martz]
```

Section "Device"
 Identifier "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
 Driver  "fglrx"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
   Option   "VideoOverlay"   "on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
   Option   "OpenGLOverlay"  "off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
   Option   "UseInternalAGPGART"  "no"

# You don't actually need this next BusID bit - unless maybe you have dual monitors?
# I've removed it from mine (single monitor only) and all is well.
# I think it's a leftover from fxglrconfig - doh!
 BusID  "PCI:1:0:0" 
                           
EndSection

```[/QUOTE]
again, try adding this in the section above:
 Option "MonitorLayout" "AUTO, AUTO"

---

### Post by martz on 2005-07-24
didn't work

do you go on irc at all?

---

### Post by martz on 2005-07-24
EUREKA!!!!

ok, here's what i did

in the xorg.conf file, under device:
```
 Option "DesktopSetup" "0x00000201"
Option "MonitorLayout" "AUTO, AUTO"
```
the 201 part sets it up so that the primary monitor (the one connected to dvi) is on the right (that's how i have mine set up... if you want it so it's on the left you set it as 200

thanks alot for all of your help

---

### Post by PeP on 2005-07-25
[QUOTE=martz]didn't work

do you go on irc at all?[/QUOTE]
nope :-)

> 
thanks alot for all of your help 
you're welcome

---

