---
title: "Ubuntu upgrade errors."
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by fraserad on 2009-07-01
Hey, 
Total Linux newb here.
I just installed some updates from the update manager and now my GRUB has 2 ubuntu options to run.  2.6.28-11 and 2.6.28-13.  Is this a new version of linux? and which version should I load?  

At first when i try to boot in the 2.6.28-13 it came up with an error that my graphics werent congfigured properly so I had to reboot.  I did that and now Maya wont work properly because it says there OpenGL isn't configured properly.  

Any help would be appreciated.
Thanks

---

### Post by raymondh on 2009-07-01
> **fraserad said:**
> Hey, 
Total Linux newb here.
I just installed some updates from the update manager and now my GRUB has 2 ubuntu options to run.  2.6.28-11 and 2.6.28-13.  Is this a new version of linux? and which version should I load?  

At first when i try to boot in the 2.6.28-13 it came up with an error that my graphics werent congfigured properly so I had to reboot.  I did that and now Maya wont work properly because it says there OpenGL isn't configured properly.  

Any help would be appreciated.
Thanks

You installed a new kernel 2.28.6-13.  You always have the option to boot any/either kernel.  Given the current status of 28-13, continue to use 28-11 until you get to fix 28-13.


Can you detail more the error/s?

Some thoughts .... 

When you installed 28-11 (or Ubuntu), did you have to install/update any drivers (whether proprietary or open-source)?  If so, you may have to re-install for 28-13 as well (of course, while being booted in 28-13).  Quick check is system > admin > hardware drivers.

Maybe Maya does not work because of dependency problems. Can you access a terminal and try running Maya .... post back out

In the meantime, you can search for and install startupmanager which allows you to set defaults for your boot-up preferences.

---

