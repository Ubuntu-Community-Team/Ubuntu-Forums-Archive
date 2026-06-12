---
title: "Is there anyway to do a complete reinstall of X/mesa/video?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by kapauldo on 2009-08-21
Hi -

I have an emachines D260 with an ATI Radeon X1200 card.  I installed Jaunty 64 with no problems, and everything worked great, except there was a known bug with firefox being slow.  So I followed directions to fix it, and my screen got filled with garbage.  Now, for the past few weeks, I've been living with generic video drivers, which I somehow managed to install.  I have no 3D access, and glxinfo gives me this:

Xlib:  extension "GLX" missing on display ":0.0".

I've tried to install the ATI drivers, I've tried to install the open source drivers, no matter what I do, i get this same problem.  My xorg.conf file is this:


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


I'm at my wits end.  Is there any way to simply reinstall all of the original ATI drivers and Mesa drivers, etc. that Jaunty initially detected?  

Also, I read that one thing I could do is install the "Restricted Hardware Drivers" but that's not a menu option for me, so I don't know if it was moved in Jaunty or it has to be manually installed.

Anyway, if someone can help me get my ATI card working with the right drivers, I'd appreciate it.

Thanks,
Kevin

---

### Post by jwaffolter on 2009-08-21
in the terminal run
sudo apt-get install envyng-core envyng-qt

after thats done open Applications->System Tools->Envyng
and choose the ati driver, this will install and configure it properly

---

### Post by kapauldo on 2009-08-21
> **jwaffolter said:**
> in the terminal run
sudo apt-get install envyng-core envyng-qt

after thats done open Applications->System Tools->Envyng
and choose the ati driver, this will install and configure it properly

ok, i did this, now the system boots, blinks 3 times, and gives me a black screen with some garbled graphics on the top of the screen.  can you tell me how to get back to the basic generic config from the terminal (i can't startup X), OR can you tell me how to launch X with a generic config?

thanks,
kevin

---

### Post by jwaffolter on 2009-08-21
look at the /etc/X11 directory and find xorg.conf backup and replace xorg.conf with it
the backups are typically named xorg.conf followed by a date string

---

### Post by kapauldo on 2009-08-21
thanks, but that didn't work (i tried that before reading your reply).  what i wound up doing was to install the ATI 9.7 driver, which i had tried earlier and knew it wouldn't work, then reinstalled it.  i now have my graphics back to some generic driver.  any other ideas how to fix GLX/opengl?

---

### Post by jwaffolter on 2009-08-21
all i have left to suggest is that you check to see that all the glx/opengl libraries are correctly installed...as well as their corresponding dev packages,

---

