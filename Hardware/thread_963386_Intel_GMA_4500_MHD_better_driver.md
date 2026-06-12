---
title: "Intel GMA 4500 MHD better driver?"
date: 2008-10-30
forum: Hardware
---

### Post by rasmus91 on 2008-10-30
Hey

Hey all, i have a Dell E6400 with a Intel(R) GMA 4500 MHD grafik card. Literally, i can just forget running anything 3D. If i do ```
glxgears
``` i only get 300 fps per second. while i should get approximately 1000+ 

I can't run anything 3D or any game with nice graphics, either it will lagg so much that i can forget everything about playing, or else the screen will screw up.

I think the problem is the driver. Does anybody know about a better driver for this computer? I run Ubuntu 8.10 64 bit. and i think everything else is running just fine.

So, any link or any idea is welcome.

(i already have tried disabling compiz, didn't help me at all.)

---

### Post by garyedwardjohnston on 2008-10-30
Try Envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Or maybe even the manufacturers website.

---

### Post by kempo on 2008-10-30
> **rasmus91 said:**
> Hey

Hey all, i have a Dell E6400 with a Intel(R) GMA 4500 MHD grafik card. Literally, i can just forget running anything 3D. If i do ```
glxgears
``` i only get 300 fps per second. while i should get approximately 1000+ 

I can't run anything 3D or any game with nice graphics, either it will lagg so much that i can forget everything about playing, or else the screen will screw up.

I think the problem is the driver. Does anybody know about a better driver for this computer? I run Ubuntu 8.10 64 bit. and i think everything else is running just fine.

So, any link or any idea is welcome.

(i already have tried disabling compiz, didn't help me at all.)

You're one step ahead of me! I can't even get the intel drivers to work - I'm stuck on vesa. I had to add a vga entry to menu.lst to even get 1280x800 out of the card.

Would you mind posting up your xorg.conf so I can see what you've done?

Many thanks!

---

### Post by phidia on 2008-10-30
Envy only works for ati & nvidia drivers-so don't try that.

The intel website is a good idea and there is a driver there for your card. However I've read installing that driver is presently more for developers or advanced users.

Look at this [thread]("http://ubuntuforums.org/showthread.php?t=928668") and see if the driver from the last post there will work.

If it does report back as others are looking to get that card working too.

I'm going to include a [link to the site]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/") with drivers for both 64 & 32 bit architectures.
If the intel card can work well it would be a good deal for everyone.

---

### Post by rasmus91 on 2008-10-31
> You're one step ahead of me! I can't even get the intel drivers to work - I'm stuck on vesa. I had to add a vga entry to menu.lst to even get 1280x800 out of the card.

Would you mind posting up your xorg.conf so I can see what you've done?

Many thanks!

Love to, But how to do that?

---

### Post by rasmus91 on 2008-10-31
> I'm going to include a link to the site with drivers for both 64 & 32 bit architectures.
If the intel card can work well it would be a good deal for everyone.

Sorry man, but a newer driver comes preinstalled in 64 bit ubuntu 8.10

---

### Post by phidia on 2008-10-31
> **rasmus91 said:**
> Sorry man, but a newer driver comes preinstalled in 64 bit ubuntu 8.10sic

Why isn't it working then? If you read the responses at that site you'll see that people had problems with the 2.4.1 driver.

---

### Post by jtherrie on 2008-11-02
I am also having problems with this chip except the problem is compounded by a native screen resolution of 1600x900. If I just try to let Ubuntu(or Kubuntu, and both tried as 8.04 and 8.10) pick the video settings I get a white screen. To get anything I have to boot in vesa mode at 800x600, and vesa wouldn't bother me so much but I cannot figure out how to set the resolution to 1600x900. Thanks in advance.

---

### Post by entner on 2008-11-02
I have a Dell Latitude E6400 with Intel X4500 graphics. Interestingly I get only 225 FPS using Compiz and with my CPU scaling setting to "ondemand" which is default in Ubuntu 8.10. Turning CPU scaling to "performance" gives me above 400 FPS.
Openarena gives me quite nice results I think, at least for an Intel graphics. [_Here is my full report about Ubuntu on the Latitude E-Series_]("http://www.entner.net/blog/dell-latitude-e6400-with-ubuntu-intrepid-ibex-810-english").
I am still surprised that glxgears results are that bad. Maybe the driver has to mature?!

---

### Post by entner on 2008-11-22
I tried with a Hardy live CD and got 1300 FPS in glxgears. There seems to be a performance problem with the new -intel driver. Also in Intrepid full screen Flash videos (Youtube) are not smooth.

---

### Post by 4Play on 2008-11-29
Hello, I have a vaio SR-130N that uses the Intel GMA 4500MHD graphics controller, and I'm going crazy trying to get the damn thing working well enough to run compiz ( a must for me )

anyway, I got the 1280x800 resolution working by modifying xorg.conf, here is mine:

```
Section "Monitor"
	Identifier  "LVDS"
	VendorName  "Sony"
	ModelName   "Vaio SR X-black LED"
   	Option      "DPMS"
	Modeline    "1280x800_76.00"  108.77  1280 1360 1496 1712  800 801 804 836  -HSync +Vsync
	HorizSync   62-63
	VertRefresh 76-77
    	Option      "Monitor-LVDS" "LVDS monitor"
EndSection


## Graphics card driver
Section "Device"
	Identifier  "Card0"
    	Driver      "vesa"
    	#Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Cantiga Integrated Graphics Controller (Q45)"
    	Option      "MonitorLayout" "LVDS"
	BusID       "PCI:0:2:0"
EndSection


## Display settings
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "LVDS"
        DefaultDepth 24
	SubSection "Display"
	Viewport   0 0
	Depth     24
	EndSubSection
EndSection
```

i got this from [here]("http://forum.notebookreview.com/showthread.php?t=318862")

but if I have to use vesa I might as well go back to using XP/Vista. If someone got the real drivers working please point the way!

---

### Post by Demophobie on 2008-11-30
I want to buy a dell E4300 which has this card.

I hope this gets fixed :(

---

### Post by Demophobie on 2008-11-30
Btw: Did you ever tried this here? 

[https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)

Comment 122/123 and 145 sounds interesting

Ppl get like 700 fps

---

### Post by 4Play on 2008-11-30
thanks for the link Demophobie, indeed the workaround proposed on posts 122/123 and summarized on 145 are a good bet. I will try them.
That bug report seems to be the place where most progress is being made to correct this issue, so ill keep a close watch there...it shouldn't take long for a more complete solution to come out (hopefully [-o< )

---

### Post by Demophobie on 2008-12-01
Ah great 4play,

hope u succeed. I want to buy a Dell E4300 with this card and 700 fps would be nice ;)

Oh btw: Is a plugged extern monitor still flickering? I saw some ppl on launchpad who reported this bug.

What does glxinfo | grep rendering give?

---

### Post by rasmus91 on 2008-12-02
I don't get what to do through this link... or how this should help me

---

### Post by Demophobie on 2008-12-02
Let's wait. I think 4Play will upload the solution soon :popcorn:

---

### Post by geckon on 2008-12-05
Hi everyone,

is there any solution, which makes GMA 4500 working fully in ubuntu? (No matter if it is for 8.04 or 8.10)
I want to buy a laptop with this chip so I am interested in.

Thaks a lot;)

---

### Post by nightfrost on 2008-12-05
> **geckon said:**
> Hi everyone,

is there any solution, which makes GMA 4500 working fully in ubuntu? (No matter if it is for 8.04 or 8.10)
I want to buy a laptop with this chip so I am interested in.

Thaks a lot;)

It seems the mileage indeed varies wrt this problem. I started subscribing to this thread since I had ordered a new laptop recently with this chip, hoping that a solution would show up in time since compiz is a must for me as well. The laptop is here now, and I've had no problems whatsoever with compiz. It runs perfectly fine and glxgears gives above 1000 fps. I've no clue why, but I'm not complaining :-)

---

### Post by 4Play on 2008-12-05
> **nightfrost said:**
> It seems the mileage indeed varies wrt this problem. I started subscribing to this thread since I had ordered a new laptop recently with this chip, hoping that a solution would show up in time since compiz is a must for me as well. The laptop is here now, and I've had no problems whatsoever with compiz. It runs perfectly fine and glxgears gives above 1000 fps. I've no clue why, but I'm not complaining :-)

That's great! what notebook do you have?
The black screen problem is notorious on Sony laptops, and on Lenovo's X200 as well.

The bug report @ [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292) (see post 122-126) does list a 'fix' but it is one I would not recommend to those less experienced in linux (i include myself in this group :p) since you have to edit one of the drivers source files, and complie/install it manually, no problems there, but if a kernel update comes along, the driver will probably no longer work, and you will have to re-compile it, and hope for it to work..

---

### Post by nightfrost on 2008-12-05
> **4Play said:**
> That's great! what notebook do you have?
The black screen problem is notorious on Sony laptops, and on Lenovo's X200 as well.

The bug report @ [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292) (see post 122-126) does list a 'fix' but it is one I would not recommend to those less experienced in linux (i include myself in this group :p) since you have to edit one of the drivers source files, and complie/install it manually, no problems there, but if a kernel update comes along, the driver will probably no longer work, and you will have to re-compile it, and hope for it to work..

I have an ASUS N20A.
Thanks for the link, by the way. I'll take a look at that.

---

### Post by nightfrost on 2008-12-06
Not all is as good as it seems. I'm severely hit by this bug [https://bugzilla.redhat.com/show_bug.cgi?id=472935](https://bugzilla.redhat.com/show_bug.cgi?id=472935). (There are a couple of ubuntu bugs to the same effect, but they're a bit more confused).

---

### Post by geckon on 2008-12-06
> **nightfrost said:**
> It seems the mileage indeed varies wrt this problem. I started subscribing to this thread since I had ordered a new laptop recently with this chip, hoping that a solution would show up in time since compiz is a must for me as well. The laptop is here now, and I've had no problems whatsoever with compiz. It runs perfectly fine and glxgears gives above 1000 fps. I've no clue why, but I'm not complaining :-)

So is it working out-of-the-box in 8.10?

---

### Post by nightfrost on 2008-12-06
> **geckon said:**
> So is it working out-of-the-box in 8.10?

Yes, it does, at least for me. But if you run compiz, then:

> 
Not all is as good as it seems. I'm severely hit by this bug [https://bugzilla.redhat.com/show_bug.cgi?id=472935](https://bugzilla.redhat.com/show_bug.cgi?id=472935). (There are a couple of ubuntu bugs to the same effect, but they're a bit more confused).

---

### Post by Demophobie on 2008-12-07
@nightfrost

Thanks for the info.
What gives: glxinfo | grep direct ?

---

### Post by nightfrost on 2008-12-07
> **Demophobie said:**
> @nightfrost

Thanks for the info.
What gives: glxinfo | grep direct ?

Hey, sorry for being so slow...

"glxinfo | grep render" gives
```

direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
```

---

### Post by farmfield on 2008-12-08
This is so weird.

I also have a 4500 MHD and the performance in Compiz is (/feels imho) great, I can run VLC full screen, rotate the 'cylinder' (deform plugin) with 3D windows a.s.o. without glitches...

At the same time I get just below 800 fps in GLXGears. I also noticed my glxgear fps decreasing as I scale down my CPU - so there's obviously a lot of CPU-emulation going on here - but why?

...and yeah, I get **Direct: Yes** in **glxinfo | grep direct** - so there's DRI - but I have a strong feeling that's due to the availability of CPU-emulation, not the x4500 hardware...

I can conclude this, though; Whatever the reason for this, it sux. Intel is the only company providing open source drivers, this should have been solved ny now...

---

### Post by dcast on 2008-12-08
In the next release of Ubuntu, they will have the 2.6.28 Kernel which has the Intel GEM (Graphics Execution Manager) drivers which are supposed to have way better support for Intel IGPs. GEM has already been merged into Fedora 10, you might give that a shot as a test. I was running it on my laptop with the X3100 graphics, and I didn't see a noticeable difference, between that and properly configured Debian Lenny xorg configuration. Of course mileage may vary.

---

### Post by farmfield on 2008-12-11
...did I forget to tell you I got 200+ fps on glxgears in Mandriva..?

Once again I just don't get it, hehe, why it differ...

---

### Post by Demophobie on 2008-12-14
How's 2nd monitor working on ubuntu 8.10 with this card?

---

### Post by mathias_sundman on 2008-12-17
I have a Dell E6500 with intel GMA 4500MHD graphics and am experiencing the same kind of problems.

Ubunutu 8.10 works fine out of the box, however graphics is very slow. Changing AccelMethod to XAA in Xorg.conf made 2D graphics like switching desktops and draging windows alot faster, but glxgears still sucks at about 200 FPS.

Disabling CPU scaling to force full CPU freq gives better glxgears results, and running with the VESA driver gives about the same performance which tells me hardware acceleration does not seem to be used at all :(

Yesterday I installed Fedora 10 on the same system and got about 1200 FPS in glxgears out-of-the-box!

That was with their 2.6.27 kernel. Have thay backported GEM support to 2.6.27? I thought that was only available in 2.6.28, so I was surprised that it worked so much better in Fedora than under Ubuntu.

Any way to determine if GEM is used or not?

Any way to determine it the GPU is accually used to hardware accelerate or if mesa is software emulating the 3D functions?

---

### Post by Demophobie on 2008-12-18
Try to use this driver if u know how to compile:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

And do the patch the ppl did in the link i posted.

This brings 770 fps in Ubuntu 8.10

---

### Post by farmfield on 2008-12-18
> **Demophobie said:**
> Try to use this driver if u know how to compile:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

And do the patch the ppl did in the link i posted.

This brings 770 fps in Ubuntu 8.10
But I already got just belov 800 fps with the current driver available in the repositorys - why don't you?

I also want to clarify that I had just below 600 FPS in Ubuntu 8.10 at first, then tried Mandriva 2009.0 where I got 200 fps more - that's 800 - and I failed to make that clear in my previous post. After using the xorg.conf from Mandriva (though somewhat cleaned up) I get the same fps in Ubuntu.

Are you folks shure you actually use the correct driver? The correct package - which is based on the 2.5.1-driver is **xserver-xorg-video-intel**...

Also **try my xorg.conf** as posted in this thread.

---

### Post by mathias_sundman on 2008-12-18
If I force the CPU freq to max (2.54GHz) by disabling CPU scaling I get about 400 FPS with glxgears

```

echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Earlier a prepackaged ubuntu package of the intel-video 2.5.1 driver was available at [http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xserver-xorg-video-intel/](http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xserver-xorg-video-intel/) named

```
xserver-xorg-video-intel_2.5.1~git20081113_i386.deb

```

That's the one I'm currently using, and the Xorg.log confirms that it's accaully using it:

```

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.5.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41

```

I'll go ahead try to build the lastest versions of xf86-video-intel
, mesa, drm and libdrm available via git from [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by Demophobie on 2008-12-19
I will get my Dell Laptop (with this card) tomorrow. 
I will let your know how it works for me.

---

### Post by aeid79 on 2008-12-21
while i was searching , i came across this : 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/271059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/271059)

[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)

i tested 9.04 alpha 2 but i still have the same problem,please let me know if it worked with anyone else

---

### Post by Demophobie on 2008-12-21
> **farmfield said:**
> But I already got just belov 800 fps with the current driver available in the repositorys - why don't you?

I also want to clarify that I had just below 600 FPS in Ubuntu 8.10 at first, then tried Mandriva 2009.0 where I got 200 fps more - that's 800 - and I failed to make that clear in my previous post. After using the xorg.conf from Mandriva (though somewhat cleaned up) I get the same fps in Ubuntu.

Are you folks shure you actually use the correct driver? The correct package - which is based on the 2.5.1-driver is **xserver-xorg-video-intel**...

Also **try my xorg.conf** as posted in this thread.

Still dont get it. What xorg.conf are u talking abount? Can't find it in this thread.
What driver are u talking about. The one in the 8.10 is not based on 2.5.1, i think its 2.4.0

---

### Post by densou on 2008-12-21
well, I get more than 1200 FPS on glxgears with a poor GMA950.

Anyway, I think GMA4500 support it's still weak and I hope next release (2.6.0 + libdrm 2.4.2) could improve it, especially they should fix [this issue]("http://git.kernel.org/?p=linux/kernel/git/anholt/drm-intel.git;a=commit;h=2052746fc8397130c120f0194a89938b0b62b6cb") (or with a new kernel, I'm not very acquainted on Linux)

Check my xorg backups:
(hardy) [http://spazioinwind.libero.it/densou/xorg.conf](http://spazioinwind.libero.it/densou/xorg.conf)
(after dist-upgrade to intrepid) [http://spazioinwind.libero.it/densou/xorg.conf.ibex](http://spazioinwind.libero.it/densou/xorg.conf.ibex)
(after updating to 2.5.1) [http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

Feel free to ask, don't be afraid :P

---

### Post by Demophobie on 2008-12-22
i get about 2800 FPS when i use a lot of the cpu, wow
being idle i get 200

---

### Post by densou on 2008-12-22
> **Demophobie said:**
> i get about 2800 FPS when i use a lot of the cpu, wow being idle i get 200

with EXA or XAA ? :)

---

### Post by Demophobie on 2008-12-22
> **densou said:**
> with EXA or XAA ? :)

XAA. My xorg.xonf looks like this:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod"   "XAA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Module"
        Load "glx"
        Load "dri"
EndSection


For example: Start glxgears, put it in the background and start a program like thunderbird, then close it:

959 frames in 5.0 seconds = 191.720 FPS --> idle
81440 frames in 5.0 seconds = 16287.997 FPS --> thunderbird checking emails
46243 frames in 5.0 seconds = 9248.402 FPS --> i closed thundbird
979 frames in 5.0 seconds = 195.648 FPS --> idle

FPS seams to be ~ to cpu usage ^^

---

### Post by densou on 2008-12-22
let's think .... 
- your card works slowy due to a basic support (next release should improve it)
or
- settings are not ok yet

I get 1200-1300 FPS with a GMA950 (i945) in both idle and heavy load (several tabs opened on Firefox + Evolution checking e-mails) condition 

[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

maybe you could try my config (first make a backup of yours!)

---

### Post by Demophobie on 2008-12-22
> **densou said:**
> let's think .... 
- your card works slowy due to a basic support (next release should improve it)
or
- settings are not ok yet

I get 1200-1300 FPS with a GMA950 (i945) in both idle and heavy load (several tabs opened on Firefox + Evolution checking e-mails) condition 

[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

maybe you could try my config (first make a backup of yours!)

Hi!

tried your xorg.conf.
Same results. :lolflag:

btw: i tried newest intel driver too, same result

---

### Post by densou on 2008-12-22
:-k  whoops, you could also need to edit /etc/modules and add:
agpgart
intel-agp
drm
(if not present, of course)

or I assume it's driver fault ;)

Could you paste your 'glxinfo' results ? (useful for other users too)

---

### Post by Demophobie on 2008-12-25
> **densou said:**
> :-k  whoops, you could also need to edit /etc/modules and add:
agpgart
intel-agp
drm
(if not present, of course)

or I assume it's driver fault ;)

Could you paste your 'glxinfo' results ? (useful for other users too)

Driver fault.
Still 199 fps.

Hope that 2.6.0 helps. Can't compile the latest version, dont know why.

---

### Post by Demophobie on 2008-12-30
oh i forgot glxinfo:

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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x59  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5a  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6b  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x70  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x71  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by mathias_sundman on 2008-12-30
I just upgraded my Jaunty partition with the latest packages (apt-get upgrade) and forced installation of the latest kernel (2.6.28-4).

After that X started working again! Last time I forced upgrading all Xorg-related packages a few weeks ago X couldn't initialize the display at all.

Anyway, after this last upgrade the intel driver seems to work much better. I can now use EAX acceleration and get about 870 FPS with glxgears, and decent 2D graphics.

x11perf --aa10text now gives about 120000/sec with EAX acceleation. So XAA acceleration with the old driver still gave slightly better 2D performance, but nothing that bothers me.

I've tried upgrading to a whole bunch of diffrent releases of the latest intel-drivers, drm, mesa on my 2.6.27 based ubuntu 8.10 system without getting any better performance so I guess it's the GEM support in the 2.6.28 kernel that's the magic spot.

So I guess we'll simply have to wait for Jaunty to get stable enough for production use, or manually install a 2.6.28 kernel and upgrade Xorg and the intel driver on a Ubunutu 8.10 system.

I give up for now. 3D performance is not that important to me. But atleast now I know there is progress on the way...

---

### Post by farmfield on 2008-12-31
Weird, I've had 8-900fps in glxgears for months now, since I 'stole' my xorg.conf from a Mandriva install and I also always had good 2D-performance... A decent driver for the 4500 should give at least 2.000+ fps in glxgears concidering Windows-performance (similar to Nvidia 8200M)...

I also wonder why I don't have the same issues as you do...

---

### Post by densou on 2009-01-01
> **Demophobie said:**
> Hope that 2.6.0 helps. Can't compile the latest version, dont know why.

I did it at ease (2.5.1), but FIRST you need to compile/install LIBDRM (Intrepid has 2.3.1 default, which not suits for newer releases .... shameful Canonical :( )

Here you are the backports for Intrepid (already .deb !),
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)


> **mathias_sundman said:**
> I just upgraded my Jaunty partition with the latest packages (apt-get upgrade) and forced installation of the latest kernel (2.6.28-4).

I read 2.6.28's changelog, it has a HUGE amount of i915 and related fix, and several changes with drm integration (not a module anymore, plugged directly), I think it'd be very helpful as next 2.6.0 release :)

---

### Post by Demophobie on 2009-01-02
> **densou said:**
> I did it at ease (2.5.1), but FIRST you need to compile/install LIBDRM (Intrepid has 2.3.1 default, which not suits for newer releases .... shameful Canonical :( )

Here you are the backports for Intrepid (already .deb !),
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)




I read 2.6.28's changelog, it has a HUGE amount of i915 and related fix, and several changes with drm integration (not a module anymore, plugged directly), I think it'd be very helpful as next 2.6.0 release :)

Hi!

Yeah i know - i already compiled the driver 2.5.1. But this did not change the fps. I tried 2.5.99 now again and it worked. But i cant run it with EXA. XServer crashes with EXA..

I will try a jaunty image today, perhaps this works better.

---

### Post by igknighted on 2009-01-02
> **Demophobie said:**
> Hi!

Yeah i know - i already compiled the driver 2.5.1. But this did not change the fps. I tried 2.5.99 now again and it worked. But i cant run it with EXA. XServer crashes with EXA..

I will try a jaunty image today, perhaps this works better.

The intel driver uses UXA for acceleration now, at least until the changes are merged back to EXA.

Also, glx gears is not a benchmark.  Slow or fast speeds there do not necessarily imply better or worse graphics performance.

It should be noted that this card does have very poor framerates (as in for gaming), but does have great HD Video capability.  The two do not necessarily go hand in hand.

---

### Post by Demophobie on 2009-01-02
> **igknighted said:**
> The intel driver uses UXA for acceleration now, at least until the changes are merged back to EXA.

Also, glx gears is not a benchmark.  Slow or fast speeds there do not necessarily imply better or worse graphics performance.

It should be noted that this card does have very poor framerates (as in for gaming), but does have great HD Video capability.  The two do not necessarily go hand in hand.

Oh sorry. XAA does not work. EXA is veeeery slow. UXA crashes after some seconds. :confused: Driver: Intel 2.5.99

---

### Post by Demophobie on 2009-01-04
But why should this fps be right? The older intel cards give LOT more fps. Why building a card to downgrade the power?
The GMA 4500 is quite as good as the nvidia gforce 8400 - and this had a lot of fps more.

This must be a driver problem. 200FPS can't be right.
I still dont understand why this card accelerates, when i use cpupower.

---

### Post by Sctt.woods on 2009-01-04
Im a newbie when it comes to  linux, I've tried it before but gave up in frustration with gusty, i have a VGN FE 890 with a 945 integrated graphics  card, however when i try to use compiz instead of metacity the screen turns either white or displays a random image, i restart and im back on meta city, i want wobbly windows can some one please help

---

### Post by densou on 2009-01-04
> **Sctt.woods said:**
> Im a newbie when it comes to  linux, I've tried it before but gave up in frustration with gusty

:confused: so, do you use Gutsy ?

---

### Post by bjoern_S on 2009-01-17
hi guys :)

there is my fps

3668 frames in 5.0 seconds = 733.557 FPS
29492 frames in 5.0 seconds = 5892.073 FPS
12281 frames in 5.0 seconds = 2456.035 FPS
3345 frames in 5.0 seconds = 666.849 FPS
52646 frames in 5.0 seconds = 10528.856 FPS
57911 frames in 5.0 seconds = 11582.145 FPS
144530 frames in 5.0 seconds = 28905.807 FPS
113493 frames in 5.0 seconds = 22674.053 FPS
5330 frames in 5.0 seconds = 1065.811 FPS
10897 frames in 5.1 seconds = 2142.108 FPS
34714 frames in 5.0 seconds = 6942.102 FPS
100092 frames in 5.0 seconds = 19991.160 FPS
79555 frames in 5.0 seconds = 15910.971 FPS
47531 frames in 5.0 seconds = 9505.218 FPS
2687 frames in 5.0 seconds = 537.362 FPS
2631 frames in 5.0 seconds = 526.145 FPS
3423 frames in 5.0 seconds = 684.417 FPS
3318 frames in 5.0 seconds = 663.482 FPS

this is under Intrepid Ibex (8,10)
i just install intrepid and keept the default driver insted of upgrading..
and my my xorg is default by ubuntu..

sorry for my bad english ;)

---

### Post by Mikey_S on 2009-01-19
Hey there folks,
Recently installed intrepid, I have an Acer Aspire 2930 with GMA 4500MHD.
Seems like everything works smoothly, VLC, compiz (cube effects, wobbly windows etc`), even glxgears gives me a pretty decent performance (about 750-800)...

But seems like a lot of different applications which require more decent amount of graphics performance won't work correctly...

This include numerous 2d, 3d games, but it is most noticeable when trying to use Google Earth... when running Google Earth, I get random pixels with bizarre colours, it's unusable... I get the same effect on a few games I downloaded from getdeb.net...

Any idea what causing this, and are you experiencing the same effects?

Thanks,

Mikey

---

### Post by entner on 2009-01-20
> **Mikey_S said:**
> 
This include numerous 2d, 3d games, but it is most noticeable when trying to use Google Earth... when running Google Earth, I get random pixels with bizarre colours, it's unusable... I get the same effect on a few games I downloaded from getdeb.net...

Any idea what causing this, and are you experiencing the same effects?


For me turning off the desktop effects (Compiz) helped a lot, especially for Google Earth.

Burt

---

### Post by Mikey_S on 2009-01-20
I will try it, but is this being caused because of the poor performance of the chip or because something like a driver or so?

---

### Post by entner on 2009-01-20
> **Mikey_S said:**
> I will try it, but is this being caused because of the poor performance of the chip or because something like a driver or so?

AFAIK this is all driver and/or kernel related. The Intel driver is under heavy reconstruction as far as I heard.

For me, I cannot even watch Youtube videos in full screen, not even at low quality. The CPU is heavily loaded and the video is not smoothly running.

---

### Post by densou on 2009-01-20
> **entner said:**
> The Intel driver is under heavy reconstruction as far as I heard.

it's not that simple :( err, I'm not a geek or similar, however I'd make a try to explain [I hope I'm writing the correct thing]:

DRI is the kernel module (merged into with .26 version if I remember well) who provides our Intel cards to work (kernel ttm<>dri<>intel dri compliant driver)
The DRI driver includes i915 (replaced old i810) and i965 (for X cards only). [note: 2d only]

.28 Kernel introduced a DIFFERENT approach method called GEM
([read more about]("http://www.pcworld.idg.com.au/article/272845/linux_2_6_28_five_best_features?fp=16&fpid=1")), afterwards TTM/DRI could become USELESS. (kernel gem<>intel gem drivers). [note: 2d only]

There are 3 rendering methods:
XAA - old 2d, most stable
EXA - better with Compiz/Metacity effects
UXA - the newer, very unstable (don't try it, random crashes)

Recent Intel 2.6.0 release added DRI2 support for UXA only [maybe shall I ask too much just focus on GEM ?]

MESA is the library for OpenGL rendering [3d], however Ubuntu includes an obsolete version since 7.10, not supporting OGL 2.0 for i965 cards (while OFFICIAL Mesa does, you can upgrade it from sources)

HDMI audio is still corrupt, .28 (not informed about .28.1) lacks an important fix in ALSA

In a few words, I meant: there is too fragmentation on this project, that's why I think Linux Intel users still encounter trouble.


P.S. [http://intellinuxgraphics.org/results/2009-01-15__0/result.htm](http://intellinuxgraphics.org/results/2009-01-15__0/result.htm)
G45 still performs bad nearly overall :(
Using NEW 2.6.0 driver ( .deb partially avaiable, libdrm 2.4.4 backport not ready ) / 2.6.28 kernel / mesa build dated 12nd January 2009 / -WIP- xserver 1.6.0

---

### Post by Murrquan on 2009-01-21
> **densou said:**
> In a few words, I meant: there is too fragmentation on this project, that's why I think Linux Intel users still encounter trouble.

So what's the fix, for those of us with these video chipsets? Is there anything we *can* do other than wait? And if we have to wait, is this something that they're definitely going to fix in 9.04?

---

### Post by nightfrost on 2009-01-21
> **Murrquan said:**
> So what's the fix, for those of us with these video chipsets? Is there anything we *can* do other than wait? And if we have to wait, is this something that they're definitely going to fix in 9.04?

The thing with Intel is that they've actually done work (and are still doing work) that benefits the whole xorg stack. Their accomplishments and commitments are really in harmony with at least my interpretation of a how open source should be ideally. Instead of simply accepting what's further down in the stack and build what they can on top of that, they've been busy improving everything that the actual intel drivers rely on. Without Intel (and Redhat, if I'm not mistaken), the state of X would be much much sadder than it is now.

When it comes to the immediate future, I'm currently running mesa 7.3-rc3 + libdrm 2.4.4 + kernel 2.6.28.1 + xserver 1.5.99.901 + intel driver 2.6.0. As you see some of this is unreleased stuff, which means I'm having certain annoying issues, but that aside my desktop behaves in ways only nvidia driven desktops could behave previously. It's all very impressive. Hopefully this stack will be what we'll have in Jaunty, which would be the beginning of the future, in my opinion.

I wish there was an "intel backport PPA" with backported stable releases for intel users. Perhaps someone is interested in starting up something like that? (There is, of course, the xorg-edgers PPA with bleeding edge packages, but I'm thinking of something much more stable).

---

### Post by densou on 2009-01-21
> **nightfrost said:**
> There is, of course, the xorg-edgers PPA with bleeding edge packages, but I'm thinking of something much more stable

:confused:
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive) [very stable on my desktop with Intrepid]
anyway, I hope next releases will not require unstable stuff as dependancies anymore. And I wonder if Jaunty could say: "Yes, I can" :p

---

### Post by jim1964 on 2009-01-21
> **densou said:**
> :confused:
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive) [very stable on my desktop with Intrepid]
anyway, I hope next releases will not require unstable stuff as dependancies anymore. And I wonder if Jaunty could say: "Yes, I can" :p

Will this work for 64 bit intrepid? Thx.

---

### Post by densou on 2009-01-21
yeah lad, amd64 builds are avaiable.... Simply add
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```
to your repositories list ( use Synaptic GUI or edit /etc/apt/sources.list ) :popcorn:

---

### Post by rasmus91 on 2009-01-22
> yeah lad, amd64 builds are avaiable.... Simply add
```

deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main

```




Is this how i can update my intel drivers?? i havent found out how to do that yet, and that anoys me greatly!

---

### Post by nightfrost on 2009-01-22
> **densou said:**
> :confused:
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive) [very stable on my desktop with Intrepid]
anyway, I hope next releases will not require unstable stuff as dependancies anymore. And I wonder if Jaunty could say: "Yes, I can" :p

Nice. I completely forgot about this repo.
Although, I'd like to see a repo tracking this: [http://intellinuxgraphics.org/2008Q4.html](http://intellinuxgraphics.org/2008Q4.html) :-)

---

### Post by Olnex on 2009-01-22
I have 4500 card, I used to use Ubuntu which gives me bad video performance - supertux is very slow. glxgears gives me only 200, scale cpu to performance gives me 300.
Now I'm using Opensuse 11.1 with xorg.conf at the end, I got 600+ with ondemand and 800+ with performance, not sure what tweaks it does.
I also tried Archlinux which is supposed to have latest driver, but it is between Ubuntu and Opensuse.

```
# /.../
# SaX generated X11 config file
# Created on: 2009-01-22T13:01:27+1100.
#
# Version: 8.1
# Contact: Marcus Schaefer <sax@suse.de>, 2005
# Contact: SaX-User list <https://lists.berlios.de/mailman/listinfo/sax-users>
#
# Automatically generated by [ISaX] (8.1)
# PLEASE DO NOT EDIT THIS FILE!
#

Section "Files"
  FontPath     "/usr/share/fonts/misc:unscaled"
  FontPath     "/usr/share/fonts/local"
  FontPath     "/usr/share/fonts/75dpi:unscaled"
  FontPath     "/usr/share/fonts/100dpi:unscaled"
  FontPath     "/usr/share/fonts/Type1"
  FontPath     "/usr/share/fonts/URW"
  FontPath     "/usr/share/fonts/Speedo"
  FontPath     "/usr/share/fonts/PEX"
  FontPath     "/usr/share/fonts/cyrillic"
  FontPath     "/usr/share/fonts/latin2/misc:unscaled"
  FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/Type1"
  FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/share/fonts/baekmuk:unscaled"
  FontPath     "/usr/share/fonts/japanese:unscaled"
  FontPath     "/usr/share/fonts/kwintv"
  FontPath     "/usr/share/fonts/truetype"
  FontPath     "/usr/share/fonts/uni:unscaled"
  FontPath     "/usr/share/fonts/CID"
  FontPath     "/usr/share/fonts/ucs/misc:unscaled"
  FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/misc:unscaled"
  FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/Type1"
  FontPath     "/usr/share/fonts/misc/sgi:unscaled"
  FontPath     "/usr/share/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/input/mice"
EndSection

Section "ServerFlags"
  Option       "AIGLX" "on"
  Option       "AllowMouseOpenFail" "on"
  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "dri"
  Load         "dbe"
  Load         "freetype"
  Load         "extmod"
  Load         "glx"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "Microsoft Notebook Optical Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  DisplaySize  286 179
  HorizSync    30-52
  Identifier   "Monitor[0]"
  ModelName    "1280X800@60HZ"
  Option       "DPMS"
  Option       "PreferredMode" "1280x800"
  VendorName   "--> LCD"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1280x800" 83.46 1280 1344 1480 1680 800 801 804 828
  Modeline 	"1280x800" 69.75 1280 1328 1360 1440 800 803 809 823 +HSync -Vsync
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "Mobile Intel GM45 Express Chipset"
  Driver       "intel"
  Identifier   "Device[0]"
  Option       "monitor-LVDS" "Monitor[0]"
  VendorName   "Intel"
  Option       "AccelMethod" "xaa" # with/without this line does not affect the result!!!
EndSection



Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
  Option       "Composite" "on"
EndSection

```

---

### Post by entner on 2009-01-22
> **Olnex said:**
> I have 4500 card, I used to use Ubuntu which gives me bad video performance - supertux is very slow. glxgears gives me only 200, scale cpu to performance gives me 300.
Now I'm using Opensuse 11.1 with xorg.conf at the end, I got 600+ with ondemand and 800+ with performance, not sure what tweaks it does.
I also tried Archlinux which is supposed to have latest driver, but it is between Ubuntu and Opensuse.


With Fedora 10 I even get 1300 FPS in glxgears as compared to 300 with Ubuntu.

But what I am more concerned about is video. I cannot watch a Youtube video in fullscreen because it is not fluent, even at low video resolution. And the CPU is fully loaded while watching. What experience do you have here with Opensuse?

Burt

---

### Post by jfr1tz on 2009-01-22
> **entner said:**
> With Fedora 10 I even get 1300 FPS in glxgears as compared to 300 with Ubuntu.

But what I am more concerned about is video. I cannot watch a Youtube video in fullscreen because it is not fluent, even at low video resolution. And the CPU is fully loaded while watching. What experience do you have here with Opensuse?

Burt

The poor flash performance has little to do with the intel driver, are you running 64 bit ?

---

### Post by entner on 2009-01-22
> **jfr1tz said:**
> The poor flash performance has little to do with the intel driver, are you running 64 bit ubuntu?

No, I am running 32 bit. But I have the same problem with videos in Totem/VLC. So I think it is a driver problem.

Burt

---

### Post by jfr1tz on 2009-01-22
> **entner said:**
> No, I am running 32 bit. But I have the same problem with videos in Totem/VLC. So I think it is a driver problem.

Burt

well with a 100% loaded cpu it's not odd that you get poor flash performance, i had similar problems, replacing a flash version fixed the cpu load and make flash more smooth albeit still a bit choppy sometimes, but this is on 64bit. Do you get poor video playback period or just with certain types of video files?

---

### Post by entner on 2009-01-22
> **jfr1tz said:**
> well with a 100% loaded cpu it's not odd that you get poor flash performance, i had similar problems, replacing a flash version fixed the cpu load and make flash more smooth albeit still a bit choppy sometimes, but this is on 64bit. Do you get poor video playback period or just with certain types of video files?

Actually I did not look into it more carefully. Definitely all Flash videos are problematic. Also all videos I tried to watch full-screen. Every second or less the video gets stuck for a short while. In Windows I have no issues. Maybe I should try with Fedora 10, where I get the good glxgears result.

I was always sure that it is the Intel driver's fault. Maybe I should try some other Flash versions.

---

### Post by Olnex on 2009-01-22
> **entner said:**
> With Fedora 10 I even get 1300 FPS in glxgears as compared to 300 with Ubuntu.

But what I am more concerned about is video. I cannot watch a Youtube video in fullscreen because it is not fluent, even at low video resolution. And the CPU is fully loaded while watching. What experience do you have here with Opensuse?

Burt

Youtube and videos are fine in both opensuse 11.1 and archlinux, I haven't tried supertux under Opensuse, but it is playable(smooth) under Arch.

---

### Post by entner on 2009-01-22
> **Olnex said:**
> Youtube and videos are fine in both opensuse 11.1 and archlinux, I haven't tried supertux under Opensuse, but it is playable(smooth) under Arch.

I just tried Fedora 10 Live CD. I installed the newest Flash player from flash.com. Still the same problem with Youtube. In fullscreen the video gets stuck each second for about half a second :-(

---

### Post by densou on 2009-01-23
Flash 10 final runs very smooth on my Intrepid+Firefox, I can state it performs worse on my laptop (Vista HP) and on my gf's desktop (XP64)

> **entner said:**
> With Fedora 10 I even get 1300 FPS in glxgears as compared to 300 with Ubuntu.

well, please note everyone that Fedora 10 uses a Mesa 7.3-devel build (latest stable: 7.2) while Suse & Debian/Ubuntu are still stuck with 7.2 and outdated DRI with i915 module (not very correct, but let me say that Mesa+DRI are the DirectX counterparts in Linux.)

:popcorn:

edit: Mesa 7.3 stable is out ! Changelog on: [http://news.swzone.it/swznews-23493.php](http://news.swzone.it/swznews-23493.php)
GEM should be avaiable with Kernel 2.6.28 only while DRI2 with UXA (very unstable).
Waiting for a .deb :)

---

### Post by entner on 2009-01-24
I just installed Jaunty on a spare partition. Intel driver 2.6.1 from the default repositories, no extra repositories enabled.

glxgears close to 60 FPS constant, which is obviously screen limited, so perfektly okay. Also in full screen I get this rate.

Unreal Tounament (the original). Perfektly fine close to 60FPS (also display refresh rate limited I guess) at highest settings, as opposed to merely 20 FPS in Intrepid sometimes going down below 10 with Intel 2.4.1.
I get no sound in UT though, no idea why.

Burt

---

### Post by rasmus91 on 2009-02-17
> But I already got just belov 800 fps with the current driver available in the repositorys - why don't you?

I also want to clarify that I had just below 600 FPS in Ubuntu 8.10 at first, then tried Mandriva 2009.0 where I got 200 fps more - that's 800 - and I failed to make that clear in my previous post. After using the xorg.conf from Mandriva (though somewhat cleaned up) I get the same fps in Ubuntu.

Are you folks shure you actually use the correct driver? The correct package - which is based on the 2.5.1-driver is xserver-xorg-video-intel...

Also try my xorg.conf as posted in this thread.

Sweet results.


I saw that some of you guys figured out how to add some sources making updating the driver very easy.

Can you please give me the link or what ever its called... I need it for 32 bit.

---

### Post by densou on 2009-02-21
> **rasmus91 said:**
> I saw that some of you guys figured out how to add some sources making updating the driver very easy.

here you are
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)

---

### Post by rasmus91 on 2009-02-25
Omg... Can't download the key :( Won't connect to the side...

---

### Post by farmfield on 2009-02-25
> **rasmus91 said:**
> Omg... Can't download the key :( Won't connect to the side...

Run in terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x5eb2edfe1fcb21db
```

And the run [alt]+[f2] and paste:

```
gksudo gedit /etc/apt/sources.list
```

The sources list will open in gedit.

In the end of the dokument you now paste:

```

deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```

Close and save the document.

Now go into Synaptic and reload sources. Use the 'mark all uppgrades'-button and then 'apply'...

When it's all done it's easiest to reboot to restart the x-server and load the new drivers.

This last step, rebooting, I haven't done yet, hehe, so here it goes 5... 4... 3... 2... 1... (bye4now)):P

---

### Post by rasmus91 on 2009-02-25
Okay, i'll reboot now. (i found out the router was blocking the page...)

---

### Post by rasmus91 on 2009-02-25
```
rasmus@rasmus-Dell-E6400:~$ glxgears
1194 frames in 5.0 seconds = 238.632 FPS
1202 frames in 5.0 seconds = 240.300 FPS
1127 frames in 5.0 seconds = 225.224 FPS
1171 frames in 5.0 seconds = 234.115 FPS
1213 frames in 5.0 seconds = 242.566 FPS
1126 frames in 5.0 seconds = 225.081 FPS
1215 frames in 5.0 seconds = 242.884 FPS

```


*sigh*

And with the visual effects on i get: 
```

rasmus@rasmus-Dell-E6400:~$ glxgears
2517 frames in 5.0 seconds = 502.611 FPS
2540 frames in 5.0 seconds = 504.007 FPS
2540 frames in 5.0 seconds = 504.681 FPS
2500 frames in 5.0 seconds = 496.745 FPS
2520 frames in 5.0 seconds = 503.648 FPS


```

I can't seem to understand this... :s

---

### Post by farmfield on 2009-02-25
I dropped from 900fps (w/ my old driver) to 250 (w/ the backported ones)... Also, Google Earth now say's I don't have OpenGL acceleration... How suckish...

So any ideas how to 'downgrade' to my previous driver, hehe?

---

### Post by bofphile on 2009-02-25
Does anyone know when the tearing in videos will be fixed ? Whether Compiz is active or not, I get tearing in my videos regardless of the player used(vlc, mplayer, totem...).

---

### Post by farmfield on 2009-02-25
> **bofphile said:**
> Does anyone know when the tearing in videos will be fixed ? Whether Compiz is active or not, I get tearing in my videos regardless of the player used(vlc, mplayer, totem...).
I don't have that problem at all, neither with the old- nor the new driver. The only problem I've had - accept poor 3D-acceleration - is with Blender and/or Google Earth when Compiz is active...

I still wonder why I have the least problems... Maybe HP did something 'right' with the BIOS settings (which I can't access though) or the general design of the motherboard, but I never had tearing and I also had acceptable performance using the 2.4.1 driver giving me about 900fps in glxgears...

I'm pretty sure the Mandriva LiveCD activates the Intel-drivers from scratch as well as an option to run compiz, I'll download the latest beta, boot off it and check my performance there - any of you could do the same and then compare performance... I'll download and boot of the Gnome/i586 LiveCD.

I'll post the numbers later this evening - it's 5.48pm locally when I post this... =)

Edit: Mandiva 2009.1 beta downloads here: [http://wiki.mandriva.com/en/2009.1_Beta](http://wiki.mandriva.com/en/2009.1_Beta)

---

### Post by bofphile on 2009-02-25
Strange you don't have any tearing with videos.  :confused:

I have a Thinkpad T500 and after a bit of searching I found out this problem was known by the developer and did not have a fix right now.

_Taken from Thinkwiki_: [http://www.thinkwiki.org/wiki/Intel_GMA_X4500HD]("http://www.thinkwiki.org/wiki/Intel_GMA_X4500HD")
"Now the chip only has 3D, which means a lot of stuff must be rewritten. The 2D Video Overlay Adaptor for Xvideo isn't available anymore. (Xvideo or xv is the xorg way of displaying vidoes and do fast scaling (to fullscreen output and stuff)) However the textured video adaptor for Xv is still available BUT it's broken. Since nobody cared about this before (because there was the better Video Overlay available) **the textured video causes a effect called Tearing (or horizontal flicker) Basically there are two frames visible at the same time. You can see this effect in every video with fast movement. No matter what resulotion. Google for Tearing if you want to learn more about this. The way to fix this is first to enable DRI2 and then patch the XV Textured Video Adapter to make use of the new vsync handeling. Some basic support for DRI2 was enabled in 2.6.0 however the patch for textured video is still missing. So: You can't watch movies with the X4500HD right now. And since the code to fix this is not yet written there is nothing you can do about it.** OpenGL is awefull slow as well (Supertux has 14FPS with OpenGL and 70FPS with software rendering) AIGLX doesnt work as well. It is all somehow connected to the DRI2 stuff..."

See also this bug report for more information: [http://bugs.freedesktop.org/show_bug.cgi?id=19635]("http://bugs.freedesktop.org/show_bug.cgi?id=19635")

---

### Post by bofphile on 2009-03-06
Well seems like the tearing problem has been solved: [http://bugs.freedesktop.org/show_bug.cgi?id=19635]("http://bugs.freedesktop.org/show_bug.cgi?id=19635")

Taken from the link "[B]I finally get to report some good news...great news in fact.  I finally have
tear free XV fullscreen video on my G45.  No Compiz needed, w00t!  Thanks to
all the devs/community for getting it there...[/B]"

Now is there anyway to get this fix on Intrepid ? :P

---

### Post by rasmus91 on 2009-03-11
Okay, i think my graphics got worse after updating. Is there a way to install a driver from another linux distribution?.. Im thinking Mandriva?

---

### Post by rasmus91 on 2009-03-14
OKay, just upgraded to 9.04 Aplha. please see that this solves the performance problem with the GMA 4500 MHD Graphic card. Before i got 250 fps with glxgears on performance, now i get 1130+

 everyone who has performance problems with this card should really be looking forward to the 9.04!!!

---

### Post by nightfrost on 2009-03-14
> **rasmus91 said:**
> OKay, just upgraded to 9.04 Aplha. please see that this solves the performance problem with the GMA 4500 MHD Graphic card. Before i got 250 fps with glxgears on performance, now i get 1130+

 everyone who has performance problems with this card should really be looking forward to the 9.04!!!

I don't know.
I've been running Jaunty for some time now, and there are serious issues with the intel support so far (might get better though). Particularly, it's compiz that's really choppy. Here's for hoping.

---

### Post by rasmus91 on 2009-03-14
> I don't know.
I've been running Jaunty for some time now, and there are serious issues with the intel support so far (might get better though). Particularly, it's compiz that's really choppy. Here's for hoping.

Really? like what?

Hey, anyone has an idea why Guild Wars crashes when i start it? Tried different ways of installing, but nothing seems to do the trick.

---

### Post by nightfrost on 2009-03-14
> **rasmus91 said:**
> Really? like what?

like bad performance from compiz and composited kwin.

---

### Post by Olnex on 2009-03-14
I am using Ubuntu 8.10 and glxgears gives me 700+ (usually 740+) FPS.
Here is my xorg.conf, it is copied from OpenSuse:

```

# /.../
# SaX generated X11 config file
# Created on: 2009-02-26T17:50:51+1100.
#
# Version: 8.1
# Contact: Marcus Schaefer <sax@suse.de>, 2005
# Contact: SaX-User list <https://lists.berlios.de/mailman/listinfo/sax-users>
#
# Automatically generated by [ISaX] (8.1)
# PLEASE DO NOT EDIT THIS FILE!
#

Section "Files"
  FontPath     "/usr/share/fonts/misc:unscaled"
  FontPath     "/usr/share/fonts/local"
  FontPath     "/usr/share/fonts/75dpi:unscaled"
  FontPath     "/usr/share/fonts/100dpi:unscaled"
  FontPath     "/usr/share/fonts/Type1"
  FontPath     "/usr/share/fonts/URW"
  FontPath     "/usr/share/fonts/Speedo"
  FontPath     "/usr/share/fonts/PEX"
  FontPath     "/usr/share/fonts/cyrillic"
  FontPath     "/usr/share/fonts/latin2/misc:unscaled"
  FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/Type1"
  FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/share/fonts/baekmuk:unscaled"
  FontPath     "/usr/share/fonts/japanese:unscaled"
  FontPath     "/usr/share/fonts/kwintv"
  FontPath     "/usr/share/fonts/truetype"
  FontPath     "/usr/share/fonts/uni:unscaled"
  FontPath     "/usr/share/fonts/CID"
  FontPath     "/usr/share/fonts/ucs/misc:unscaled"
  FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/misc:unscaled"
  FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/Type1"
  FontPath     "/usr/share/fonts/misc/sgi:unscaled"
  FontPath     "/usr/share/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/input/mice"
EndSection

Section "ServerFlags"
  Option       "AIGLX" "on"
  Option       "AllowMouseOpenFail" "on"
#  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "dri"
  Load         "dbe"
  Load         "freetype"
  Load         "extmod"
  Load         "glx"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[1]"
#  Option       "AccelFactor" "0.1"
#  Option       "BottomEdge" "650"
  Option       "Buttons" "5"
#  Option       "CircScrollDelta" "0.1"
#  Option       "CircScrollTrigger" "2"
#  Option       "CircularScrolling" "1"
  Option       "Device" "/dev/input/mice"
#  Option       "EdgeMotionMaxSpeed" "15"
#  Option       "EdgeMotionMinSpeed" "15"
  Option       "Emulate3Buttons" "on"
  Option       "EmulateMidButtonTime" "75"
#  Option       "FingerHigh" "17"
#  Option       "FingerLow" "14"
#  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
#  Option       "LeftEdge" "120"
#  Option       "MaxSpeed" "3"
#  Option       "MaxTapMove" "110"
#  Option       "MaxTapTime" "180"
#  Option       "MinSpeed" "0.2"
  Option       "Name" "ALPS;Touchpad"
  Option       "Protocol" "auto-dev"
#  Option       "RightEdge" "830"
  Option       "SHMConfig" "on"
#  Option       "TopEdge" "120"
#  Option       "UpDownScrolling" "1"
  Option       "Vendor" "Sysp"
#  Option       "VertScrollDelta" "20"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
#  Option       "AccelFactor" "0.1"
#  Option       "BottomEdge" "650"
  Option       "Buttons" "7"
#  Option       "CircScrollDelta" "0.1"
#  Option       "CircScrollTrigger" "2"
#  Option       "CircularScrolling" "1"
  Option       "Device" "/dev/input/mice"
#  Option       "EdgeMotionMaxSpeed" "15"
#  Option       "EdgeMotionMinSpeed" "15"
  Option       "Emulate3Buttons" "on"
  Option       "EmulateMidButtonTime" "75"
#  Option       "FingerHigh" "17"
#  Option       "FingerLow" "14"
#  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
#  Option       "LeftEdge" "120"
#  Option       "MaxSpeed" "3"
#  Option       "MaxTapMove" "110"
#  Option       "MaxTapTime" "180"
#  Option       "MinSpeed" "0.2"
  Option       "Name" "ALPS;Touchpad"
  Option       "Protocol" "auto-dev"
#  Option       "RightEdge" "830"
  Option       "SHMConfig" "on"
#  Option       "TopEdge" "120"
#  Option       "UpDownScrolling" "1"
  Option       "Vendor" "Sysp"
#  Option       "VertScrollDelta" "20"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[5]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImPS/2 Generic Wheel Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  DisplaySize  331 207
  HorizSync    30-62
  Identifier   "Monitor[0]"
  ModelName    "SAMSUNG LCD MONITOR"
  Option       "DPMS"
  Option       "PreferredMode" "1280x800"
  VendorName   "SEC"
  VertRefresh  43-60
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1280x800" 83.46 1280 1344 1480 1680 800 801 804 828
  Modeline 	"1280x800" 69.75 1280 1328 1360 1440 800 803 809 823 +HSync -Vsync
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "965 GM"
  Driver       "intel"
  Identifier   "Device[0]"
  Option       "monitor-LVDS" "Monitor[0]"
  Option       "SaXDualHSync" "31-48"
  Option       "SaXDualHead" ""
  Option       "SaXDualMode" "Clone"
  Option       "SaXDualMonitorModel" "1024X768@60HZ"
  Option       "SaXDualMonitorVendor" "--> VESA"
  Option       "SaXDualOrientation" "LeftOf"
  Option       "SaXDualResolution" "1024x768"
  Option       "SaXDualVSync" "50-60"
  Option       "SaXExternal" "Identifier&EXT+VertRefresh&50-60+HorizSync&31-48+PreferredMode&1024x768+VendorName&--> VESA+ModelName&1024X768@60HZ"
  VendorName   "Intel"
EndSection


Section "Monitor"
  HorizSync    31-48
  Identifier   "EXT"
  ModelName    "1024X768@60HZ"
  Option       "PreferredMode" "1024x768"
  VendorName   "--> VESA"
  VertRefresh  50-60
EndSection


Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[5]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
  Option       "Composite" "on"
EndSection


```

---

### Post by rasmus91 on 2009-03-15
Hi again, Can i ask one of you other guys with this chip to try and install GW and see if you can start it and go to the login screen?

I would really like to know if any one else is capable of that, and then tell me how. 

I'm really about to give up on running Guild Wars. Its easy installing, the game installer can be downloaded here. And you Won't need an account before you get to the login screen.

heres the link:[http://www.guildwars.com/downloads/gwsetup.zip]("http://www.guildwars.com/downloads/gwsetup.zip")  Please try someone... This is REALLY driving me nuts.

Just try installing this with wine. then cd to "Guild Wars" and use "wine Gw.exe" and post you output, tell me if the game launches properly!

My output is:

```
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  481
  Current serial number in output stream:  481

```

---

### Post by conorsulli on 2009-03-16
Well when I run compiz wobbly windows with with glxgears on I get foggy trails off the glxgears window when I drag it round the screen. This is a sure indication that things aren't being direct rendered truly by the graphics card (Am I not right?!?!) . For those of you that get the 1200+ frames  I would love to know if you experience this problem... you shouldn't I think,,, Im definatly subscribing to this post. i get around 530-570 glxgears with compiz running. On a dell studio 17".

---

### Post by rasmus91 on 2009-03-16
> Well when I run compiz wobbly windows with with glxgears on I get foggy trails off the glxgears window when I drag it round the screen. This is a sure indication that things aren't being direct rendered truly by the graphics card (Am I not right?!?!) . For those of you that get the 1200+ frames I would love to know if you experience this problem... you shouldn't I think,,, Im definatly subscribing to this post. i get around 530-570 glxgears with compiz running. On a dell studio 17".

Which version do you run?

I get 1100+ when running setting cpu to performance.

This is what happens when i have wobbly windows and drag the glxgears window (see attached screenshot)

(still if anyone would like to help me with the Guild wars GLXBadDrawable problem it would be greatly appreciatet)

---

### Post by NT4usB on 2009-03-16
> **rasmus91 said:**
> ...
(still if anyone would like to help me with the Guild wars GLXBadDrawable problem it would be greatly appreciatet)

I'd love to but I've had no luck getting the intel graphics going on a new GA-EG41M-S2H g41 chipset board.
VGA out works (poorly) and DVI out doesn't find the display...

---

### Post by rasmus91 on 2009-03-17
> I'd love to but I've had no luck getting the intel graphics going on a new GA-EG41M-S2H g41 chipset board.
VGA out works (poorly) and DVI out doesn't find the display... Thanks For the attention though ;) What system are you running?

Anyone else who have the time and are willing to help me out with the GW problem?

---

### Post by NT4usB on 2009-03-17
> **rasmus91 said:**
> Thanks For the attention though ;) What system are you running?

[GA-EG41M-S2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2945") board. E5200 processor. 4GB DDR2.
Hardy
Intrepid
Fedora 10
Debian stable, testing, unstable.
[IMG]http://www.senortuna.com/main/images/smilies/5191beatdeadhorse.gif[/IMG]

Just read where FC11 might have a better handle on the Intel graphics so I'm off to try that.[IMG]http://www.senortuna.com/main/images/smilies/banghead.gif[/IMG]

---

### Post by rasmus91 on 2009-03-18
> Hardy
Intrepid
Fedora 10
Debian stable, testing, unstable.

All of those at the same time???

Well, I upgraded to 9.04, the graphic card is okay here... Would really like to run Guild Wars though.

---

### Post by NT4usB on 2009-03-18
> **rasmus91 said:**
> All of those at the same time???...

oh, and Jaunty 9.04...
Not *all* at the same time. I have two drives in this box, for when it replaces my master frontend/backend. iirc, Jaunty is on one now, and FC10 on the other.
Been trying all the distros, looking for one that like the G41.

---

### Post by conorsulli on 2009-03-18
Rasmus, that weird trails of glxgears is the same as what I get. Only with compiz running though. I reckon a lot of it has to do with cpu emulation hopefully the issue will be fixed after the new intel drivers with dri come out.

---

### Post by rasmus91 on 2009-03-18
> Rasmus, that weird trails of glxgears is the same as what I get. Only with compiz running though. I reckon a lot of it has to do with cpu emulation hopefully the issue will be fixed after the new intel drivers with dri come out.

Yeah, sorry i guess i forgot to mention that mine was with compiz on to... I have no idea why... (well, something with the drivers obviously, but i can run 3D linux games now, i couldn't do that in 8.04 and 8.10)

> Just read where FC11 might have a better handle on the Intel graphics so I'm off to try that.

What is FC11?

I've heard Mandriva should have good intel graphics, but I'm not so sure.

---

### Post by conorsulli on 2009-03-18
FC11 is Fedora (fedora core 11) its generally known to be the bleeding edge distro where features are developed for redhat to be stabilized . its generally a good os but doesn't have the same finish as ubuntu. I find it functions better though for driver support etc, and new features such as modesetting in the kernel and plymouth etc are incorporated quicker.

---

### Post by rasmus91 on 2009-03-18
okay


I started a thread about my problems with Getting Guild wars running (see [http://ubuntuforums.org/showthread.php?t=1099774&highlight=direct+rendering%3A+set)]("http://ubuntuforums.org/showthread.php?t=1099774&highlight=direct+rendering%3A+set)")

Please note this: ```
glxinfo | grep rendering 
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

I was told that this means my driver is not properly installed. Does anyone now how i solve this?

---

### Post by Olnex on 2009-03-19
I tried Mandriva 2009.0, the KDM is not crap as Opensuse 11.1, and glxgears give me 1200+ fps

> **rasmus91 said:**
> 
I've heard Mandriva should have good intel graphics, but I'm not so sure.

---

### Post by rasmus91 on 2009-03-19
Can i see output of: ```
glxinfo | grep rendering
```

please. I would really like to know if you have Direct rendering...

---

### Post by Olnex on 2009-03-20
> **rasmus91 said:**
> Can i see output of: ```
glxinfo | grep rendering
```

please. I would really like to know if you have Direct rendering...

Sorry, now I am using Ubuntu 8.10, but I copied xorg.conf from Mandriva, the command shows Yes.

Below is several xorg.conf from different distros:

**Ubuntu 8.10 Default**

```

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

```

You can see everything is default.

**OpenSuse 11.1 with MODIFICATIONS**

```

# /.../
# SaX generated X11 config file
# Created on: 2008-12-31T09:51:36+1100.
#
# Version: 8.1
# Contact: Marcus Schaefer <sax@suse.de>, 2005
# Contact: SaX-User list <https://lists.berlios.de/mailman/listinfo/sax-users>
#
# Automatically generated by [ISaX] (8.1)
# PLEASE DO NOT EDIT THIS FILE!
#

Section "Files"
#  FontPath     "/usr/share/fonts/misc:unscaled"
#  FontPath     "/usr/share/fonts/local"
#  FontPath     "/usr/share/fonts/75dpi:unscaled"
#  FontPath     "/usr/share/fonts/100dpi:unscaled"
#  FontPath     "/usr/share/fonts/Type1"
#  FontPath     "/usr/share/fonts/URW"
#  FontPath     "/usr/share/fonts/Speedo"
#  FontPath     "/usr/share/fonts/PEX"
#  FontPath     "/usr/share/fonts/cyrillic"
#  FontPath     "/usr/share/fonts/latin2/misc:unscaled"
#  FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
#  FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
#  FontPath     "/usr/share/fonts/latin2/Type1"
#  FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
#  FontPath     "/usr/share/fonts/baekmuk:unscaled"
#  FontPath     "/usr/share/fonts/japanese:unscaled"
#  FontPath     "/usr/share/fonts/kwintv"
#  FontPath     "/usr/share/fonts/truetype"
#  FontPath     "/usr/share/fonts/uni:unscaled"
#  FontPath     "/usr/share/fonts/CID"
#  FontPath     "/usr/share/fonts/ucs/misc:unscaled"
#  FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
#  FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
#  FontPath     "/usr/share/fonts/hellas/misc:unscaled"
#  FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
#  FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
#  FontPath     "/usr/share/fonts/hellas/Type1"
#  FontPath     "/usr/share/fonts/misc/sgi:unscaled"
#  FontPath     "/usr/share/fonts/xtest"
#  FontPath     "/opt/kde3/share/fonts"
#  InputDevices "/dev/gpmdata"
  InputDevices "/dev/input/mice"
#  InputDevices "/dev/input/mouse2"
EndSection

Section "ServerFlags"
  Option       "AIGLX" "on"
  Option       "AllowMouseOpenFail" "on"
  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "dri"
  Load         "dbe"
  Load         "freetype"
  Load         "synaptics"
  Load         "extmod"
  Load         "glx"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "Microsoft Wheel Mouse Optical"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
  Option       "AlwaysCore" "true"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
#  Option	"Device" "/dev/input/mouse2"
#  Option       "Device" "/dev/psaux"
  Option       "FastTaps" "1"
  Option       "Emulate3Buttons" "on"
  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
  Option       "VertEdgeScroll" "true"
  Option       "TapButton1" "1"
  Option       "TapButton2" "2"
  Option       "TapButton3" "3"
EndSection


Section "Monitor"
  DisplaySize  286 179
  HorizSync    30-52
  Identifier   "Monitor[0]"
  ModelName    "1280X800@60HZ"
  Option       "DPMS"
  Option       "PreferredMode" "1280x800"
  VendorName   "--> LCD"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1280x800" 83.46 1280 1344 1480 1680 800 801 804 828
  Modeline 	"1280x800" 69.75 1280 1328 1360 1440 800 803 809 823 +HSync -Vsync
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x800" 
    Virtual    3840 1200
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "Mobile Intel GM45 Express Chipset"
  Driver       "intel"
  Identifier   "Device[0]"
  Option       "monitor-LVDS" "Monitor[0]"
  Option       "SaXDualHSync" "31-48"
  Option       "SaXDualHead" ""
  Option       "SaXDualMode" "Clone"
  Option       "SaXDualMonitorModel" "1024X768@60HZ"
  Option       "SaXDualMonitorVendor" "--> VESA"
  Option       "SaXDualOrientation" "LeftOf"
  Option       "SaXDualResolution" "1024x768"
  Option       "SaXDualVSync" "50-60"
  Option       "SaXExternal" "Identifier&EXT+VertRefresh&50-60+HorizSync&31-48+PreferredMode&1024x768+VendorName&--> VESA+ModelName&1024X768@60HZ"
  VendorName   "Intel"
EndSection


Section "Monitor"
  HorizSync    31-48
  Identifier   "EXT"
  ModelName    "1024X768@60HZ"
  Option       "PreferredMode" "1024x768"
  VendorName   "--> VESA"
  VertRefresh  50-60
EndSection


Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
#    Group      "video"
#    Mode       0660
EndSection

Section "Extensions"
  Option       "Composite" "on"
EndSection


```

I modified "DRI" section, commented everything so glxgears give me 700-800 fps, otherwise it gives me 400-500 fps.

**Mandriva**

This is the one I'm using now:

```
# File generated by XFdrake (rev 247269)

# **********************************************************************
# Refer to the xorg.conf man page for details about the format of
# this file.
# **********************************************************************

Section "ServerFlags"
    #DontZap # disable <Ctrl><Alt><BS> (server abort)
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
    #DontZoom # disable <Ctrl><Alt><KP_+>/<KP_-> (resolution switching)
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri" # direct rendering
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection

Section "InputDevice"
    Identifier "SynapticsMouse1"
    Driver "synaptics"
    Option "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1280x800"
    HorizSync 31.5-90
    VertRefresh 60
    
    # Monitor preferred modeline (59.9 Hz vsync, 49.3 kHz hsync, ratio 16/10, 113 dpi)
    ModeLine "1280x800" 71 1280 1328 1360 1440 800 803 809 823 -hsync -vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_120"  181.21  1280 1376 1520 1760  800 801 804 858  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_100"  147.89  1280 1376 1512 1744  800 801 804 848  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_85"  123.38  1280 1368 1504 1728  800 801 804 840  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_75"  107.21  1280 1360 1496 1712  800 801 804 835  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_60"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x800_50"  68.56  1280 1336 1472 1664  800 801 804 824  -HSync +Vsync
EndSection

Section "Device"
    Identifier "device1"
    VendorName "Intel Corporation"
    BoardName "Intel 810 and later"
    Driver "intel"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1280x800"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1280x800"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1280x800"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1280x800"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "SynapticsMouse1" "SendCoreEvents"
    Screen "screen1"
EndSection
```

Also, I remembered in Fedora 10 I got pretty good glxgears, I cannot remember what exactly it is, but it is nearly or above 1000, however, I did not see a xorg.conf file in /etc/X11 so I did not have a copy of it.

---

### Post by rasmus91 on 2009-03-21
> Sorry, now I am using Ubuntu 8.10, but I copied xorg.conf from Mandriva, the command shows Yes.

How the heck is this possible?

Can you please give me a short guide or something.... well, just tell me how to setup direct rendering?

Just tell me what to do... I don't know if its just something with the "xorg.conf"

But please tell me how i can get direct rendering, I would really like that!

---

### Post by jim1964 on 2009-03-23
I just installed Jaunty Alpha on my Dell 1545. I'm getting about 1200 fps with glxgears. And, Blender graphics response is much better (e.g., drawing the bounding box after hitting the "B" key). Looks promising. As a side note, the Blender site notes a bug in the Vista driver for the GM45 graphics and I have experienced it. So... the Linux drivers appear to have surpassed the Vista drivers. Jaunty also fixed my resume from sleep problem and screen dimming via the keyboard. I'm looking forward to the formal release of Jaunty. Yay for Linux! :P

---

### Post by rasmus91 on 2009-03-23
> I just installed Jaunty Alpha on my Dell 1545. I'm getting about 1200 fps with glxgears. And, Blender graphics response is much better (e.g., drawing the bounding box after hitting the "B" key). Looks promising. As a side note, the Blender site notes a bug in the Vista driver for the GM45 graphics and I have experienced it. So... the Linux drivers appear to have surpassed the Vista drivers. Jaunty also fixed my resume from sleep problem and screen dimming via the keyboard. I'm looking forward to the formal release of Jaunty. Yay for Linux! 
sweet

may i see your output of:
```
glxinfo | grep rendering 

```

---

### Post by jim1964 on 2009-03-23
> **rasmus91 said:**
> sweet

may i see your output of:
```
glxinfo | grep rendering 

```

direct rendering: Yes

Can you please explain what is good or bad about that? Thanks.

---

### Post by rasmus91 on 2009-03-24
> direct rendering: Yes

Can you please explain what is good or bad about that? Thanks.

Sure, much much better 3D graphics. You'll be able to play windows 3D games through wine.

Can you tell me if you have installed another driver than the default?

Okay i have direct rendering as well by now, got it by typing:

```
unset LIBGL_ALWAYS_INDIRECT
```

But still can't run guild wars, i get error:

```

X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  490
  Current serial number in output stream:  490

```

Man this is driving me nuts.

---

### Post by Hossie on 2009-03-29
This seems to be a kernel issue. Gentoo with .28 -> working. Ubuntu 8.10 -> not working. Jaunty -> working. With Jaunty you get a 2.6 Intel driver and a .28 kernel -> 3D is working, even with an empty xorg.conf. So just upgrade to Jaunty. ;)

---

### Post by rasmus91 on 2009-03-31
> This seems to be a kernel issue. Gentoo with .28 -> working. Ubuntu 8.10 -> not working. Jaunty -> working. With Jaunty you get a 2.6 Intel driver and a .28 kernel -> 3D is working, even with an empty xorg.conf. So just upgrade to Jaunty. 

Dude, i have Jaunty, If you read more of the thread you would know that i have told others that 3D works on Jaunty, The problem still is, i have no Direct rendering.

I can do:
```
unset LIBGL_ALWAYS_INDIRECT
```

Which will "activate" Direct Rendering, but it still doesn't work a 100%

---

### Post by densou on 2009-04-03
have you tried with latest Mesa 7.4 ? It should fix your issue... (available prior update from Jaunty repos)

Jaunty improved performance a lot, and Compiz runs decently (the 1st time since Feisty - GMA950) however not smooth as I tested on Fedora 11 Beta (out-of-the-box: Linux 2.6.29, Gnome 2.25.96 -why? lol-, Compiz 0.7.8, Mesa 7.4 + Xserver 1.6)

It's hard to make a good comparison between F11 and Jaunty due to their disequality (2.6.28, G 2.26.0, C 0.8.2, Mesa 7.3 + Xserver 1.6)


I wonder when editing xorg.conf on Jaunty I can't see any changes at all meanwhile I had to use a customized one with Hardy and Intrepid as well.... or performance barely sucked :mad:

---

### Post by Olnex on 2009-04-03
I tried 9.04 beta livecd with default xorg.conf, there is no improvement for glxgears, but maybe I should try my current xorg.conf later.

---

### Post by jim1964 on 2009-04-05
> **Olnex said:**
> I tried 9.04 beta livecd with default xorg.conf, there is no improvement for glxgears, but maybe I should try my current xorg.conf later.

I don't know if it's true or not... But maybe a full install would result in more up to date libraries or packages being installed. I get about 1200 FPS on my Dell 1545 with Jaunty alpha installed. Just a thought.

---

### Post by Olnex on 2009-04-05
I installed 9.04 beta, after install, glxgears gives me 800 fps, there are 200MB updates, I only upgraded xorg-server-video-intel and xorg-something-core and xorg packages, then restart, now it gives me 1100-1200 fps, later I upgraded everything, however, this time it gives me 700-800 fps.

---

### Post by Olnex on 2009-04-06
And it also have the problem in 8.10, when I boot to GDM or logout to GDM, the screen resolution is 1024x768 but my screen resolution is 1280x800, in 8.10, I can use ctrl+alt+del to restart X, but 9.04 disabled the key combination, fortunately I can set screen resolution from System->Preferences->Display(it used to not working in 8.10).

Also, I tried the xorg.conf file from Opensuse which I used in 8.10, it does not work any more.

---

### Post by starfly on 2009-04-06
Same Problem here, using Jaunty since 3 Month in the Beta Status...

My Notebook is a Toshiba Sattelite U400 15G.

The Fps randomly changed between 100 to now 655fps in these three month.

But my mainproblem is : Intel "works" on his driver, but they didnt get it managed that their neweset Graphic Board, which is mainly oversized, can play Ut2004 from year 2004!

In Windows it works perfectly, all effects on, on 1024 X 786 !

In ubuntu ive got to put all down to minimal, an than its getting in stuck until ive vanished the enemy and nothing more is moving ;)


Any ideas why the performance is quite still that bad ?! people and forums are still full of posts since 2007 that intel should improve the performance of these chips, that they are equal to windows...but since 2007 were left outside alone ! The game has the same performance as on the X3100 from my girlfriend, and sorry...my Board should be 3X faster than the 3100...but its realy the same performance problem...and iam very angry about it !

Over years they are "improving" dvd quality, but sorry, I WATCH DVD AND HD ON MY TV ! But my notebook should run quite fast, theres no advantage for me to watch hd videos without stuck, when i cant watch youtube without stucking and loading...and i cant play games from the last 10th years... they shoult improve THAT !

Thank you for listening to this speech ;-)

By the way, can i improve speed, by setting the acceleration mode to uxa ?!

---

### Post by rasmus91 on 2009-04-10
Which version of Ubuntu?

---

### Post by starfly on 2009-04-13
newest, jaunty all updates

---

### Post by rasmus91 on 2009-04-14
weird, mine works fine, but with no direct rendering. i've tried Kubuntu though, when using KDM i have direct rendering.

---

### Post by farmfield on 2009-04-14
I installed 64-bit Jaunty just the other day, installed the 2.6.29.1 kernel and though I got 1100+ fps in GLXGEARS(*) I couldn't run Google Earth... So I activated UXA... WoW!

UXA works lika a charm for me. I get a little bit less fps, like 8-900 in GLXGEARS, but the only thing that doesn't work is the OpenGL effects in Cairo-Dock 2 rc1 - but that might as well be the release candidate of Cairo-Dock as the driver - and no other bugs for me at all...

It will be interesting to see if I can get kernel 2.6.30.x working though, where the Intel drivers reside in the kernel... Now I can boot all the way until GNOME where it just stops - no signs why either, no into in the bootlog or anything... We'll se when rc2 gets out, maybe it'll work then... =)


*[SIZE="2"](*) doesn't matter how good a benchmarker it is, it gives me a comparison[/SIZE]*

---

### Post by whitethunder on 2009-04-14
Hi All,

I have recently installed Ubuntu 9.04 on a desktop which uses the intel graphic accelerator x4500. As I have read on the forum, a lot of people reported problems with the driver of this chip. Some people have written that the driver has been fixed however, I still can't get the maximum resolution (1920x1080) which I can get with my other desktop. That resolution does not even exist in the list of available resolutions, the maximum is 1680x1050. However, if I chose a resolution above 1024x768, the display gets messed up and I cannot fix it unless I connect the PC to my old monitor, then I can see some part of the display and I have to lower it back to 1024x768.

My FPS using glxgears is horrible! it is 322!

Is there a fix for this? I thought Ubuntu 9.04 has fixed this problem but apparently it still exists.

Thank you very much.

---

### Post by whitethunder on 2009-04-15
OK guys, please be patient with me. This is my first time installing Linux on my home computer and I am having so much trouble with this graphic card. 

For some reason, my system halted and I had to reboot it. Now, when it boots up, right when I should see the log in display, my display gets messed up. It shows some garbage which I can't understand. My keyboard doesn't respond either, even num lock does not work. 

I had this problem with CentOS and it was due to the graphics card driver. I uninstalled CentOS and installed Ubuntu 9.04 and it was working OK, although with much lower resolution than what the card can support. 

Do you have any idea how I can fix this? 

I really appreciate your help.

---

### Post by rasmus91 on 2009-04-15
> Is there a fix for this? I thought Ubuntu 9.04 has fixed this problem but apparently it still exists.


Yeah, i can understand you have some hard troubles... I switched to UXA, I got a bit less fps, but a much much better flow, and direct rendering as well.

This is the way i added UXA:

```

cd /etc/X11

sudo nano xorg.conf


```

then your xorg opens:

find the device section and add:
```

Option "AccelMethod" "UXA"

```

Then save and quit, then reboot, and tell me what happens. Compiz is Muuuch better on my comp now.

---

### Post by farmfield on 2009-04-15
But isn't UXA way buggier on kernel 2.6.28.x..? I think that manual install of 2.6.29.1 is neccesary to get it stable - but i might be wrong...

With a machine with a x4500 one should really run 64bit Jaunty... Install it - and if you're as brave (or stupid) as me, you'll run ext4 on both root and home partitions (preferably on your production machine, hehe) - and update it fully. Then install the 2.6.29.1 kernel... (both files)

1: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-image-2.6.29-02062901-generic_2.6.29-02062901_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-image-2.6.29-02062901-generic_2.6.29-02062901_amd64.deb)

2: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901_2.6.29-02062901_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901_2.6.29-02062901_all.deb)

Let the installer overwrite the grub menu-lst as it keeps the 2.6.28.11 boot option anyway, so if your machine won't boot with 2.6.29.1 you'll just choose the older kernel from the list.

Then use [alt]+[f2] and run:

```
gksudo gedit /etc/X11/xorg.conf
```

Find the section 'device' and add the two lines:

```
   Option   "AccelMethod"   "uxa"  
   Option   "EXAOptimizeMigration" "true"
```

Save xorg.conf and restart gdm - logout, when asked for login, press [ctrl]+[alt]+[backspace] - or just reboot, same same...

Good luck! 8-)

---

### Post by whitethunder on 2009-04-15
Thanks to everybody for replying so quickly. My problem right now is even worse than bad resolution: I see random pixels on the display when the computer boots up (just garbage). This happend after I had to manually reboot the PC when it halted. 

I managed to boot in recovery mode and get the root command prompt. What do you think is making my display messed up? Is my driver damaged or my xorg.conf is damaged? This is how my xorg.conf looks like right now (I have to type it here, see between ======= and  ==========):

=========================================================
Section "Device"
 Identifier "Configured Video Device"
 Driver "vesa"
EndSection

Section "Monitor" 
 Identifier "configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection
======================================================

Is this file corrupted? If it is not, what should I do to fix the messed up display problem? 

Thanks again

---

### Post by farmfield on 2009-04-15
> **whitethunder said:**
> Thanks to everybody for replying so quickly. My problem right now is even worse than bad resolution: I see random pixels on the display when the computer boots up (just garbage). This happend after I had to manually reboot the PC when it halted. 

I managed to boot in recovery mode and get the root command prompt. What do you think is making my display messed up? Is my driver damaged or my xorg.conf is damaged? This is how my xorg.conf looks like right now (I have to type it here, see between ======= and  ==========):

=========================================================
Section "Device"
 Identifier "Configured Video Device"
[COLOR="Red"] Driver "vesa"[/COLOR]
EndSection

Section "Monitor" 
 Identifier "configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection
======================================================

Is this file corrupted? If it is not, what should I do to fix the messed up display problem? 

Thanks again
Paste my two lines replacing the red line - which are the one breaking your X...

Your configured device includes the driver - now your xorg have two, the configured device and the VESA driver, and the VESA isn't the right one...

And what we're doing here is an acception, basically xorg is going away, it's been somewhat replaced by HAL (hardware abstraction layer) so don't mess with it - accept for the UXA-stûff that is, hehe...

...there's no rule without an acception, right? ;^)

---

### Post by rasmus91 on 2009-04-15
Hey farm field, i'am planning to format my drive again when the finished version of 9.04 is out, and run ext4... did the thing you do solve all graphic problems?

btw, my UXA isn't more unstable than the EXA was... ;)

---

### Post by whitethunder on 2009-04-15
Thank you very much FarmField. I replaced the line with vesa with your two lines. Now, instead of garbabe, I get a blank screen with back light. Any ideas?

---

### Post by farmfield on 2009-04-15
> **whitethunder said:**
> Thank you very much FarmField. I replaced the line with vesa with your two lines. Now, instead of garbabe, I get a blank screen with back light. Any ideas?
Which Jaunty version and kernel versions are you running?

And as you kan access the xorg.conf in safemode, just remove the lines, then reboot, [esc] in grub, choose kernel 2.6.28.11 and you're back in GDM...

---

### Post by whitethunder on 2009-04-15
I have version 9.04. My kernel version is 2.6.28-11-generic. I removed your lines which I added and rebooted. Even without those, I get a black screen with back light.

---

### Post by farmfield on 2009-04-16
> **whitethunder said:**
> I have version 9.04. My kernel version is 2.6.28-11-generic. I removed your lines which I added and rebooted. Even without those, I get a black screen with back light.
I never talked about using this with 2.6.28.11 even though others did.

Make a fresh install of Jaunty 64 bit. Use **system->synaptic->mark all updates->apply** to update your system. Reboot. Then use my links to install the 2.6.29.1 kernel. Reboot. Add the two lines. Reboot.

And it should work. I won't guarantee it will, but it should.;)

---

### Post by whitethunder on 2009-04-16
This is not related to the display problem but since you suggested reinstalling the OS. I have a RAID 5 on that PC. Do you think I can reassemble it without losing any data if I reinstall the OS?

Thanks.

---

### Post by farmfield on 2009-04-16
> **whitethunder said:**
> This is not related to the display problem but since you suggested reinstalling the OS. I have a RAID 5 on that PC. Do you think I can reassemble it without losing any data if I reinstall the OS?
Sorry, I have no clue about raid, haven't used raided disks since the late nineties...:(

---

### Post by NT4usB on 2009-04-16
> **whitethunder said:**
> This is not related to the display problem but since you suggested reinstalling the OS. I have a RAID 5 on that PC. Do you think I can reassemble it without losing any data if I reinstall the OS?

Thanks.

No need to reinstall.
Several ways to get your video back:

A. Ctrl+Alt+F1 to switch to a tty. cd /etc/X11/ 
copy the backup you made of xorg.conf before you edited it to xorg.conf.

B. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

C. iirc, there's a new command xconfigure-xorg (or something) that may also work. google it.

D. If you can't get to a tty, even from recovery mode, boot to a live CD, mount the HD, then edit xorg.conf. Delete xorg.conf and failsafe xorg should kick in and give you some graphics to work with.

Reinstalling, aka Fixing it 'the Windows way' shouldn't even be on the table...

---

### Post by whitethunder on 2009-04-17
Hi all, 

I have come to the conclusion that my problem is not an xorg.conf problem. when I run the pc with the live cd, it works fine. It complains that something is not right with the display but when I choose "fail safe" option, it works. 

After I ran Ubuntu with the live cd, I went to the /etc/X11 folder and checked xorg.conf and xorg.conf.failsave. These two files are exactly like what I have on my own harddisk, however, when I boot using the ubuntu on the harddisk, I only get a black screen and my keyboard doesn't work! 

I was thinking about reinstalling the OS but then, I thougt that I should accept the challenge and fix this once for all. It might happen again ;). so I would be grateful if you can tell me whatever you think it might work.

---

### Post by djuliette on 2009-04-17
I'm having the same problems with my video.  8.10 worked like a charm then I updated to 9.04 two days ago and video is choppy and the desktop effects are very slow (AWN dock is slow and the desktop cube barely works, in 8.10 they were fine).
I've tried all the xorg.conf chages listed in this thread to no effect, not better not worse.
I used the update manager to go from 8.10 to 9.04, has anyone gotten good results from a fresh install?

---

### Post by Murrquan on 2009-04-18
> **djuliette said:**
> I'm having the same problems with my video.  8.10 worked like a charm then I updated to 9.04 two days ago and video is choppy and the desktop effects are very slow (AWN dock is slow and the desktop cube barely works, in 8.10 they were fine).
I've tried all the xorg.conf chages listed in this thread to no effect, not better not worse.
I used the update manager to go from 8.10 to 9.04, has anyone gotten good results from a fresh install?

I'm in more or less the same boat; I haven't done anything to xorg.conf, but I tried the Intel PPA at [https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa) with seemingly no result. Very frustrating framerate drop.

And here I'd been hoping that 9.04 would *solve* my problems. >.>

---

### Post by smaw0351 on 2009-04-18
> **Murrquan said:**
> I'm in more or less the same boat; I haven't done anything to xorg.conf, but I tried the Intel PPA at [https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa) with seemingly no result. Very frustrating framerate drop.

And here I'd been hoping that 9.04 would *solve* my problems. >.>

wow, thanks for posting this! i thought upgrading would solve my problems on my latitude e6400. i'll hold for now :)

---

### Post by farmfield on 2009-04-18
For me it was the manual update to kernel 2.6.29.1 and activating UXA that solved the choppy framerate as well as Google Earth (which never worked on this computer with Compiz activated before)...

I actually run kernel 2.6.30rc2 now as VirtualBox kernel module wouldn't compile under 29.1 and so far it's stable... I'm in awe, hehe... :D

[I]OT: @djuliette

Check out Cairo-Dock, AWN doesn't seem to keep up, CD are way ahead... They won't be able to compete with Gnome-DO/Docky in the long run, but for now they're way ahead of the competition...[/I]

---

### Post by smaw0351 on 2009-04-18
> **farmfield said:**
> For me it was the manual update to kernel 2.6.29.1 and activating UXA that solved the choppy framerate as well as Google Earth (which never worked on this computer with Compiz activated before)...

I actually run kernel 2.6.30rc2 now as VirtualBox kernel module wouldn't compile under 29.1 and so far it's stable... I'm in awe, hehe... :D

[I]OT: @djuliette

Check out Cairo-Dock, AWN doesn't seem to keep up, CD are way ahead... They won't be able to compete with Gnome-DO/Docky in the long run, but for now they're way ahead of the competition...[/I]

what kind of frame rate are you getting now?

---

### Post by farmfield on 2009-04-18
Just 7-800fps in glxgears but it's not only the framerates, the machine feel way smoother in Compiz, Google Earth a.s.o... So I prefer this over getting 1000+ fps in an app that maybe doesn't say that much anyway, hehe...

I don't game though, so I have no clue how it would perform in a 3D game...:(

---

### Post by densou on 2009-04-18
> **djuliette said:**
> I used the update manager to go from 8.10 to 9.04, has anyone gotten good results from a fresh install?

me (fresh Jaunty's Beta install) after I didn't get any pro (random bugs/issues) upgrading from Intrepid. I'd recommend a fresh install, it worked like a charm :D (I use a separate /home since I installed Feisty)


> **Murrquan said:**
> And here I'd been hoping that 9.04 would *solve* my problems.

I haven't ever seen a good release like Jaunty. Gusty/Feisty neither.

It has few annoying issues (not always related against Canonical), but overall is worthwhile more than a mere try ;)

Especially for testing UXA (God-like here / GMA950)

---

### Post by smaw0351 on 2009-04-18
> **farmfield said:**
> Just 7-800fps in glxgears but it's not only the framerates, the machine feel way smoother in Compiz, Google Earth a.s.o... So I prefer this over getting 1000+ fps in an app that maybe doesn't say that much anyway, hehe...

I don't game though, so I have no clue how it would perform in a 3D game...:(

would you mind posting how you did it, or link me to the steps? i'd rather try a proven method.

thanks!

---

### Post by rasmus91 on 2009-04-20
> wow, thanks for posting this! i thought upgrading would solve my problems on my latitude e6400. i'll hold for now 

But i have a E6400 and my computer runs like never before... Even though i still have big problems getting things to work in wine. But i've been offered by my school to get XP free, and legally, So I'm gonna go back to Dual booting. I've run linux only for a while now, and it has been a pleasent run. I do however have some crappy problems with some windows programs which are forcing me to dual boot windows XP... Plus, at the time i had vista NWN2 never ran probably, now i get the chance to play the sucessor my favorite game of all times ( :D ) As time passes by I'll go back to linux only again. But as far as I'm concerned now, this will be the easiest solution for me.

As a warning if you consider upgrading: I use UXA, runs smooth, with a frame rate just around 900-999... i have direct rendering but! Theres a problem with the pixelshader, Which is resulting in a low framerate in the game Urban terror, and the game NWN crashing when people are firing certain spells and stuff.

---

### Post by Demophobie on 2009-04-20
Hey!

Update: I have a Dell Latitude E4300. Using Gentoo now.
Intel 2.6.3-r1 with unmasked Mesa/Xserver version gives me (on 2.6.29-r1 kernel): glxgears

6089 frames in 5.0 seconds = 1217.772 FPS
6335 frames in 5.0 seconds = 1266.925 FPS

Best result i ever had. Still have problems in 3D Games. Very slow.
The guys in the intel channel tell me, that glxgears is no way to compare graphics power.

Intel 2.7.0 released - waiting for an ebuild and will give update.

---

### Post by smaw0351 on 2009-04-21
i just upgraded to jaunty today from intrepid.

i'm on a latitude e6400 using the intel gma 4500 mhd driver.

on intrepid i was getting between 100-200 fps now with jaunty i'm getting about 750 fps.

compiz is a lot smoother also.

my cpu's are in the single digit percent utilization at rest instead of the double digits at rest with intrepid.

jaunty is looking good so far!!!!!!

---

### Post by farmfield on 2009-04-22
64bit Jaunty + kernel 2.6.30rc3 + UXA - works like a charm, 1100+ fps in glxgears, flickerfree fullscreen HD on youtube even when spinning the compiz 'globe' a.s.o... WOW!

RC3: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/)

---

### Post by whitethunder on 2009-04-23
Hi guys, 

I fixed my black screen problem. I had to uninstall and reinstall the x server. The resolution problem still exists.

---

### Post by keypox on 2009-04-24
> **farmfield said:**
> 64bit Jaunty + kernel 2.6.30rc3 + UXA - works like a charm, 1100+ fps in glxgears, flickerfree fullscreen HD on youtube even when spinning the compiz 'globe' a.s.o... WOW!

RC3: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/)

what is uxa? Further how do you install the new kernel?  I downloaded the last file and restarted but i dint see the new kernel

---

### Post by whitethunder on 2009-04-24
Another problem of this sort: 

When I wake up the system from suspend, the same exact problem that I had before happens. I get a black screen and my mouse and keyboard don't work. If I restart, things work fine! 

This is a funny OS! You know what? Ubuntu actually made me appreciate Windows XP a lot! (hey, please don't beat me for praising windows on linux forum!)

---

### Post by keypox on 2009-04-24
> **keypox said:**
> what is uxa? Further how do you install the new kernel?  I downloaded the last file and restarted but i dint see the new kernel

Never mind i found this in this thread lol

Then use [alt]+[f2] and run:

Code:

gksudo gedit /etc/X11/xorg.conf

Find the section 'device' and add the two lines:

Code:

   Option   "AccelMethod"   "uxa"  
   Option   "EXAOptimizeMigration" "true"

Save xorg.conf and restart gdm - logout, when asked for login, press [ctrl]+[alt]+[backspace] - or just reboot, same same...

im not getting 1100+ though after doing this and i got the new kernel installed.  Had to install all the files on that link lol

---

### Post by densou on 2009-04-25
my GMA950 works wonderful with UXA, but I found an annoying issue: awful video output when playing SD sources (not on HD ones!), x11 (best for me)-xv-xvmc

so I thought to upgrade xf86-video-intel to fairly new 2.7.0, but I had no improvement :(

I solved this nuisance installing Gnome Mplayer 0.9.5 (.deb), now UXA beats EXA at all :guitar:

---

### Post by Olnex on 2009-05-10
Weird, I tried Ubuntu 8.04.2, glxgears gives me 900-1100 fps, while 9.04 gives me only 600-700 fps, both with latest updates. Here is my lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
85:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)

```

---

### Post by Olnex on 2009-05-10
Also, I am now using 9.04 with latest updates, I added UXA option and something migration to true to xorg.conf, now glxgears gives me around 500 fps(was 700) but now I can watch youtube fullscreen without pause.

---

### Post by farmfield on 2009-05-11
[Kernel 2.6.30rc4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/") gives me 1100+ fps but can't run Google Earth while running Compiz (it starts, but 3D is screwed, flickering a.s.o.) - same prob's as earlier...

Acitivating UXA I get the same fps and Google Earth works perfectly while running Compiz - for a while, then my computer (a [Compaq Presario CQ60]("http://www.pricerunner.co.uk/pl/27-1206001/Laptop-Computers/Compaq-Presario-CQ60-214EM-Intel-Celeron-Dual-Core-T1600-1.66GHz-3GB-250GB-TFT15.6-DVDRW-Win-Vista-Home-Premium-Compare-Prices")) goes into chewing-gum-mode and is unuseable... Reboot anyone? Going once, twice... ;^)

It feels like they're getting closer though, couldn't run UXA at all with either rc2 or 3...

1100-1200 fps is low though, it should perform twice that - but on the other hand 'they' (developers, people who know?) say glxgears is meningless as a benchmarking tool... And I don't care about specifik fps anyway, I just want basic 3D to work while compiz is running...

---

### Post by farmfield on 2009-05-11
Semi-ot:

Anyone got problems doing screenrecordings? I never got that working, I get totally screwed up graphics, artifacts a.s.o. and UXA or no UXA doesn't make any difference... My graphics memory might be defect though, kinda feel lika more probable than a driver issue...

---

### Post by Olnex on 2009-05-12
There is a problem, when I add AccelMethod UXA and XAAOptimizeMigration true to xorg.conf, I cannot play Diablo II Exp (via wine) any more, wine gives me a window that says access violate, and running command line I see main_dri2.c or something(I cannot remember the exact file name) is missing.

---

### Post by farmfield on 2009-05-12
I don't know if I updated this but Plun wrote about it and this is what I use in my xorg.conf now:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" # may break 3D rendering if enabled
EndSection
```

This works with 2.6.29.3 but not (stable anyway) with any of the .30rc1-5


For you entering this thread late you open xorg.conf by using [alt]+[f2] and running

```
gksudo gedit /etc/X11/xorg.conf
```

Enter your password when asked and replace the device section with the code above. I can't guarantee it'll work on any specific machine though, but try it out...

***

---

### Post by Olnex on 2009-05-13
After checking Xorg.0.log (System->Administration->Log File Viewer), I found that:

(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

So what actually works are AccelMethod and Tiling, and UXA alone causes wine+DiabloII crashes, adding Tiling "false" resolves the problem.

---

### Post by farmfield on 2009-05-13
I don't have those lines in my log, so it might be used in my computer then...

But to be honest, I find this crap way to fuzzy, hehe, as it's all trial and error... It took the chinese 2000 years to work out their medicine, I hope we figure this out faster than that, hehe... ;^)

Why do I once again get that feeling this is about a design flaw in the hardware, otherwise, why do they have such problems getting the drivers to work...

Currently I'm using kernel 2.6.29.3 and UXA and it seems to be working, at least for the moment. Had some weird errors in Thunderbird, but not sure it's connected to UXA.

I'll also reboot into .30rc5 again today and check it out as I found out yesterday that though I thought I were running rc5 yesterday I was actually running rc4 and I'll reconfigure my boot.lst and try rc5 for real - and of course give you all a report in this thread... =)

@Olnex

You never wrote which kernel you run..?

---

### Post by Olnex on 2009-05-13
I am running Ubuntu 9.04 with default kernal(without any self-compiled things) and latest updates.

---

### Post by farmfield on 2009-05-13
Whoa, compiling kernels? Never, hehe... xD

They are all available as deb's...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by whitethunder on 2009-05-17
How long does it usually take for a Graphic Accelerator like this to be nicely supported in Ubuntu?

Is there any way to find information about the group or individual who is working on the driver for this chip?

---

### Post by densou on 2009-05-18
> **whitethunder said:**
> How long does it usually take for a Graphic Accelerator like this to be nicely supported in Ubuntu?

(imo) Jaunty is the best Ubuntu release so far concerning Intel GMA's support [cons: one annoying nuisance, MTRR range not recognized at every X boot]. However if you meant "to be nicely supported OUT-OF-THE-BOX", I'd recommend Fedora or Mandriva rather than Ubuntu, definitely. ;)

> Is there any way to find information about the group or individual who is working on the driver for this chip?

[http://intellinuxgraphics.org](http://intellinuxgraphics.org)

---

### Post by xxeper on 2009-06-30
I'm trying to add:

```
deb [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu) jaunty main
```but I can't get the key from 1FCB21DB

I've tried:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1FCB21DB
```But I get:

```
gpg: requesting key 1FCB21DB from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```Ideas?

Maybe there's another way to fix what I'm looking to fix. I've got an E6500 with the Intel 4500MHD and it works perfectly in Jaunty, until I plug my laptop into the dock and go to my two 1680x1050 displays. I can get both working, however, monitor #2 has what I like to call a "black hole" over 2/3 of the screen where I get trails from anything moved over it, and when I rotate [cube] to other desktops, it's "see through" showing the other virtual desktops.

Please tell me there's a fix for this.

Here's my xorg.conf

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    3360 1050
    EndSubSection
EndSection

Section "Device"
    Identifier    "Intel X4500MHD"
    Driver        "intel"
    VendorName    "Intel Corporation"
    BoardName    "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID        "PCI:0:2:0"
    Option        "DRI" "true"
    Option        "AccelMethod"        "UXA"
    Option        "EXAOptimizeMigration"    "true"
    Option        "MigrationHeuristic"    "greedy"
    Option        "Tiling"        "false"
EndSection
```

edit: This ONLY happens with the appearance effects [compiz, etc] on.

---

### Post by Olnex on 2009-06-30
You can try this one:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

it works for me without problem.

---

### Post by wijit on 2009-07-01
I have got this error after routinely update failed and a try to follow suggestions from ubuntu forum:
```
pv@pv-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
pv@pv-desktop:~$ 
```
Help is needed. Followed is a brief description of the system that the problem occured:
A Compaq Presario, P4, 256Mb RAM
ubuntu Jaunty which update dead since 2.6.28-11

---

### Post by xxeper on 2009-07-01
I was finally able to update the Intel driver, but I'm getting the same issue. Black hole on monitor #2, unless I turn all effects off.

Any ideas?

Is anyone else here using a 4500 MHD with two monitors on a laptop?

EDIT: I guess this has "something" to do with it :(

> Note that the maximum supported size of the virtual desktop []("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#") for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled. This may matter if you like games and compiz desktop effects, or if you want Google Earth to display in better than geological time. Obviously the larger the virtual desktop, the more graphics memory is used. So for good performance with a shared graphics system such as Intel the Virtual should be no larger than necessary. Oh well :(

---

### Post by davidY on 2009-07-16
Using the bleeding edge xorg ppa and the new kernel in the same ppa, you get good video performance. Bad youtube performance.

---

### Post by checoimg on 2009-08-21
I got a zip file from intel pega called ASPEED_AST2050.ZIP and entered to the folder[COLOR=Lime] [COLOR=Green]/ASPEED AST2050/Linux/Linux/[/COLOR][/COLOR] , then opened [COLOR=Green]lxdrv.tar.gz[/COLOR]. Finally ran [COLOR=Green]update.sh[/COLOR] in a terminal.
I didn't exactly know what I was doing. Then when I shut off my Lap a Debian screen that I never saw appeared. weird for me cause I'm used to see only Ubuntu screens. 

Another esult is that when I did GLXGEARS instead of 300 fps I got 900 fps.

I'll try to find out what I did I still have the ZIP archive.

This is the link:

[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=3137&DwnldID=17980&lang=por&iid=dc_rss](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=3137&DwnldID=17980&lang=por&iid=dc_rss)

---

### Post by checoimg on 2009-08-28
This is the contente of the .sh file that I was talking about.
But then I decided to do the safe configuration of the other thread
 after wich it made glxgears go to 400 fps.

And the point is that the readme file of the driver says to run update.sh on a terminal 
---------------------------------------------------------------------------------------------------------------------------
#!/bin/sh

# Set Variables 
XF86_LIB_DIR="/usr/X11R6/lib/modules"
XF86_DRV_DIR="/usr/X11R6/lib/modules/drivers"

# Uninstall
if [ "$1" = "uninstall" ]; then
echo "AST2000/2100 Linux XF86 driver uninstall begin ...."
rm -f $XF86_DRV_DIR/ast_drv.*
# rm -f $XF86_LIB_DIR/libddc.*
# rm -f $XF86_LIB_DIR/libfb.*
# rm -f $XF86_LIB_DIR/libint10.*
# rm -f $XF86_LIB_DIR/libramdac.*
# rm -f $XF86_LIB_DIR/libvbe.*
# rm -f $XF86_LIB_DIR/libvgahw.*
# rm -f $XF86_LIB_DIR/libxaa.*

test -e ./backup/ast_drv.* && cp -f ./backup/ast_drv.*   $XF86_DRV_DIR
# cp -f ./backup/libddc.*    $XF86_LIB_DIR
# cp -f ./backup/libfb.*     $XF86_LIB_DIR
# cp -f ./backup/libint10.*  $XF86_LIB_DIR
# cp -f ./backup/libramdac.* $XF86_LIB_DIR
# cp -f ./backup/libvbe.*    $XF86_LIB_DIR
# cp -f ./backup/libvgahw.*  $XF86_LIB_DIR
# cp -f ./backup/libxaa.*    $XF86_LIB_DIR

rm -rf ./backup
echo "AST2000/2100 Linux XF86 driver Uninstall Finished"
exit 0
fi

# Install
echo "AST2000/2100 Linux XF86 driver update begin ...."
rm -rf ./backup
mkdir ./backup
test -e $XF86_DRV_DIR/ast_drv.* && cp -f $XF86_DRV_DIR/ast_drv.* ./backup
# cp -f $XF86_LIB_DIR/libddc.* ./backup
# cp -f $XF86_LIB_DIR/libfb.* ./backup
# cp -f $XF86_LIB_DIR/libint10.* ./backup
# cp -f $XF86_LIB_DIR/libramdac.* ./backup
# cp -f $XF86_LIB_DIR/libvbe.* ./backup
# cp -f $XF86_LIB_DIR/libvgahw.* ./backup
# cp -f $XF86_LIB_DIR/libxaa.* ./backup

rm -f $XF86_DRV_DIR/ast_drv.*
# rm -f $XF86_LIB_DIR/libddc.*
# rm -f $XF86_LIB_DIR/libfb.*
# rm -f $XF86_LIB_DIR/libint10.*
# rm -f $XF86_LIB_DIR/libramdac.*
# rm -f $XF86_LIB_DIR/libvbe.*
# rm -f $XF86_LIB_DIR/libvgahw.*
# rm -f $XF86_LIB_DIR/libxaa.*

cp -f ast_drv.*   $XF86_DRV_DIR
# cp -f libddc.*    $XF86_LIB_DIR
# cp -f libfb.*     $XF86_LIB_DIR
# cp -f libint10.*  $XF86_LIB_DIR
# cp -f libramdac.* $XF86_LIB_DIR
# cp -f libvbe.*    $XF86_LIB_DIR
# cp -f libvgahw.*  $XF86_LIB_DIR
# cp -f libxaa.*    $XF86_LIB_DIR

echo "AST2000/2100 Linux XF86 driver update finished"
--------------------------------------------------------------------------------------------------

---

### Post by Junkieman on 2009-09-27
Hi all, another 4500 owner here, I'm hoping someone could give me some tips for upping the frame rate :)

Compiz runs pretty smooth, even youtube videos play without trouble. But I have a problem running certain games, specifically Super Tux Kart, its actually unplayable. This is with desktop composition turned off. Though I'm not fanatical about games, I'd love to get this working :)

I thought it's a hardware acceleration issue, and installed the [xorg Intel drivers (2.5.1)](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/), with no improvement. Do I need a newer kernel for this to work, or some extra configuration I have missed?

Any help will be much appreciated :)

**More info**
Intel DG45ID Desktop board, uses the X4500HD graphics chipset
Ubuntu 8.10 kernel 2.6.27-14
xorg Intel drivers 2.5.1
glxgears gives 250fps
direct rendering: Yes

---

### Post by Takehaniyasubiko on 2009-10-19
Hi,

Any news about GMA 4500 performance in Ubuntu 9.10?

---

### Post by rasmus91 on 2009-11-12
Hi again.

Sorry i haven't posted any updates or anything for a long time. But currently im running Win(doh!)s 7 for a school app that i need, and haven't had time to get working in wine.

That said, I'm still trying to find out if, and when better drivers are developed for this graphics card. And I'd like to know if anyone have been able to run a Direct3D game in wine?

If anyone wonders about what there is to the most recent drivers i can recommend checking this page[http://intellinuxgraphics.org/testing.html]("http://intellinuxgraphics.org/testing.html")

to see what tests it has passed...

I'm short of time.

See ya' all later!

---

### Post by Sarcaza on 2009-11-17
> **Takehaniyasubiko said:**
> Hi,

Any news about GMA 4500 performance in Ubuntu 9.10?

Hi, I recently installed Kubuntu 9.10 on a latitude E6400 with the 4500MHD card.  The install is still pretty much all defaults and went totally smooth except the broadcom wireless card which was a bit of a hassle (wouldn't auto-detect, had to download the drivers from the broadcom site and install them by hand, even then, I get tons of errors and frequent network drops on a WPA2 home network).  

My glxgears results are:

glxgears
1913 frames in 5.0 seconds
2819 frames in 5.0 seconds
2824 frames in 5.0 seconds

Which I guess is pretty good.  

Compositing works well too, and I'm getting around 40-90fps according to the Show FPS plugin although it is still a little too slow for normal use.

Google earth is not too great, fairly jerky, but useable.

Youtube "HD" videos in full screen run pretty well with the occasional jerkiness or glitch although it seems to be less with compositing disabled.

I haven't played too many games but for the two I've tried:
Supertuxkart is very playable at 1024x768 in windowed mode (sorry don't know how to get FPS).
Heroes of Newerth beta is totally unplayable because everything but health bars is not rendered, or rendered as solid black.  The intro screen has VERY low fps.

If anyone has any very easy to install games they'd like me to test, let me know.

I hope this helps!

Sam

---

### Post by rasmus91 on 2009-11-23
Did you ever run wine?

I played Guild Wars, and i talked a lot about in in the Beginning of this test. I had a Direct 3D rendering ERROR... you could try installing guild wars through wine... If you want the super easy install download PlayOnLinux here: [http://playonlinux.com/en/]("http://playonlinux.com/en/") install it, run it and find guild wars. The old error was before it could even enter the game, so you won't need an account to check if it is any better.

I also tried neverwinter nights on this computer, and it ran smooth, until end of prelude where it would crash due to some shader Error. If you'd like you could test Neverwinter nights, It's downloadable from bioware. but you'll need a serial.

(As i believe i said, i run windows 7 for school purposes... And it sucks.)
Furthermore i've been running Test on my computer today. And it turns out the CPU is set to (under)clock to 800 Mhz when the sensors tmp4/tmp5 Measure 65 degrees celcius. This causes some of the problem. And it has something to do with the BIOS Which Dell has promised to solve by releasing a new BIOS update.

For Further Information on this topic, go to [http://en.community.dell.com/forums/p/19247293/19492010.aspx?PageIndex=1]("http://en.community.dell.com/forums/p/19247293/19492010.aspx?PageIndex=1") heres a lot of information, as well as a lot of very good links.

I'll be back soon.

Cheers, Rasmus.

---

### Post by csq on 2009-11-24
I recently bought an Dell E5400 with Intel G45 card also. I started with Fedora 11 and later 12. They turned me down completely, so many annoying problems, the computer freezes for no reason, the resolution is never right, ... I switch to ubuntu recently and seems it works right away. However, I want to know is there any simple test I can run to make sure everything is right?

I run the glxgears:
2415 frames in 5.0 seconds
2189 frames in 5.0 seconds
2230 frames in 5.0 seconds

pretty good.

---

### Post by csq on 2009-11-24
wait a second,

2415 frames in 5.0 seconds
2189 frames in 5.0 seconds
2230 frames in 5.0 seconds

gives approximately 400-500 fps. This seems a pretty small figure.

---

### Post by csq on 2009-11-24
Another problem.

Why I don't have xorg.conf in /etc/X11?  Am I missing something?

---

### Post by rasmus91 on 2009-11-25
I'm pretty sure you do have a xorg.conf there... Pehaps its hidden. But back when i ran ubuntu i edited xorg.conf to UXA... This ran far better than before. aprox. 950-1300 fps. plus all rendering was better.

Good luck, write if you need further help. i think it's limited what i can do though, as i do not have a Linux System on my own computer, which makes it rather difficult for me to test stuff my self.


Cheers, Rasmus

---

### Post by csq on 2009-11-25
Hi, rasmus91
I generated the xconf.org. what should I do then?

---

### Post by rasmus91 on 2009-12-01
It depends. What do you wish to do?

If i was you, i'd try running UXA. to do that:

Add this under the Device section in your xorg.conf:
```
Option "AccelMethod" "UXA"
```

Remember to do this as root. (you could "nano" the xorg.conf through bash)

Good Luck. I'llbe back ;)

---

### Post by infestor on 2009-12-13
```
2346 frames in 5.0 seconds
2157 frames in 5.0 seconds
2112 frames in 5.0 seconds

```

do you think these fps values are alright?

---

### Post by rasmus91 on 2009-12-13
Perhaps, depends on you xorg.conf

Do you use UXA settings?

I found those to be the best at 3D rendering, not the fastest, but most reliable + the rate didn't drop much while playing games and stuff.

cheers, Rasmus

---

### Post by checoimg on 2009-12-14
Try Fedora 12 It works out of the box from the DVD I couldnt find the solution in Ubuntu. Test the driver using Blender 3D

---

### Post by rasmus91 on 2009-12-15
Hey there.

I just read a danish review of Ubuntu 9.10 and the intel cards. And it says that even though the framerate seems slow it's better than ever.

I testet it a bit my self, and i'm able to run quite a bit of different games in wine.

Oh, and by the way; The Xorg.conf will not be generated by the system due to a new way of doing the x.org thing. so don't generate one unless necessary. (nvidia drivers makes one by default.) The intel driver runs UXA by default by now.

So bottom line is that the intel card works quite allright in Ubuntu atm, and for that we can thank the Ubuntu team and the Intel-linux drivers team.

Cheers, Rasmus

---

### Post by csq on 2009-12-16
Hi, Rasmus

My problem is that if I close glxgears openGL window, there is an error message: 

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 23973 requests (23970 known processed) with 0 events remaining.

It is very annoying. In some other applications, I can't even close the openGL window.

---

### Post by csq on 2009-12-16
[FONT=monospace]Regarding frame rate, I add the following to xorg.conf, then I get 800 frames per second. Much better,

    Option "AccelMethod" "uxa"
    Option "EXAOptimizeMigration" "true"
[/FONT]

---

### Post by csq on 2009-12-17
Another improvement.
I update some OpenGL package, right now I have 1100 fps

---

### Post by rasmus91 on 2009-12-29
sounds sweet... For everyone's benefit would you post some links and some info on what you did?

---

### Post by csq on 2009-12-31
Actually, I don't recommend updating OpenGL package. I think what I did is to update Mesa, but it turns out to totally break some other opengl packages.
I will say stick with 
[FONT=monospace]Option "AccelMethod" "uxa"
    Option "EXAOptimizeMigration" "true".

Happy new year.
[/FONT]

---

### Post by rasmus91 on 2010-01-07
Thanks for the help.

---

### Post by rasmus91 on 2010-02-08
I'm afraid that the intel drivers still have their problems, i would go as far as saying that next time i buy a laptop it will have an nVidia card, why? well, because imo nVidia kicks everything else right in the nuts...

I'm unable to play DDO though following the guide at winehq. this is getting tiresome...

---

### Post by Junkieman on 2010-02-10
I know Intel released their hardware specs so that better drivers can be created, but it will probably take a while before anything solid is reached. 

So meanwhile I invested in a nVidia 9800, after much research and asking around. Im pretty happy with it, but will keep my eye on the Intel progress at the same time.

glxgears give me these now :)
```
89287 frames in 5.0 seconds
89996 frames in 5.0 seconds
90401 frames in 5.0 seconds

```

---

### Post by rasmus91 on 2010-02-11
> glxgears give me these now  Glxgears is not a real benchmark, it's just made for testing your 3d.

Did you put a nvidia 9800 in your laptop?
i don't get it...

---

### Post by rasmus91 on 2010-02-22
Okay guys, added the most recent intel ppa's to my repository, and i've decided to install playOnLinux, and install Mount & Blade(this thread: [http://ubuntuforums.org/showthread.php?t=1234368&highlight=mount+blade]("http://ubuntuforums.org/showthread.php?t=1234368&highlight=mount+blade")), and see if it works, if it doesn't im gonna backup my recent data and format to Lucid Alpha to see how the drivers are there.

And, well, I'm never ever gonna Buy anything with intel onboard graphics again. Never.

---

### Post by pingu1 on 2010-03-07
Do you guys think it's an O.K. buy to get a computer with Intel GMA 4500 for Ubuntu?
I don't really use hard-core games, but I would like good graphics for movies and for CompizFusion and so on...

A penny for your thoughts on this.... I see 80% of the laptops have this card....

---

### Post by pingu1 on 2010-03-07
And: is nVidia a 100% guaranteed success if you buy a laptop with nVidia-card?
Even the new ones?

---

### Post by pingu1 on 2010-03-07
I think I'll be going with nVidia, but it would be nice to get a comparison between Intel GMA 4500 and an nVidia card when it comes to the performances I mentioned 2 threads ago... (basic 3D use/resolution/compiz-fusion).

---

### Post by rasmus91 on 2010-04-08
> And: is nVidia a 100% guaranteed success if you buy a laptop with nVidia-card?
Even the new ones?

supposedly, i think they have the best support.

> I think I'll be going with nVidia, but it would be nice to get a comparison between Intel GMA 4500 and an nVidia card when it comes to the performances I mentioned 2 threads ago... (basic 3D use/resolution/compiz-fusion).

I Don't think you'd need those to tell that nvidia is best by far.
My laptop sometimes crashed compiz, a nVidia card will have much more fps than these intel Cards + You'll have reduced waiting time when it comes to Image editing, 3D modelling etc.

Also Games run better, and you'll be able to game in wine.

Cheers, Rasmus.

---

### Post by rasmus91 on 2010-05-05
As i have installed Lucid, i will soon (probably today) do a test, just to see if i can actually do anything.

I'd very much like to play runescape, but unfortunately it just wont run in anything but safemode.
I have some reason to believe that this is due to my graphics card, but i'm just not sure of it.

---

### Post by messie on 2010-05-07
Greetings, and sorry if I am hijacking the trhead, however it seems the right place to me.

I also have the damned 4500 mhd... The problem is that it crashes after a couple of minutes running a 3d app. With windows, the screen goes black and the notification says the graphics card stopped to work and recovered. With ubuntu, the whole system goes nuts and crashes forever and I have to reboot. I own a toshiba portege m800-10z. I hope someone has some idea of what is going on, however i suspect hardware failure...

---

### Post by Linuxforall on 2010-05-07
Try the Xswat ppa for updated Intel drivers and see if you get better performance.

---

### Post by rasmus91 on 2010-05-07
> Greetings, and sorry if I am hijacking the trhead, however it seems the right place to me.

Thats okay... As long as it lives ;)

> I also have the damned 4500 mhd... The problem is that it crashes after a couple of minutes running a 3d app. With windows, the screen goes black and the notification says the graphics card stopped to work and recovered. With ubuntu, the whole system goes nuts and crashes forever and I have to reboot. I own a toshiba portege m800-10z. I hope someone has some idea of what is going on, however i suspect hardware failure...

Well, 4500 has run sooooo bad on this computer, nothing like what you are describing though, my guess is its a hardware problem.

---

### Post by gbrubal on 2010-07-09
Hi, i have the intel  gma 4500hd (its a pavillion dv3, no other video card) and i cant seem to get the brightness to work. Any clues?

---

### Post by 007casper on 2010-09-01
I have a 30" apple cinema display. The monitor handles up to 2560 x 1600 pixels which is the optimum resolution for this monitor. I found out that most apple monitors have nvidia graphic card.
 
The monitor is hooked up to a motherboard Intel BOXDG45FC. This motherboard has Onboard Video Chipset Intel GMA 4500. However, using KDE interface I dont get beyond 1280x800 resolution for the monitor.
 
How can I get the maximum resolution for the monitor?

I have started a threat here, and it seems nobody has the answer.  Maybe it is just facing me straight, and I just cant figure out how to go about it.
[http://ubuntuforums.org/showthread.php?t=1457530&highlight=Intel+GMA+4500](http://ubuntuforums.org/showthread.php?t=1457530&highlight=Intel+GMA+4500)

I dont have xorg.conf file

Please, advise.

---

### Post by rasmus91 on 2010-09-02
> I dont have xorg.conf file

No, it was removed. You can generate one though, but i'd advice you not to as my display wacked up last time i did that.

Im sorry, but i don't think i can offer much help on this because i've switched out my laptop to a much much better one.

---

