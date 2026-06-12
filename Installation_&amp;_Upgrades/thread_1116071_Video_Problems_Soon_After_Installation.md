---
title: "Video Problems Soon After Installation"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by RonnieV on 2009-04-04
I've been attempting to install Ubuntu 8.10 onto a Dell GX110 with 256 RAM for sometime with little success. 

Ubuntu seems to install properly from a live CD. Following installation and the requested reboot, everything seems to function properly. However, after I shutdown and reboot, my display becomes unviewable.  In order to troubleshoot, I've not installed updates.  The problem definitely occurs before updates are installed.  To add a small bit of additional information, installing the updates does not fix or prevent the problem.  

This Dell has an Intel motherboard with built in graphics and an Intel 810E chipset.

Has anyone else experienced this problem and determined the cause or better yet a solution?

---

### Post by utnubuuser on 2009-04-04
Hi - I've had a similar issue with the new Debian Lenny on a older laptop with only 256 megs ram,  the only way I got it fixed was by going through the recovery screen, then> sudo apt-get remove xserver-xorg-core --purgethen> sudo apt-get install xserver-xorg-corereboot

I suppose your tried getting at the command line with ctrl+alt+F1, then > sudo dpkg-reconfigure xserver-xorg
back to graphical with ctrl+alt+F7

---

### Post by RonnieV on 2009-04-04
Thanks for your reply. I should have included that while I'm an experienced Windows user, I'm fairly new with linux.

I've used the command line in linux and should be able to execute the commands you suggested, but would really appreciate knowing what you think may be going on and the solution being applied by your suggested commands.  It seems so odd to me that Ubuntu seems to display everything properly after the OS installation but then seems to "forget" a setting or something once the machine is shutdown.

Thanks, again for your earlier post and the additional comments I hope you share.

---

