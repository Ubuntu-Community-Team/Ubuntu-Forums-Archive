---
title: "autofixing low-graphics mode after upgrade to karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by QplQyer on 2009-11-01
Hi,

After upgrading to Karmic I have the following problem: most of the time I boot into Kubuntu, right after I see the NVIDIA splashscreen and kdm should start, Kubuntu shows a message stating that it is started in low-graphics mode due to it not being able to detect my input and videosettings.  It then offers me the options of booting in low-graphics mode, fixing the problem, or spawning a shell.  Now, most of the time, when I choose shell and I try to login, kdm immediately starts (while I'm typing the username or passwd) and shows up properly, without any low-graphics mode error.  I can then login and everything works flawlessly.  Anyone has an idea how I could fix it?

I am running:

- Karmic Koala 9.10, upgraded from 9.04
- Proprietary nvidia-drivers, installed by hand after the update, version 190.42
- Kernel 2.6.31-14-generic

I already tried to run nvidia-settings and save the settings there to my xorg.conf, added nvidia to autoloading modules and disabling the nv modules, but all to no avail.

---

### Post by ErikDeBruijn on 2009-11-09
I've had the same problem (also NVIDIA). Already had this under jaunty. Ashamed of myself, because I mitigated the problem by keeping the computer on during the night most of the times. I've tried a lot of things but I'm still in the dark why I get this failsafe mode while a /etc/init.d/kdm restart solves my problem. Doing this from a startup script didn't work though, so I need to get into a terminal and run it manually before I can use my computer. I was hoping that during the upgrade to Karmic, this issue would finally be solved. Now I really want to give it another try to prevent 50 Watts consumption over half a year.

Any pointers where I could look?

---

### Post by pescez on 2009-11-15
same problem here, waiting for answers. anyway, hitting the Cancel button in the low-res window brings to shell and after a couple of seconds you get KDM screen.
same situation as above karmic upgraded from jaunty
nvidia 185

---

### Post by QplQyer on 2009-11-15
My problem is fixed after the latest ubuntu-updates with the new 2.6.31-15 kernel.

---

### Post by DaleCooper82 on 2009-11-18
Same here! Yupeee! 

Enable "proposed" repos and get 2.6.31-15 kernel, there is XOrg update as well. All works now and am happy! Good job.

---

