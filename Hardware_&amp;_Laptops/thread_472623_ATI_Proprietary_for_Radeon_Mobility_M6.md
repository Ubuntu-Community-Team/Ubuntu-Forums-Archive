---
title: "ATI Proprietary for Radeon Mobility M6"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by zeh on 2007-06-13
Hi,

I´m trying to replace the ATI open source drivers for the proprietary one. The reason is because DRI is not working anymore, and i don´t know why. Suddenly it stopped working and glxinfo gives no direct rendering.

I know that the latest release of fglrx doesn´t support the ATI mobility M6, but older versions does. Can i install an older version of ATI drivers in Feisty? Where can i donwload it?

Thank you!

---

### Post by Gagle on 2007-06-13
You can use the older drivers.  I would use Aiglx and the Ubuntu 6.10 method :
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

You won't get max. support but it is the safe way I believe.  

hope it helps,

gagle

---

### Post by trippinnik on 2007-06-13
That link just seems to go the the Beryl howto page.  Since you mentioned that 'it stopped working' maybe we should find out what changed.  Maybe you could post your xorg.conf,or checkout this thread [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746).

---

### Post by Kubunteando on 2007-06-14
Not tested myself, but according to many posts if you install the proprietary drivers those don't support AIGLX, so you have to install Beryl with Xgl, so changing the drivers means you may need to change the least some configurations on Beryl and X.Org.

I have an ATI Radeon Mobility 9000 and I tried both, the Open Source and the proprietary. And the Open Source lets you play more games, like Sauerbraten and Regnum Online (for Regnum Online you need the latest version of the Open Source which is 6.5.3 not included in Feisty, but downloadable from [www.mesa3d.org](www.mesa3d.org)).
Also you can run Google Earth natively on Linux. On the other hand you get a bit reduced performance but you win stability and continuous support.

---

### Post by zeh on 2007-06-14
Thank you all for the replies.

Actually, I don´t want to install Beryl, because its performance in my M6 is very poor. I just want to try the proprietary drivers to get graphic performace like i get in windows. The performance of the open drivers in linux (ati, or radeon drivers) is not good, even in 2d, like resizing windows, refreshing window contents.

I´ll try your tip and I´ll post my xorg.conf and xorg log as soon as i get home.

Thanks!

---

### Post by zeh on 2007-06-14
Hi,

here is my xorg.conf and xorg.0.log

I've tried different configurations with no success...
tried removing the Extensions and ServerFlags, changing "radeon" to "ati", removing all Device options...
I think this started when i tried to install fglrx. I think this driver replaced something and now i cant get DRI. The strange thing is that there is no errors in xorg log, as you can see attached. I also tried to reinstall xorg, radeon, and ati drivers. Nothing...

 If i do a complete feisty reinstall, i get DRI... :confused:

---

### Post by Kubunteando on 2007-06-15
I have an ATI Radeon Mobility 9000, and I tried to install the ATI proprietary drivers 8.28, but they seem not to be compatible with the new kernel... So I stick to the Open Source ones.
I find the performance quite good, I can run Beryl smoothly.

Try to reinstall the packages "libgl1-mesa-glx" and "libglu-mesa", just use adep, right-click and reinstall.

---

### Post by Kubunteando on 2007-06-15
How about the output of "glxinfo"?

---

### Post by zeh on 2007-06-15
> **Kubunteando said:**
> I have an ATI Radeon Mobility 9000, and I tried to install the ATI proprietary drivers 8.28, but they seem not to be compatible with the new kernel... So I stick to the Open Source ones.
I find the performance quite good, I can run Beryl smoothly.

Try to reinstall the packages "libgl1-mesa-glx" and "libglu-mesa", just use adep, right-click and reinstall.

Hi! Thanks for the reply.

I made the reinstall you've suggested...Nothing yet...
Isn't this odd? :frown:

Here is my glxinfo output:

> 
zeh@zeh-presario:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 x86/MMX/SSE NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by Kubunteando on 2007-06-16
I would try the following:

- in xorg.conf comment out load "GLcore", just to clean it
- comment out 	Option "BusType" "PCI", the card is detected as AGP, but this is preventing to use AGP, so it will be slow.

- reinstall the package "mesa-utils"

If you still get the same result afterwards, check how many FPS you get when you execute "glxgears". According to Xorg.0.log DRI HW acceleration is enabled. What looks bad is the Opengl client being ATI instead of SGI. So the problem looks to be in some library.

When you installed the fglrx driver, this replaced some OpenGL libraries.
So to be sure of solving the issue I would install fully MESA.

---

### Post by zeh on 2007-06-16
> **Kubunteando said:**
> I would try the following:

- in xorg.conf comment out load "GLcore", just to clean it
- comment out 	Option "BusType" "PCI", the card is detected as AGP, but this is preventing to use AGP, so it will be slow.

- reinstall the package "mesa-utils"

If you still get the same result afterwards, check how many FPS you get when you execute "glxgears". According to Xorg.0.log DRI HW acceleration is enabled. What looks bad is the Opengl client being ATI instead of SGI. So the problem looks to be in some library.

When you installed the fglrx driver, this replaced some OpenGL libraries.
So to be sure of solving the issue I would install fully MESA.

Hi!

I've done everything you've suggested. Nothing yet..
Here is my glxresults:
> 
2353 frames in 5.3 seconds = 440.536 FPS
2155 frames in 5.4 seconds = 402.466 FPS
2165 frames in 5.4 seconds = 404.602 FPS
2160 frames in 5.4 seconds = 402.449 FPS
2160 frames in 5.4 seconds = 397.817 FPS
2160 frames in 5.4 seconds = 398.884 FPS
2158 frames in 5.3 seconds = 404.370 FPS
2160 frames in 5.4 seconds = 401.915 FPS


The strange thing is that glxgears shows a nice FPS, but the gears actually spins very slow...

---

### Post by zeh on 2007-06-16
:popcorn:

Hi Kubunteando,

I FINALLY GOT IT!!!! \\:D/
I paid attention to your observation **"what looks bad is the Opengl client being ATI instead of SGI "**
So....after googling **A LOT** about libraries and manually replacing symlinks for libGL.so.1.2, with no sucess, ](*,) i found a nice tip in this page:

[[COLOR="YellowGreen"]**http://wiki.linuxquestions.org/wiki/Library-related_Commands_and_Files#ldconfig**[/COLOR]]("http://wiki.linuxquestions.org/wiki/Library-related_Commands_and_Files#ldconfig")

I used the command **ldconfig** that recreated the symlinks, and created a proper symlink (libGL.so.1) in /usr/lib!

Now i get direct rendering!
Man, this fglrx made a real mess!! :twisted:
I think the unistall script for fglrx don't do a complete job.

Thanks a lot for your replies. It helped a LOT!!!

---

