---
title: "Slower than WindowXP"
date: 2008-09-04
forum: General Help
---

### Post by laptoppana on 2008-09-04
Hi all,

I running FireFox both XP and Ubuntu Hardy, and I found that the speed of FireFox on Xp is faster and the browser roll smoother. How can I speed up FireFox on Ubuntu? Thanks

---

### Post by lakersforce on 2008-09-04
Do you have direct rendering enabled?

Do this, and if the answer is no, that is your problem.
```

glxinfo | grep rendering
```

If your answer is no, do a

```
glxinfo

```
and post the output here.

---

### Post by prshah on 2008-09-04
> **laptoppana said:**
> 
I running FireFox both XP and Ubuntu Hardy, and I found that the speed of FireFox on Xp is faster and the browser roll smoother. How can I speed up FireFox on Ubuntu? Thanks

If you find that browsing is slower in Ubuntu than in XP using any browser, maybe you need to do the MTU fix as in [this post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12").

Just a suggestion, you may not need this, so please read the post thoroughly (maybe even the entire thread) before you attempt this.

---

### Post by Martin_sensei on 2008-09-04
Could this be a graphics card issue?  Do you have the restricted drivers for you graphics card enabled?

I think this is available from the Administration menu under Hardware, or Restricted Hardware.

---

### Post by Sycron on 2008-09-04
It's from System-->Administration-->Hardware Drives.

---

### Post by laptoppana on 2008-09-04
> **lakersforce said:**
> Do you have direct rendering enabled?

Do this, and if the answer is no, that is your problem.
```

glxinfo | grep rendering
```

If your answer is no, do a

```
glxinfo

```
and post the output here.

The answer is NO, and here is the output of glinfo. Please give me a hint, thanks for your time!

name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by laptoppana on 2008-09-04
> **prshah said:**
> If you find that browsing is slower in Ubuntu than in XP using any browser, maybe you need to do the MTU fix as in [this post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12").

Just a suggestion, you may not need this, so please read the post thoroughly (maybe even the entire thread) before you attempt this.

Thanks for your reply, but my issues related to display speed only, not internet speed.

---

### Post by laptoppana on 2008-09-04
> **Martin_sensei said:**
> Could this be a graphics card issue?  Do you have the restricted drivers for you graphics card enabled?

I think this is available from the Administration menu under Hardware, or Restricted Hardware.

I went to hardware driver and found no *properties driver*.
And I could run Cube effect smoothly, do you think still graphic card issues?

---

### Post by prshah on 2008-09-04
> **laptoppana said:**
> The answer is NO, and here is the output of glinfo.
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)


Try this```

unset LIBGL_ALWAYS_INDIRECT
compiz --replace

```

Note: this may stop compiz from working; in that case

```

export LIBGL_ALWAYS_INDIRECT=0
compiz --replace

```

will get it back again.

---

### Post by laptoppana on 2008-09-05
> **prshah said:**
> Try this```

unset LIBGL_ALWAYS_INDIRECT
compiz --replace

```

Note: this may stop compiz from working; in that case

```

export LIBGL_ALWAYS_INDIRECT=0
compiz --replace

```

will get it back again.

I just tried it and I have problems immediately, all application hang and force me to restart. That why I can not copy the output of that code here. The speed of FireFox still very slow and sometime hang when I try to scroll heavy pages.
Anymore help, please!!!

---

### Post by Crafty Kisses on 2008-09-05
Post the results of > top

---

### Post by laptoppana on 2008-09-05
> **Codename said:**
> Post the results of > top

I do not understand, sorry because I am new in Ubuntu.

---

### Post by CheeseEatingBulldog on 2008-09-05
> **laptoppana said:**
> I do not understand, sorry because I am new in Ubuntu.

He means to ask if you would open a terminal (Applications>Accessories>Terminal) and type "top" and then post the info here.

It will show what processes / apps are eating your system resources. It could be that there is a process or app running in the background. Also, do you have a lot of add-ons in your firefox?

---

### Post by laptoppana on 2008-09-05
> **CheeseEatingBulldog said:**
> He means to ask if you would open a terminal (Applications>Accessories>Terminal) and type "top" and then post the info here.

It will show what processes / apps are eating your system resources. It could be that there is a process or app running in the background. Also, do you have a lot of add-ons in your firefox?


Ah, OK :-) Here it is, thanks

top - 21:36:48 up  2:34,  2 users,  load average: 0.24, 1.89, 1.55
Tasks: 118 total,   2 running, 115 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.7%us,  1.3%sy,  0.0%ni, 93.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    506424k total,   497476k used,     8948k free,     9232k buffers
Swap:   248968k total,   182724k used,    66244k free,   171408k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5203 root      20   0  275m  48m 6764 R  3.0  9.7   4:01.43 Xorg               
 4726 messageb  20   0  2828 1220  792 S  0.7  0.2   0:03.02 dbus-daemon        
 4963 haldaemo  20   0  6180 2664 2140 S  0.7  0.5   0:02.62 hald               
 5594 thanhlp   20   0 26384  13m 6704 S  0.7  2.8   0:31.70 compiz.real        
 9079 root      20   0  3880 1512 1236 S  0.7  0.3   0:00.02 wpa_supplicant     
 9439 thanhlp   20   0 75896  20m  11m S  0.7  4.2   0:01.86 gnome-terminal     
 9464 thanhlp   20   0  2308 1116  852 R  0.7  0.2   0:00.64 top                
 6202 thanhlp   20   0  240m  93m  20m S  0.3 19.0   5:25.22 firefox            
    1 root      20   0  2844 1424  508 S  0.0  0.3   0:02.56 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by Zorael on 2008-09-05
I'm sorry, what kind of video card is this? To get a detailed output, please enter this in a terminal and paste it here.
```
$ lshw -C video
```

---

### Post by laptoppana on 2008-09-05
I also see that all of memory used by aplication, is that the reason make firefox slow? And what is zombie? is that some kind of virus in Ubuntu?

---

### Post by laptoppana on 2008-09-05
> **Zorael said:**
> I'm sorry, what kind of video card is this? To get a detailed output, please enter this in a terminal and paste it here.
```
$ lshw -C video
```

I guess I have no problem with video card because I could run Compiz smoothly. Here is the output, please look through it:

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

---

### Post by jerome1232 on 2008-09-05
> **laptoppana said:**
> I also see that all of memory used by aplication, is that the reason make firefox slow? And what is zombie? is that some kind of virus in Ubuntu?

A zombie is just a process that's not using up cpu time.

For a better look at ram run free top doesn't report ram in a very human readable form, htop is a bit better but it's not installed by default

```
free -m
```

example output from my tiny home server, as you can see it has [COLOR="Teal"]114 MB of ram[/COLOR], [COLOR="DarkOrange"]15 MB aren't used[/COLOR], [COLOR="Green"]80 MB are avaible for use by applications[/COLOR], and [COLOR="DarkRed"]26 MB of swap is being used[/COLOR]
```
             total       used       free     shared    buffers     cached
Mem:           [COLOR="Teal"]114[/COLOR]         99         [COLOR="DarkOrange"]15[/COLOR]          0         22         42
-/+ buffers/cache:         34         [COLOR="Green"]80[/COLOR]
Swap:          313         [COLOR="DarkRed"]26[/COLOR]        287
```

---

### Post by laptoppana on 2008-09-05
No I did not install any new addon to FireFox

---

### Post by laptoppana on 2008-09-05
Thanks for your hint:

```

            total       used       free     shared    buffers     cached
Mem:           494        466         28          0         10        140
-/+ buffers/cache:        315        179
Swap:          243        173         69

```

May be I need to increase swap?

---

### Post by jerome1232 on 2008-09-05
I'm not sure if this is the problem but it looks to me like your swaping like mad.

That shows you have 179 MB freely available for applications yet your swap is roughly 3/4 of the way full, and that swap partition is a bit small I would've done 512 MB at least.

---

### Post by laptoppana on 2008-09-05
> **jerome1232 said:**
> I'm not sure if this is the problem but it looks to me like your swaping like mad.

That shows you have 179 MB freely available for applications yet your swap is roughly 3/4 of the way full, and that swap partition is a bit small I would've done 512 MB at least.

How can I increase swap file? It seems difficult task for beginer like me?

---

### Post by laptoppana on 2008-09-05
I just found some code to increase swap file, now the overall speed of computer has improve slightly but the display speed of firefox still slow

```
             total       used       free     shared    buffers     cached
Mem:           494        465         29          0          1        151
-/+ buffers/cache:        311        182
Swap:          536        169        366

```

---

### Post by jerome1232 on 2008-09-05
Well at least it's a little progress, I noticed in top you have alot of "k" apps which means your probably using Kubuntu, is konqueror slow or does it work fine? Can you test a few browsers out to see if this is a universal thing or if it is limited to firefox, try opera too.

Are you sure this is a local thing and not network related, I don't know why but some ISP's DNS servers just throw a hissy fit and work fine for windows computers but have serious lag when Ubuntu (I'm talking it added maybe a full minute to some sites) tries to connect. I've found OpenDNS remedied the slowness in those situtations.

I'm pretty much out of suggestions, 494 MB of ram ought to be enough to run your apps. I think officially Ubuntu says you should have 512 but 494 is 512 as far as I'm concerned. 

edit: Also have you tried turning off compiz might want to pursue the video route that was being talked about earlier in this thread.

---

### Post by snowpine on 2008-09-05
In my experience, 512mb is borderline for compiz desktop effects... I know you like the Cube but can you try disabling them as an experiment?

---

### Post by lakersforce on 2008-09-05
Read this thread, past the code (before you try anything): [[COLOR="Orange"]http://ubuntuforums.org/archive/index.php/t-423311.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-423311.html")

If
```

Direct Rendering: No
```

it might be a bug: [[COLOR="Orange"][URL="http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg559760.html"]http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg559760.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg561265.html")[/COLOR][/URL]

If you can confirm that it is a bug, you might consider to [[COLOR="Orange"]report it.[/COLOR]]("https://bugs.launchpad.net/")

I have an intel 965g (X3100) and it works out-of-box on the current Ubuntu Linux kernel (and on the 8.4 install disc).

---

### Post by Zorael on 2008-09-05
I had to add/modify these sections to my /etc/X11/xorg.conf to get *any* form of acceptable video performance on my intel chipset. This will fix sucky EXA performance (with MigrationHeuristic set to greedy) and enable AIGLX. Obviously the first Device section is your video card, so you should modify yours accordingly and not just add the section alongside your existing one.
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"DRI" "true"
	Option		"AccelMethod" "EXA"
	Option		"ExaNoComposite" "false"
	Option		"MigrationHeuristic" "greedy"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option		"AIGLX" "true"
EndSection

Section "DRI"
	Group		"video"
	Mode		0660
EndSection

Section "Extensions"
	Option		"Composite" "enable"
EndSection
```

See [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492).

---

### Post by laptoppana on 2008-09-06
I tried to install Opera but not success, some how it can not locate the server...

I did also disable the Cube, restart and test Firefox again, the speed is the same, no improve.

---

### Post by lakersforce on 2008-09-06
Your problems are not related to your browser, _but the fact_ that you don't have direct rendering (graphic card drivers) installed (anything else suggested in this thread is imho bad advice).

Your graphic card should be supported by default, because it is an intel, but by some weird reason it is not.

Sorry that I can't provide any more help.

Try to search around for a solution for your card. Your card should 100% work out-of-box!

---

### Post by laptoppana on 2008-09-07
> **lakersforce said:**
> Your problems are not related to your browser, _but the fact_ that you don't have direct rendering (graphic card drivers) installed (anything else suggested in this thread is imho bad advice).

Your graphic card should be supported by default, because it is an intel, but by some weird reason it is not.

Sorry that I can't provide any more help.

Try to search around for a solution for your card. Your card should 100% work out-of-box!

Thanks, how can I check my card support direct rendering or not?
Oop I found it in the top of this thread: glxinfo | grep rendering

---

### Post by sml on 2008-09-07
If you are looking for a fast & responsive desktop (particularly with your vintage PC) then perhaps give Puppy a spin .....

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)
[http://www.puppylinux.com/](http://www.puppylinux.com/)

It runs from RAM so there is no need to access data from some mechanically spinning disk! (ie the hard drive).

It won't be that long before every operating system runs entirely from RAM. Hard discs (both mechanical & solid state) will be just used for data storage.

---

### Post by laptoppana on 2008-09-07
I did add some more line to  the xorg.config as below

```
Section "DRI"
	Group		"video"
	Mode		0660
EndSection
```

Restart and got direct rendering is YES, cheers!!!!

```
direct rendering: Yes

```

But however I did the result the same, Firefox page scroll still slow! :-(

May be I need to add some more line specific to Intel card? Because in my xorg.config file only state very general as below:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Gamma 		0.6
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by laptoppana on 2008-09-07
> **sml said:**
> If you are looking for a fast & responsive desktop (particularly with your vintage PC) then perhaps give Puppy a spin .....

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)
[http://www.puppylinux.com/](http://www.puppylinux.com/)

It runs from RAM so there is no need to access data from some mechanically spinning disk! (ie the hard drive).

It won't be that long before every operating system runs entirely from RAM. Hard discs (both mechanical & solid state) will be just used for data storage.

No, I using laptop Panasonic, I liek it because very light, tough, handy even it quite old-vintage system.

---

### Post by laptoppana on 2008-09-07
I found a lot of topic around also complain about video card, but not many lucky with that. Do we have a better solution?

---

### Post by Zorael on 2008-09-07
Try adding this to your videocard device section as well.
```
Option		"MigrationHeuristic" "greedy"
```
Then open up **/etc/environment** and add this line to the bottom.
```
INTEL_BATCH="1"
```
Complete reboot, try again.

---

### Post by laptoppana on 2008-09-08
> **Zorael said:**
> Try adding this to your videocard device section as well.
```
Option		"MigrationHeuristic" "greedy"
```
Then open up **/etc/environment** and add this line to the bottom.
```
INTEL_BATCH="1"
```
Complete reboot, try again.

No result still the same, anyway thanks for the help!.

---

### Post by chrisme52 on 2009-07-12
I do recommend trying Opera.
I found it to work well on numerous versions of Kubuntu and is far supeerior to firefox.

---

