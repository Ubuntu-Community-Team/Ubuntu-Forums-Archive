---
title: "Fix for texture corruption on Dell D620/ Nvidia 7300"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by EtanSivad on 2007-06-14
If you have an Nvidia card with shared or "Turbo" memory (The 7300 for example has 64 mbs of vram and shares 192mb of system memory) and a dual core CPU, you'll get texture corruption under Nvidia binary that Ubuntu uses by default.  See [here]("http://ubuntuforums.org/showthread.php?t=436629") for examples and [here]("http://www.nvnews.net/vbulletin/showthread.php?t=91641&page=2") for details on the issue.


Fortunately the latest 100.14.09 nvidia driver fixes the issue, but it's a bugger to install (For me anyway.)  So here's a quick guide to manually installing the driver.  Which, word of caution, I'd only bother to do *IF* you're getting texture corruption.  The install is a little obnoxious.  



First you'll need to get the latest linux driver from Nvidia [URL="http://www.nvidia.com/object/linux_display_ia32_100.14.09.html"]here:
[/URL]

Download the file to your home directory or someplace where you can find it again of course.  


Switch to terminal 1 Crtl+Alt+F1


Shutdown Gnome

> sudo /etc/init.d/gdm stop

(Or KDE)

> sudo /etc/init.d/kdm stop

Uninstall the ubuntu driver

> sudo aptitude remove nvidia-glx nvidia-kernel-common



There's a bug in the uninstall that leaves one file behind, you can read about it [here.]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217") 

In any event, remove the file manually.

> sudo rm /lib/linux-restricted-modules/.nvidia_new_installed


Next disable the NV driver so ubuntu won't load it:

> sudo nano /etc/default/linux-restricted-modules-common 

Go down and change the DISABLED_MODULES="" to read.

> DISABLED_MODULES="nv"

Save and exit.
Finally, install the new driver:

> sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run


Answer yes to everything and let it configure your /etc/X11/xorg.conf


Once it says everything is configured, restart gnome/KDE.


> sudo /etc/init.d/gdm start


(Or KDE)


> sudo /etc/init.d/kdm start


Then hit Crtl+Alt+F7 to switch back to your Gnome session.

You might need to reboot, but I didn't have to.  Hope that helps!

-Etan

---

### Post by ganyx on 2007-07-07
It does not work with my AMD 64 CPU. But Thank you anyway!

---

