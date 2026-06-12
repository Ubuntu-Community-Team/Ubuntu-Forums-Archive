---
title: "HP Elitebook 8440p Graphics."
date: 2010-08-01
forum: Hardware
---

### Post by JJ452 on 2010-08-01
Hi,

Ubuntu 10.04 will not detect the Intel HD graphics on my laptop (Core i5 520m). This results in the laptop not being able to detect any external monitors or projectors via the VGA port or any eye candy being enabled. Does Ubuntu officially support the Intel HD Graphics  or is it my laptop?

---

### Post by JJ452 on 2010-08-07
I hate to be a pain but does anyone know anything?

---

### Post by krazyd on 2010-08-09
it works out of the box on my 8440p with the i7-620M

what's the output of

```
glxinfo | grep -C 4 renderer
```

---

### Post by jdv2272 on 2010-08-10
Doesn't work on my HP 8440p Elite I5 either though I can see the external monitor.   I don't see anything on the laptop's built in display.   Simply the backlight.   So far I've been able to use it on external monitors just fine.  Really makes using the laptop a challenge.

Here is the out put from the glxinfo for my laptop.

GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, GL_ARB_copy_buffer, 

Any ideas, I think there was a bug entered for this but I believe it has been closed now.

thanks
John

---

### Post by JJ452 on 2010-08-10
> **krazyd said:**
> it works out of the box on my 8440p with the i7-620M

what's the output of

```
glxinfo | grep -C 4 renderer
```

Interesting, do you have an Nvidia Card? I'll post that tomorrow as I left my laptop at work. I had to change the drivers to vesa to get the laptop screen to work but this killed the vga port (maybe the vesa drivers can't recognise any of the monitors). When I changed the vesa to intel it went into some recovery thing and I had to change it back.

---

### Post by JJ452 on 2010-08-13
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 


That's the output. I hadn't that installed so I did that also. Thoughts?

---

### Post by krazyd on 2010-08-15
@jdv2272: there is a bug in the driver - just boot with the external monitor unplugged or the main screen won't work.

@JJ452: somehow, you don't have the intel driver enabled and/or installed. How did you install Ubuntu? And what happens if you backup and then delete your Xorg.conf?

---

### Post by JJ452 on 2010-08-17
> **krazyd said:**
> 
@JJ452: somehow, you don't have the intel driver enabled and/or installed. How did you install Ubuntu? And what happens if you backup and then delete your Xorg.conf?
 
[FONT=Batang][SIZE=3]I was given the laptop with it installed. I have since booted from the live CD. When I do this, the purple screen comes up and then goes black, it stays this way (the backlight is on). When I boot with a VGA monitor connected both screens go black (no backlight). When I boot and let the purple screen disappear and then plug the VGA monitor, the external monitor works.[/SIZE][/FONT]
[SIZE=3][FONT=Batang]          With the external monitor working I open the monitors program and it displayed both the external monitor and my laptop screen but it was picking both up as external and the laptop screen was black (backlight on). Visual effects worked perfectly. With this in mind I assume the person who installed Ubuntu seen the black screen and forced it into a certain mode causing no graphics drivers to be installed.[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]If I delete the xorg.conf file it says something failed and then lunches in low graphics mode (which is what it runs in anyway!).[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]I'd be very grateful if you could help me fix this![/SIZE][/FONT]

---

### Post by krazyd on 2010-08-18
To be honest, it's a bit complicated to debug something like this via a forum :)

Since neither of us know what setting/configuration has been changed from default, I'd recommend just backing up your $HOME and reinstalling.

---

### Post by JJ452 on 2010-08-19
> **krazyd said:**
> To be honest, it's a bit complicated to debug something like this via a forum :)

Since neither of us know what setting/configuration has been changed from default, I'd recommend just backing up your $HOME and reinstalling.

That was the plan until I found out the laptop screen doesn't work out of the box! Maybe if I post the live CD's xorg.conf file (With working ports and graphics) and my current settings (working laptop screen) maybe we could mix them to get it working?

---

### Post by JJ452 on 2010-08-22
Here is my xorg.conf file:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

I wasn't sure where the live CD's config file was (it's a script?) but the only problem with it is my laptop screen is seen as an external screen and it is black.

---

### Post by JJ452 on 2010-09-04
I reinstalled 10.04 and it didn't work but then I installed the beta of 10.10 and it works flawlessly! I love Ubuntu! Thanks for trying to help anyway.

---

### Post by st0kes on 2010-09-10
> **JJ452 said:**
> Here is my xorg.conf file:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

I wasn't sure where the live CD's config file was (it's a script?) but the only problem with it is my laptop screen is seen as an external screen and it is black.

Thanks for posting this. My xserver had completely died because of the maverick upgrade, at least now I have vesa graphics again. 

Is this the best we can get for the moment with this laptop?

---

### Post by JJ452 on 2010-09-12
> **st0kes said:**
> Thanks for posting this. My xserver had completely died because of the maverick upgrade, at least now I have vesa graphics again. 

Is this the best we can get for the moment with this laptop?

I did a fresh install of 10.10 beta and the laptop runs great with all the graphics options available and external monitors working fine. I suggest you reinstall Ubuntu with the beta instead of doing an update if you want the graphics (or wait until October for the release).

---

### Post by st0kes on 2010-09-13
Hmm ... doing a rebuild is not convenient for me ...

Can you post your xorg.conf since you did your rebuild (if you have one)? I want to try and tinker with mine a little more before going down that route.

---

### Post by Tuliku on 2010-09-24
No triumph here..
Elitebook 8440p, intel graphics card, i5 520 processor

- 10.04, installation is only possible with using a external screen. Although i googled and found several instructions on how to make the main screen of the laptop work, it does not work for this one, most likely cause everyone else has the nvidea graphics card.

- 10.10 beta, when booting up the installation, it stops with an error message that the keyboard is unknown..?

- 9.10 Installation goes great, and boots up perfectly, but once on the main screen, after 5 seconds whole laptop freezes.
Booting up with command line, but the log files show nothing useful.

What to do…?

---

### Post by Tuliku on 2010-10-01
So... i made the 9.10 work, by installing it, boot up in command line, update every package, latest kernels, and then it works fine.

This morning i got courages, and used the option to upgrade to 10.04.. I though it will download tall the latest stuff as well, so it might work..
Took a small hour, and result is that it works again only on a external screen.
Also trying these drivers, it did not help sadly enough:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

if anyone has an idea... it would be greatly appreciated.

---

### Post by krazyd on 2010-10-03
wait for the new release (less than a week!) and try an alternative (not GUI/livecd) install.

---

### Post by AngiolettoNero on 2011-01-21
Hi!
I'm an Italian boy. I do not speak English very well... but I'm in this topic because I have the same problem on the same NoteBook.

I would to install Ubuntu 10.10 on my HP EliteBook 8440p i5 and Nvidia graphic but the istallation has the black screen... I can't see anything.
I boot the Ubuntu live with USB driver, with CD and DVD x64... I tested Linux Mint 10 too but nothing. Always the same problem.

What should I do to install correctly Ubuntu Maverick?

Thanks to all, Roberto from Italy.

---

