---
title: "Need help enabling themes etc. Ubuntu 8.04 Dell Latitude D600"
date: 2008-08-16
forum: General Help
---

### Post by Wally_dog on 2008-08-16
Well, I finally made the jump and installed Ubuntu 7.10, then upgraded to 8.04. All this was done on my Dell Latitude D600 laptop. Can anyone point me to a guide that shows me how to enable whatever I need so that I can use Emerald themes? Also, the 3D cube effects etc. would be nice, but all I would really like right now are the Emerald themes. If it helps, I am using a Mobility Radeon 9000 graphics card, and I have not messed with the drivers for it.

If anyone can please help me get this to work, I would be very grateful towards you :)

Thanks for your time & patience,

Wally

---

### Post by ad_267 on 2008-08-16
The sticky in this forum should give you everything you need to know:
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Have you enabled the proprietary drivers by going to System - Administration - Hardware Drivers?

---

### Post by Wally_dog on 2008-08-16
Thank you so much for your response. Before checking the thread you linked, I followed your instructions and went to System -> Administrations -> Hardware Drivers. I entered my root password, and when the box came up, there was nothing in it... is that a problem?

---

### Post by ad_267 on 2008-08-16
> **Wally_dog said:**
> Thank you so much for your response. Before checking the thread you linked, I followed your instructions and went to System -> Administrations -> Hardware Drivers. I entered my root password, and when the box came up, there was nothing in it... is that a problem?

I'm not sure. It could be, or it could be that the drivers are open source and installed by default. I only have experience using the Nvidia drivers. 
Enter this command for an idea of what drivers you're using:
```
glxinfo | head
```

---

### Post by Wally_dog on 2008-08-16
I entered that command in the terminal and got this:

```
mike@mike-laptop:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

```

Please note that I did enter a script I found here that supposedly "skips checks". Once I did that, I tried enabling Desktop Effects, but only 3/4 of my screen appeared horizontally, so I reverted back to the old settings. The other 1/4 of the screen that was not appearing was black. Is there an easy way to repair my Ubuntu install? I was thinking of reinstalling it so that I could start over fresh without having messed up xorg or whatever those files are. Is there an easy way to do that? I can use Windows XP (I have it set up as a dual-boot right now).

---

### Post by ad_267 on 2008-08-16
If you just enabled compiz and then disabled it there shouldn't have been any changes to your xorg settings. Try just logging out and back in again. You can reconfigure X without reinstalling if you need to.

It might be a good idea to post in the [Multimedia and Video]("http://ubuntuforums.org/forumdisplay.php?f=334") forum for help with your video card. I found this page [BinaryDriverHowtoATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") but it doesn't look like your card is supported.

---

### Post by Wally_dog on 2008-08-16
No, I just meant that I had entered a LOT of stuff in Terminal that didn't end up working somewhere down the road (one or two commands would do stuff, then I would enter one and it would fail etc.). What do you suggest I do??? All I really want is for emerald to work.

---

### Post by ad_267 on 2008-08-16
Well if you have modified a lot of settings for xorg you can enter "dpkg-reconfigure -phigh xserver-xorg" into a terminal to reconfigure xorg to default values.

If there's other packages you've installed you can uninstall them using synaptic or "apt-get purge package_name"

---

### Post by Wally_dog on 2008-08-16
I entered that (you forgot to put "sudo" in front of the command), and then it gives me this:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080816224020

```

I got a LOT of errors like that when entering commands.

---

### Post by ad_267 on 2008-08-16
That's not an error. That's just telling you that it's backing up the old configuration.

---

### Post by Wally_dog on 2008-08-17
Oh... well I am going to reinstall Ubuntu again so I can try this over. Everytime I reboot and login, I get the "Your last session lasted less than 10 seconds" message, and the only way to fix it is by using the Last Xscript session (or whatever that is called).

---

### Post by pelled on 2008-10-05
Hi,

I've recently upgraded my Dell Latitude D600 from Ubuntu 7.04 to 7.10 and finally to 8.04. In 7.04, I had correct screen resolution (1400x1050) and hardware acceleration, but in 8.04 I got none of these.

After running the command;
# sudo dpkg-reconfigure -phigh xserver-xorg
and rebooting, I now have at least the screen resolution in place (1400x1050 on the laptop and 1280x1024 on my 19" LCD). :)

Still, I don't have hardware acceleration. Any suggestions how to enable that. ](*,)

Regards
Pelle

---

