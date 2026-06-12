---
title: "Compiz problem with ATI"
date: 2008-07-30
forum: General Help
---

### Post by RellikZephyr on 2008-07-30
Hi

i am new (very new) to linux and am having the common compiz problem

i have tried everything and nothing has worked

the output from compiz --replace is...

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:9400 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (2048: Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

incase it helps video card = ati 2900XT 512MB

output from compiz check is all OK
have tried ati binary X.org drivers, when visual effects activated screen turns all white
have tried restricted drivers from install, when restart get black screen and system hang
have done fresh install of compiz
have updated
have tried installing xgl

really dont know what else to try

thanks in advance for help

RellikZephyr

---

### Post by gvartser on 2008-07-30
Check out:
[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

/g

---

### Post by RellikZephyr on 2008-07-30
thanks for reply

but...  i cant enable desktop effects  so that liitle guide doesnt work for me because it goes off the assumption i can

RellikZephyr

---

### Post by anewguy on 2008-07-30
I don't know if it would help your problem or not, but have you installed the following:

xserver-xorg-video-ati


I have an ATI 9250 card and the driver was loaded automatically when I installed Hardy, so I checked the xserver and glx stuff and nothing seemed vendor-specific for what I have installed for glx, just things like the glx core, but I do know that my xorg.conf file says "ati" for the driver so it's using the above file.

---

### Post by RellikZephyr on 2008-07-30
tried it just then

script output says its already the newest version

so i guess its already installed

and still visual effects wont enable

RellikZephyr

---

### Post by gvartser on 2008-07-30
Maby the problem is that your card is blacklisted:

How to find out:
-> [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

If its blacklisted, here is what you can do.

**1) Make a backup of the original compiz script file:**
   ```
$ sudo cp /usr/bin/compiz /usr/bin/compiz_backup
```

**2) Edit the compiz script file: **
   ```
$ sudo vi /usr/bin/compiz
```
   _Search for the lines and comment out the "ati" part._

   [COLOR="Blue"]# blacklist based on the pci ids
   # See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
   T=" 1002:5954 1002:5854 1002:5955" # ati rs480
   T="$T 1002:4153" # ATI Rv350
   T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965
   T="$T 8086:2972" # i965 (x3000)
   T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
   BLACKLIST_PCIIDS="$T"
   unset T[/COLOR]

_Example:_

[COLOR="Blue"]# blacklist based on the pci ids
   # See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
   [COLOR="Red"]#T=" 1002:5954 1002:5854 1002:5955" # ati rs480
   #T="$T 1002:4153" # ATI Rv350[/COLOR]
   T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965
   T="$T 8086:2972" # i965 (x3000)
   [COLOR="Red"]#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700[/COLOR]
   BLACKLIST_PCIIDS="$T"
   unset T[/COLOR]

**3) Restart X:**
   -> CTRL + ALT + BCKSPC

**4) Enable Compiz effects:**
   You should be able to enable Compiz Fusion now by going to &#8220;System -> Preferences -> Appearance&#8221; 
   and choosing something other than &#8220;None&#8221; on the &#8220;Visual Effects&#8221; tab.

Good luck,
/g

---

### Post by overdrank on 2008-07-30
Moved :)

---

### Post by anewguy on 2008-07-30
Since we didn't have you do it before, could you copy and paste the output of the following back here please:

glxinfo <enter>


Also, be sure you have the compizconfig-settings-manager package installed and can access it via System/Preferences/Advanced Desktop Effects Settings.


:)

---

### Post by RellikZephyr on 2008-07-31
gvartser:  how do i "comment out"??   if it is just the # denotation  then they are already done

i didnt add #'s they were already there, i have tried the SKIP_CHECKS=yes thing could that have done it??

here is section  (copy and paste straight out of script)
```

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
BLACKLIST_PCIIDS="$T"
unset T


anewguy:

here is output

choppa@choppa-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
choppa@choppa-desktop:~$ 
```

and yes  i already have compiz manager package installed

sorry for long post... how do i put output code into its own little window in post??

Thanks

---

### Post by overdrank on 2008-07-31
> **RellikZephyr said:**
> gvartser:  how do i "comment out"??   if it is just the # denotation  then they are already done

i didnt add #'s they were already there, i have tried the SKIP_CHECKS=yes thing could that have done it??

here is section  (copy and paste straight out of script)
```

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
BLACKLIST_PCIIDS="$T"
unset T


anewguy:

here is output

choppa@choppa-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
choppa@choppa-desktop:~$ 
```

and yes  i already have compiz manager package installed

sorry for long post... how do i put output code into its own little window in post??

Thanks

Hi and the code tags are # and you can insert the text between the code tags. I will edit for you this time, :)

---

### Post by RellikZephyr on 2008-07-31
so  i just type a 

#

then enter the code

#


hmm  just testing if it works   

if it doesnt  tell me what im doin wrong please

EDIT:  nope  didnt work  how i use tags??


RellikZephyr

---

### Post by overdrank on 2008-07-31
> **RellikZephyr said:**
> so  i just type a 

#

then enter the code

#


hmm  just testing if it works   

if it doesnt  tell me what im doin wrong please

EDIT:  nope  didnt work  how i use tags??


RellikZephyr

On the reply message box in the top right corner you will see #. If you will click on it will insert the ```
 
``` these are the tags that you use. Insert you text in between. The only difference is code will be in capital letters CODE. But if I did you would not see. :)
Edit added screen shot.

---

### Post by PmDematagoda on 2008-07-31
You don't seem to be having direct rendering available, this may be because:-
1) Your VGA card is too old to support it.
2) The current driver doesn't support DRI or 3D acceleration.

Did you try installing the fglrx driver through Hardware Drivers in System>Administration>Hardware Drivers and seeing if that allows you to use compiz-fusion?

---

### Post by RellikZephyr on 2008-07-31
overdrank:  ahh  i see  didnt even consider looking at the buttons, thought it was a type tag

got it now   thanks

PmDematagoda:

ok  1:  no my video card isnt too old   its a 2900XT

and 2:  when i install the restricted drivers and do the required restart,  once i get to where the login screen should be, all i get is a black screen and system hang

and if i do that, do you know how i can recover so ubuntu will boot normally again??

RellikZephyr

---

### Post by PmDematagoda on 2008-07-31
> **RellikZephyr said:**
> overdrank:  ahh  i see  didnt even consider looking at the buttons, thought it was a type tag

got it now   thanks

PmDematagoda:

ok  1:  no my video card isnt too old   its a 2900XT

and 2:  when i install the restricted drivers and do the required restart,  once i get to where the login screen should be, all i get is a black screen and system hang

and if i do that, do you know how i can recover so ubuntu will boot normally again??

RellikZephyr

Enable the driver again, and this time when you get the black screen, press Ctrl+Alt+F1 to switch to a virtual terminal, login and then execute:-
```
cat /var/log/Xorg.0.log > ~/xorg.log
```
then reboot the system with:-
```
reboot
```
and the boot Ubuntu in Recovery Mode, once there select xfix and after that is finished, try and see if you can reach the desktop now, if you can, post the outputs of:-
```
cat ~/xorg.log
```
and
```
cat /etc/X11/xorg.conf
```

---

### Post by RellikZephyr on 2008-07-31
ok  before  i do that   how do i boot in recovery mode??

RellikZephyr

---

### Post by PmDematagoda on 2008-07-31
> **RellikZephyr said:**
> ok  before  i do that   how do i boot in recovery mode??

RellikZephyr

You will probably get a part with "Press Esc to enter boot(or GRUB) menu", press Esc there and then you will be presented with a menu from which you can start Ubuntu in recovery mode.

---

### Post by RellikZephyr on 2008-07-31
ok

got black screen, but system hang was complete,  meaning got no keyboard so i couldnt  Ctrl+Alt+F1 and execute   cat /var/log/Xorg...etc

so no xorg.log to post output (No such file or directory)

output for cat /etc/Xll/xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
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
EndSection

```

EDIT:  if i try to enable desktop effects now, screen goes all white

RelliKZephyr

---

### Post by PmDematagoda on 2008-07-31
Then try installing the radeonhd driver with:-
```
sudo apt-get install xserver-xorg-video-radeonhd
```
after that is installed post the output of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by RellikZephyr on 2008-07-31
ok  radeonhd drivers installed

output is

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
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
EndSection


```

trying to enable visual effects incurs same white screen

RellikZephyr

---

### Post by RellikZephyr on 2008-08-01
bump

please help  im out of ideas

RellikZephyr

---

### Post by PmDematagoda on 2008-08-01
Can you post the output of:-
```
glxinfo | grep direct
```

---

### Post by RellikZephyr on 2008-08-01
output is

```


direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


```

RellikZephyr

---

### Post by antonr on 2008-08-04
Maybe check out this link for some config ideas.

[http://wiki.x.org/wiki/radeonhd#head-af81f9fb39542285c5a7c330c13b8ffe97c71e51](http://wiki.x.org/wiki/radeonhd#head-af81f9fb39542285c5a7c330c13b8ffe97c71e51)

The open source 'xf86-video-radeonhd' (driver "radeonhd") is being
actively developed right at the moment.
I'm currently trying to compile from source, to install on Feisty.
(but I got some errors involving uint8_t and uint32_t at the moment..).

Some maybe useful links:

[http://dri.freedesktop.org/wiki/ATIRadeon#head-6cd1522552beb3e7ad5489538ba676bbce863c87](http://dri.freedesktop.org/wiki/ATIRadeon#head-6cd1522552beb3e7ad5489538ba676bbce863c87)

[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-radeonhd;a=summary](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-radeonhd;a=summary)

The command ddcprobe, can probably display the chipset used by your card.

sudo apt-get install xresprobe
sudo ddcprobe

---

### Post by colobix on 2008-08-04
Hi. I too have the same problem with blacklisted ATI card. 
I am new so I do not understand all that code thing. How do I turn off that blacklist thing so I can activate the desktop effects?

Please help,

---

### Post by tosoth on 2008-08-04
> **RellikZephyr said:**
> output is

```


direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


```

RellikZephyr

Hello.
I don't think you will get desktop effects to work with **radeonhd** driver, because (if I remember corectly) it doesn't support 3D acceleration yet.
You have to do it with **fglrx** driver. The black screen you get after installing this driver can be cured by setting larger **AGP aperture size** in BIOS. I had to set it to 512MB.

---

### Post by RellikZephyr on 2008-08-05
> **tosoth said:**
> Hello.
I don't think you will get desktop effects to work with **radeonhd** driver, because (if I remember corectly) it doesn't support 3D acceleration yet.
You have to do it with **fglrx** driver. The black screen you get after installing this driver can be cured by setting larger **AGP aperture size** in BIOS. I had to set it to 512MB.

Hi

my graphics card is a PCI-E card  so will the AGP aperture have anything to do with it??  or am i looking for a PCI-E aperture??
cause they are 2 completely diffent architectures

RellikZephyr

---

### Post by tuxxy on 2008-08-05
I recommend upgrading to an nvidia card to solve all issues you have with ATI

---

### Post by RellikZephyr on 2008-08-05
> **tuxxy said:**
> I recommend upgrading to an nvidia card to solve all issues you have with ATI

lol  yeah maybe

tosoth:  i have looked through my BIOS (ASUS) and i cant see any setting for the AGP Aperture

im losing intrest in ubuntu quickly, having this much trouble to get what i think is a basic system function working

unless anyone has any other ideas  i might try again with intrepid when its released  or till there is better open source ATI support

i know compiz can work, i played with a live CD of Mandriva  and compiz worked out the box no gliches or hiccups

so anyone with any new ideas   please enlighten me

Thanks 

RellikZephyr

---

### Post by PmDematagoda on 2008-08-06
After installing the fglrx driver and you reach the black screen, press Ctrl+Alt+F1 and then execute:-
```
cat /var/log/Xorg.0.log > ~/Desktop/xorg.log
```
then reboot the PC, reconfigure X as you did before and then post the contents of the xorg.log file on the desktop.

---

### Post by RellikZephyr on 2008-08-07
> **PmDematagoda said:**
> After installing the fglrx driver and you reach the black screen, press Ctrl+Alt+F1 and then execute:-
```
cat /var/log/Xorg.0.log > ~/Desktop/xorg.log
```
then reboot the PC, reconfigure X as you did before and then post the contents of the xorg.log file on the desktop.

reinstalled fglrx when got to black screen computer was completely frozen  Crtl+Alt+F1 command did nothing

reset comp, screen came up saying couldnt boot problem with video then gave me a terminal  typed said code  gave me a no dir or file exists

did reboot via sudo reboot,  went into grub menu and ran recovery mode,   said it failed some fsck ??? check  duplitcate sector or something

wont go into basic gui with xfix command until i type sudo reboot, then when it displays menu (with xfix)  cant use menu  just types over menu the terminal code

so now i cant boot ubuntu

ummm....????

RellikZephyr

---

### Post by PmDematagoda on 2008-08-07
Can you atleast reach a terminal through Recovery Mode? If so, run:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then see if the X-Server starts up properly.

---

### Post by RellikZephyr on 2008-08-07
ok  can get terminal in recovery but...

ran said script, got...

```

command 'sudo' is available in usr/bin
command could not be located because usr/bin is not in the PATH environment variable

```

so i change dir to usr/bin, retyped script ...   to no avail

so i went back to root and ran script without sudo cause im in root

same thing only replace 'sudo' with 'dpkg-regonfigure'

so xserver still no good

RellikZephyr

---

