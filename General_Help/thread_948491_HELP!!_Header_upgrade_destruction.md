---
title: "HELP!! Header upgrade destruction"
date: 2008-10-15
forum: General Help
---

### Post by Wickd on 2008-10-15
Hi there!

I have now recently updated my kernel headers via Update Manager! From 2.6.24-19 to 2.6.24.21. Both generic

After I installed this, my Xserver did not want to load my old settings an ran Ubuntu in 640x480 resolution. When I try to run nvidia-settings, It informs me: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

**I then attempted to run the nvidia-xconfig with the following results**:

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

------

Also the mysqld does not want to startup.


I have a Nvidia 8500GT 512mb graphics adapter

Thanks in advance

---

### Post by Wickd on 2008-10-15
Some more issues: My Virtual Box also does not want to load, and rythmbox completely exits as soon as you listened to more than 2 songs.

Ok, I recompiled the Virtualbox Kernel and that did the trick for virtualbox, does this mean that I will have to do the same for all my applications? If that is the case how does a kernel header upgrade work?

Please someone help me

---

### Post by Wickd on 2008-10-15
Nevermind, found the solution, just reinstalled some apps and voila

---

