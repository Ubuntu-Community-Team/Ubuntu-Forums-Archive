---
title: "Install Ubuntu on an External Monitor only."
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by Danzarak on 2008-12-12
Hello,

I'm relatively new to Ubuntu (only on 2 of my 3 machines.)  I have a Sony Vaio PCG-8W1M laptop which I use as a media center.  I've been using it for a couple of years with Windows Media Center, and I now want to flatten it and install Intrepid + MythTV.

My problem is this... the monitor on the laptop is totally broken.  This has been fine, as it has an HDMI out which I use to output to my TV, once windows has loaded.

However, neither the HDMI or external VGA outs on the laptop display the bios or boot process.  I was hoping that if I insert the standard Ubuntu install disk, that when it got to the install screen, it would dual-output to the external VGA out so I could install.  I know Ubuntu supports multiple monitors once installed - but is there a method I could use to install from an external monitor?

I've so far tried...

Pressing del to get into the bios - no external output.
Pressing FN+F7 (switch output) at all stages of the process - no external output.

Is there any other way to achieve this?  Would I have any more success with the Alternative CD? I've searched the forums but haven't found anything yet.

I have grown to hate Vista which is what is currently installed. Please help me remove it.

Thanks
Danzarak

---

### Post by Danzarak on 2008-12-12
Hi...

I've been reading around this subject, looking for all available options to get this done.  Some people I've found seem to be able to see output on the external monitor during install... am I doing anything wrong?  Is there something I need to press (that I can't see) to initiate the Ubuntu install to a point where it will output to the external monitor?

Additionally - I've been trying to find a guide for preseeding to allow automatic installation.  Could anyone recommend a guide?  If I do manage to install, will Ubuntu automatically be installed in a state where on bootup, it will output on the external monitor?

Thanks again...

Danzarak

---

### Post by linux_tech on 2008-12-12
What type of video do you have?
```
sudo lshw -C video
```

Go to System -> Preferences -> Screen Resolution and check settings there

Run xrandr with no switches.
```
xrandr
```

That should show you to see all the displays hooked up and the resolutions they support.

---

### Post by Danzarak on 2008-12-12
Hi.

Actually... I'm trying to install Ubuntu, so I can't do what you have asked me to do.

However, I do know that the graphic card is an NVidia GO 7600.
Thanks.

---

### Post by Danzarak on 2008-12-12
Hi..

Ok, I'm a little further along now.  Turns out that the CD I'd burned out of 8.10 was faulty.  I reburned at minimum speed, and rebooted with it in the drive.

After a short while, a mirror display of the Live CD install came up on my external monitor - very flickery and distorted, but enough to complete the install.  I was then able to install Ubuntu 8.10.

The first thing that happened was that I need to download 200meg of updates, which I did and installed.

The problem I am now having is that I think it has installed the NVidia display drivers - and when I boot, I can hear it get to the login screen, and it allows me to login... but it now only shows the display on the broken screen, not on the external monitor.

I assume there is something I now have to do on the screen - activate the external monitor I assume - to allow me to use the external monitor.

Does anyone know of a way I can do this using a keyboard shortcut - or a way to go back to the standard drivers, and enable the second monitor before I install the Nvidia drivers?  When it was running with standard drivers only, it only showed a single monitor - and the resolution on the external suggested that it was a clone only.

Thanks,
Danzarak

---

### Post by linux_tech on 2008-12-14
if you're using the external monitor only, try this command:
```
xrandr --output LVDS --same-as VGA
```

Use this command to go back to external only:
```
xrandr --output LVDS --off
```

If you're using the laptop monitor only and the external monitor is plugged in and turned on (but not active), use this command:
```
xrandr --output VGA --same-as LVDS
```

Use this command to go back to laptop only:
```
xrandr --output VGA --off
```


This article explains more on using xrandr or xorg to regulate video choices. I like xrandr because it is dynamic, faster to troubleshoot and usually resolves issue faster.   
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

---

