---
title: "Hardy Heron and Nvidia Geforce FX 5600"
date: 2008-06-18
forum: Hardware
---

### Post by TheZorch on 2008-06-18
I've just installed Ubuntu 8.04 and enabled the Nvidia drivers under Hardware Drivers.  I can get the GLX desktop compositing and effects to work but I have a serious problem with screen resolution.  I have an 8x AGP Nvidia Geforce FX 5600 card and I'm limited by a 640x480 resolution.  According to several sources my card is supposed to be supported by the drivers which Ubuntu downloads from the repos when you enable the driver.  I tried using nvidia-xconfig, Nvidia-Settings, and even tried drivers installed by EnvyNG.  I want to be able to set my resolution to 1024x768.  Is there a tool which will let me change my resolution to one which is not listed in Screen Resolution, or is a config file I can edit to add the resolution setting?  Please help!

---

### Post by Odrodzona-Sarmacja on 2008-06-18
I don't know if I can help you, but... When I configure x server during recovery bootup, then it sets me up with the open source driver for nvidia and not with the "full power on" nvidia-glx-new driver. So I would make sure that xorg uses nvidia-glx-new by reinstalling this driver and rebooting.

However if this above still doesn't help to get more display settings, then I would think about checking up on the driver for my monitor.

If both drivers are set and working and still something doesn't show up, then I would go with installing from repository nvidia-settings package and experimenting with, but only as the last resort.

Good luck!

---

### Post by TheZorch on 2008-06-19
OK, finally fixed it and discovered a big in Hardy at the same time.

The problem **was not** the Nvidia drivers but Hardy itself.  The Screen Resolution applet under the Preferences menu is lacking one important option.  The ability to select which Monitor you have.  The old applet "displayconfig-gtk" from Gutsy is still there but neither listed on the menu nor available to be added to the menu via the Edit Menu option.

After fighting with xfix and xrandr for hours I found a forum which suggest trying displayconfig-gtk.  I did, selected that I had a 1024x768 monitor, and changed my resolution to that resolution.  IT WORKED.  I was then able to turned on Advanced Desktop Effects in the Appearance applet which enabled GLX and now I can enjoy once again Ubuntu's superb full screen zoom and color inversion which is great for my vision problem.

After getting my problem fixed I want to the Ubuntu site and filed a bug report concerning the Screen Resolution applet.  Since it didn't include a option to select your monitor people with me who don't have standard-type VGA monitors will have major problems.  My monitor is a VGA-compatible 21inch Sun Microsystems workstation display I got off Craigslist for free.  I know its not a standard monitor because the PnP feature which normally allows the graphics drivers to identify what the monitor is and what resolutions and refresh rates it can handle is missing from this one.  I tried connecting this monitor to my laptop using Windows Vista, it couldn't figure out what the monitor was and it kept flickering on and off and wouldn't work right.  I tried a regular brand name monitor and it worked perfectly.  So, that is what happened and hopefully someone will see my bug report and make certain that Hardy's Screen Resolution applet is fixed.

---

### Post by neutroniu on 2008-09-22
> **TheZorch said:**
> 
[...] The old applet "**displayconfig-gtk**" from Gutsy is still there but neither listed on the menu nor available to be added to the menu via the Edit Menu option. [...]

Thanks **TheZorch**, this one might not be clean(direct), but did the job for me, finally a tool that does the job.

---

