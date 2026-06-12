---
title: "New gfx card but no graphics"
date: 2008-07-15
forum: General Help
---

### Post by Scarlett on 2008-07-15
I got an Nvidia 280 GTX and my resolution reverted to 600 x 800.  Nvidia has just put out a driver for this (117.13-pkg2) and since I couldn't find a way to make the restricted drivers work I tried to compile their driver into the kernel.  (Sorry if that's not the right terminology, I'm not really sure.)  Anyway, I exited out of the window manger and sudo sh'd the package from Nvidia and everything looked like it was going ok.  

When it was done I got the logon screen and it flickered to my desktop for a second and then it just turned white.  I can see my cursor but everything else is white.  Now I'd just be happy to get my resolution back to 600 x 800 so I can see what I'm doing.  I made a backup of xorg.conf but I'm sort of lost with just the command line.  Help?

---

### Post by Scarlett on 2008-07-15
Ok, I managed to restore my backup of xorg.conf and after rebooting I can now get to my desktop and the resolution looks good.  Yay, progress!  Conky shows up.  Nice!  

BUT... I have no menu bar.  Grrr!  How do I get that back?

---

### Post by johnhalsted on 2008-07-16
i had the same problem, i got the new graphics card, tried to use envy to install the suitable drivers, but it failed, i then got the drivers from nvidia compiled and installed.

after i restarted awfully bad colors flickering etc... just waiting for a possible solution to appear or even new drivers

---

### Post by ellgor on 2008-07-16
Hi,

You could try this,check to see if you have a package called nvidia-settings (synaptic) install if not, then open a terminal and type in:

gksudo nvidia-sttings

a new window will open with the settings for you to adjust, hope this helps.

Regards, Ellgor.

---

### Post by jonian_g on 2008-07-16
Installing the driver from the nvidia website is a really bad idea.
The best way to do it is with the Restricted Drivers Manager or Envy (has newer versions of the driver).

Why it's a bad idea? Because every time you get a kernel update (three times till now after Hardy released), you have to reinstall the driver.
If Envy or Restricted Drivers Manager fail, try again...

---

