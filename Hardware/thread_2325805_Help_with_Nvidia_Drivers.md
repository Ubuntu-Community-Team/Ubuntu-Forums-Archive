---
title: "Help with Nvidia Drivers"
date: 2016-05-25
forum: Hardware
---

### Post by Jvinas on 2016-05-25
Hi Guys, i new here and i want to install lubuntu in my old pc but i having issues with my GPU(Geforce 4 MX 4000).
The nouveau is not working, when i put my USB with lubuntu and choose to go to the live desktop,my screen get stuck.
I fixed this problem adding the following boot parameters : nomodeset and nouveau.noaccel=1. So i finally get access to the live desktop ,i need to install the system and install the nvidia 96.xx.xx drivers or an alternative for them and remove nouveau.
And I neeed help. 
Thanks Guys.

PC Specs 

Intel Pentium 4 3.20 GHz( I think )
1.5 GB RAM
120 GB Hard Drive
Nvidia Geforce 4 MX 4000 GPU

---

### Post by ajgreeny on 2016-05-25
If those boot options work for you go ahead and install and on the reboot into the installed OS you will need to hold shift at power-on which will make the grub menu appear.

Whilst the top item in grub is highlighted hit "E" key to edit the entry and then use cursor keys to go down to the line that has **quiet splash** near the end.  Add the same boot options to that line directly after **quiet splash** then hit F10 to boot with those options (for that boot only).  This should get you to a GUI though it will probably be low resolution.  From there install the nvidia driver that is best for your system's graphics card, but don't worry about removing the nouveau driver as it will not be used if an nvidia one is available as far as I'm aware.

You should now be able to reboot and forget about the boot options as the machine ought to now boot to a GUI at the proper resolution.

Good Luck!

---

### Post by $yl9pAR%t on 2016-05-25
This driver (nvidia-96) is not supported in *buntu 16.04, if I remember right it was not supported in *buntu 14.04 either. Probably you have a chance to use it in *buntu 12.04.1, but my recommendation is *buntu 16.04 with nouveau because support for 12.04 is ending in less than 1 year.

---

### Post by mörgæs on 2016-05-26
[This post]("http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687") may or may not work for a Geforce 4. 

Though, regardless of drivers and settings I suggest that you look for a better graphics card. You have one of the strongest processors within the Pentium 4 family but the graphics card is a bottleneck.

---

