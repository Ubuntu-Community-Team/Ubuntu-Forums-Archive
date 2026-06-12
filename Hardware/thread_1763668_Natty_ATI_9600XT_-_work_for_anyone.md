---
title: "Natty ATI 9600XT - work for anyone?"
date: 2011-05-20
forum: Hardware
---

### Post by ofb on 2011-05-20
Having just an ugly time with this one. It'd be useful to know if anyone has made this card work in 11.04. (and if so, how?)

I've purged yesterday's attempts using this advice,
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

That seems to put me back where I was at install: glxgears actually works and shows '424 frames in 5.0 seconds = 84.744 FPS', and nothing shows up under Sys>Admin>Additional Drivers.

If I install the fglrx packages from Synaptic, glxgears is busted and nothing shows up under Additional Drivers. I get menu entries for Catalyst, but clicking them just gets a dialog about missing driver.

Trying to install the recommended driver from ATI was a multi-hour trip down the rabbit hole. Booting into tty1, booting into no monitor signal, booting into a driver listed under 'Additional Drivers' but refusing to install. Saw everything but success. It was the proverbial brown acid.

FWIW, this card had been working okay on a different motherboard and under Lucid with the default driver. glxgears output was about 12000, and nothing was listed under Hardware Drivers.


some current outputs:

```


o@bluefish:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AR [Radeon 9600] [1002:4152]


o@bluefish:~$ LIBGL_DEBUG=verbose glxinfo | head
libGL: OpenDriver: trying /usr/lib/dri/tls/r300_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/o/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/o/.drirc: No such file or directory.
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 


o@bluefish:~$ cat /etc/X11/xorg.cong
cat: /etc/X11/xorg.cong: No such file or directory


o@bluefish:~$ fglrxinfo
fglrxinfo: command not found


```

---

### Post by stangbang on 2011-05-21
the fglrx driver no longer works with this card. You would have to use version 9.3 which will not work with current kernels. You need to use the open source radeon driver.

---

### Post by ofb on 2011-05-21
Thank you.

Am I running the open source radeon driver now? And are those lines above with " Can't open configuration" something that can and should be fixed?

It's a little odd to see the card go from 12000 down to 450 between boxes, so I'm curious.


====

Details for people who search the forums:

What stangbang says is exactly correct.

The longer version is ATI dropped support for legacy Radeon cards as of their 9.4 driver.

9.3 remains available, and is what ATI gives you when you go to their site and select the choices for your card & OS.

However xserver was upgraded to 1.6 as of ubuntu 9.04 jaunty, so ATI's 9.3 stopped being usable to essentially everyone.*

It'd be an awful good idea for ATI to mention this on that page, but meanwhile, _you don't want that driver_. You are stuck with the default open source driver. Typically these don't do very well in 3D. So really what you want to do now is just stop messing with it, and go get a Nvidia card.

Nvidia legacy support on Linux has had its ups and downs, but the ATI legacy support is essentially non-existent. Try Nvidia AGP cards instead.


... to be entirely complete I should mention there is also the open source xorg-edge PPA driver. All it did for me is make the glxgears gears flash in different primary colours. But the irrepressibly curious may want to try it anyway.


*You /could/ dig out the old archived Ubuntu distros and set up an offline gaming box using your ATI card, but again that's just for the irrepressibly curious. Not something a normal well-adjusted person should consider. (Yes, I am probably going to do that. It's a dual-boot box with w98 games on one side and ut2k4 on the linux.)

I may have gotten the odd version number wrong above because I've just pounded this out from memory, but it's essentially correct. Hopefully it'll save a few people from the rabbit hole.

---

### Post by stangbang on 2011-05-21
The reason for your FPS being so low is because your monitor is most likely set to 85Hz. This is because glxgears is using vsync.


Also I would not worry about the debug errors.

---

### Post by ofb on 2011-05-21
Thanks again.

The physical monitor & refresh were the same in both cases. Perhaps the card just doesn't like this new old motherboard. Ah well, not worth fussing over.

---

### Post by Blasphemist on 2011-05-22
This is for installing the open source drivers.
[https://help.ubuntu.com/community/RadeonDriver#Require](https://help.ubuntu.com/community/RadeonDriver#Require) Natty/11.04 and Modesetting Only

---

