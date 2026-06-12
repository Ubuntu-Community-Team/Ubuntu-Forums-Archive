---
title: "Videocard Woes"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by mrcbrown on 2005-06-20
I have been trying to get my ATI Radeon 9600SE to work under Ubuntu - while I have active video, and my LCD is showing things properly, video (dvd/mpeg) is lagged, I have tried a few players to make sure it wasnt something software related, but it just seems no matter what I do - the ATI drivers end up making things worse off than using the stock driver it installed with.

So my question is this - can anyone give me some tips/xorg confs to make my ATI work? or should I just snag a Nvidia 5200 or something on the cheap? Just looking for something to make this smooth and easy. Any help is appriciated - I have tried all the ATI How-to's on here, and other forum suggestions for linux in general running ATI - while some report AWESOME enhancements, I am just not seeing them - so if it's easier for me to get a Nvidia card on sale at the geeks - I'd just as soon do that for ease of install, drivers etc.

Anything is appriciated.

---

### Post by Arktis on 2005-06-21
I've got a 9600 and it's working okay with 3d acceleration (~2700 fps with glxgears, ~500 fps with fgl_glxgears). What steps exactly were you getting stuck on?

Here are some commands you can run and post the output of :

glxgears
fgl_glxgears
glxinfo
fglrxinfo
gedit /var/log/Xorg.0.log

Of course, none of those will actually be useful if you have not followed the steps in the howtos that can be found on this fourm.

One side note though : When it says to get the rpm in addition to the .run file, I didn't. I got that part via synaptec (xorg-driver-fglrx); I wanted to ensure compatibility with future upgrades.

Also, I have an FX 5200 which was in this computer before my ati card... if I recall it wasn't easy for me to get set up either, but that was also several months ago. Besides, from personal experience, I'd say it's a pretty crappy card. I'm ashamed I ever bought the thing.

---

### Post by mrcbrown on 2005-06-21
Yeah did that one - it does get my glxgears FPS up - but for instance tuxracer won't render worth anything - slow, laggy, and on a similar machine running FedoraCore 2 (media rig for TV/PVR) - it has a NVida 5200 - Tuxracer runs without issue.

This is what is weird though:

```

cbrown@bigboy:~$ fgl_glxgears
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

``` 

Whereas just plain glxgears reports back;

```

cbrown@bigboy:~$ glxgears
1200 frames in 5.0 seconds = 240.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1424 frames in 5.0 seconds = 284.800 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

Only thing I can come up with is this is a "SE" card, "budget" card so to speak, so my thought is its not 'complete' definately doing that how-to did up my FPS about 100+ from the stock ATI driver that loads after first boot, but I had hoped for more :)

Here are the others:

```

cbrown@bigboy:~$ glxinfo
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

```

cbrown@bigboy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I am going to go over the X log here, twas fairly large, see if there's anything odd with that - we over it once before didn't notice anything funky, but heck been working on this at odd late night hours - for all I know i've got a typo somewhere - just hoping it's not SE related, and can save my self a couple bucks.

---

### Post by Arktis on 2005-06-21
> ```

cbrown@bigboy:~$ glxgears
1200 frames in 5.0 seconds = 240.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1424 frames in 5.0 seconds = 284.800 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

 ```

 cbrown@bigboy:~$ fglrxinfo
 display: :0.0  screen: 0
 OpenGL vendor string: Mesa project: www.mesa3d.org
 OpenGL renderer string: Mesa GLX Indirect
 OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
 
```

Just as I thought, your 3d accel is installed but OFF. Something is preventing it from loading. Your fps output from glxgears is way too slow and your fglrxinfo output shows you're running OpenGL indirectly.

That log will probably say WHY. The whole thing is too big to post, so just look for lines in it that start with (WW) and (EE) and post those. WW=warning, EE=Error.

---

### Post by mrcbrown on 2005-06-21
[QUOTE=Arktis]Just as I thought, your 3d accel is installed but OFF. Something is preventing it from loading. Your fps output from glxgears is way too slow and your fglrxinfo output shows you're running OpenGL indirectly.

That log will probably say WHY. The whole thing is too big to post, so just look for lines in it that start with (WW) and (EE) and post those. WW=warning, EE=Error.[/QUOTE]
 ```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d1f000 at 0xb7dad000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

There ya have it - going to try shutting off DRI and see if it makes any difference.

Update: Nope :( Any ideas / help are appriciated.

---

### Post by Arktis on 2005-06-21
Yeah, turning off dri isn't going to help.  Heheh. =p

Okay, so your kernel module or the driver is the wrong version for some reason... At this point I have to stop, because I don't know what you should do other than start the install process over or make sure you've got the linux-restricted-modules corresponding to your kernel version. BUT now that the problem seems identified, someone else with more knowledge should be able to assist.

I *KNOW* you can get this working.  SO good luck.

---

### Post by mrcbrown on 2005-06-21
[QUOTE=Arktis]Yeah, turning off dri isn't going to help.  Heheh. =p

Okay, so your kernel module or the driver is the wrong version for some reason... At this point I have to stop, because I don't know what you should do other than start the install process over or make sure you've got the linux-restricted-modules corresponding to your kernel version. BUT now that the problem seems identified, someone else with more knowledge should be able to assist.

I *KNOW* you can get this working.  SO good luck.[/QUOTE]

Well thanks for joggin my brain to read the log - looked over it so many times, but just so frickin long lol - i'm gonna poke at it a bit more, but maybe it's just a sign to goto sleep.

---

### Post by Arktis on 2005-06-21
oh yeah, have you done this?: 
 
 cd /lib/modules/fglrx/build_mod
 
 sudo sh make.sh
 
 cd /lib/modules/fglrx/
 
 sudo sh make_install.sh



Oh yeah, then after that I read somewhere that I should do this :

 sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME

replace 2.6.10-5-386 with whatever your kernel version is. But, only do it if you did the steps above and it still isn't working.

Edit: I edit my posts a lot =p

---

### Post by mrcbrown on 2005-06-21
[QUOTE=Arktis]oh yeah, have you done this?: 
 
 cd /lib/modules/fglrx/build_mod
 
 sudo sh make.sh
 
 cd /lib/modules/fglrx/
 
 sudo sh make_install.sh



Oh yeah, then after that I read somewhere that I should do this :

 sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME

replace 2.6.10-5-386 with whatever your kernel version is. But, only do it if you did the steps above and it still isn't working.

Edit: I edit my posts a lot =p[/QUOTE]


Yeah - sadly it didnt help - but I do appriciate the help - I did notice after some tweaks I am getting this:

```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 SE (RV350 4151) found
-=-=-=-=-=- scrolling down -=-=-=-=-=-
(WW) fglrx(0): board is an unknown third party board, chipset is supported

```

I am starting to think a non-SE or NVidia card may be in order - I am guessing its something to do with the dreaded "SE" that the driver isnt fully understanding - dang budget cards!

---

### Post by Arktis on 2005-06-21
I get the same 2 error messages. It's just saying that there is no entry in xorg.conf for your 2ndary card output; your svideo out. You'll note the bus ID it talks about is not the bus ID in your xorg.conf, but the next increment beyond that. I never bothered to put the 2nd entry in my xorg.conf, I still have that error message, and everything works fine. The chipset warning you can also ignore, it's just saying that the card has a radeon chipset but is manufactured by a third party. It's supported. =)

---

### Post by mrcbrown on 2005-06-21
[QUOTE=Arktis]I get the same 2 error messages. It's just saying that there is no entry in xorg.conf for your 2ndary card output; your svideo out. You'll note the bus ID it talks about is not the bus ID in your xorg.conf, but the next increment beyond that. I never bothered to put the 2nd entry in my xorg.conf, I still have that error message, and everything works fine. The chipset warning you can also ignore, it's just saying that the card has a radeon chipset but is manufactured by a third party. It's supported. =)[/QUOTE]
 Odd indeed. Maybe it's time to step back, slip and fall onto the bed ;)

---

### Post by mrcbrown on 2005-06-21
Well I think its half working now - basically now though when I run either gears I get either lockup or screen gets distorted and must be restarted.

I may be getting somewhere.. just not sure where ;)

---

### Post by mrcbrown on 2005-06-21
```

cbrown@bigboy:~$ fgl_glxgears
603 frames in 5.0 seconds = 120.600 FPS
774 frames in 5.0 seconds = 154.800 FPS
792 frames in 5.0 seconds = 158.400 FPS
779 frames in 5.0 seconds = 155.800 FPS
cbrown@bigboy:~$ glxgears
3547 frames in 5.0 seconds = 709.400 FPS
3713 frames in 5.0 seconds = 742.600 FPS
3711 frames in 5.0 seconds = 742.200 FPS
3714 frames in 5.0 seconds = 742.800 FPS

```

I'll write up in more detail the steps from various threads I did plus the stuff in this thread, all in all, it came down to conf after all that - at this point just happy to be able to run fgl_glxgears without having system lockups - so much for uptime! :)

---

### Post by pablito on 2005-07-24
Any chance you could write up those steps?!  I think I'm seeing the same problem.

P.

---

### Post by hikenboot on 2006-10-21
I am not sure but I have had similar direct rendering no problems on the nvidia video card it works if i start in maintenance mode and startx from the command line as root but does not work as a normal user. I believe this to be a rights issue with /dev/nvidia* chmod 777 /dev/nvidia* does not work because pam is reverting it back to rw rw rw I think it should be rwx rwx rwx or somthing like that but Iwould think this would cause security issues.

regards,

steve
hikenboot<remove this for no spam >@yahoo.com

---

