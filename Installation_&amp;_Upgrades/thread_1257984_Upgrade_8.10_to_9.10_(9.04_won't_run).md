---
title: "Upgrade 8.10 to 9.10 (9.04 won't run)"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by ZachMitchell on 2009-09-04
Greetings!

I'd really like to upgrade my system to 9.10 due to the fact 9.04 refuses to run on my computer. (Whether I use the live cd or upgrade it with the update manager.) I'd like to use 9.10 because I tested the live cd and it works perfectly with my system but I have a triple boot system. Is there any possible way to upgrade my system to 9.10, and if not will doing a clean install of it see my Windows partitions and keep them in GRUB?

By the way, I've done some research and it seems that everyone that owns a XFX GeForce 8200 mother board has issues with 9.04.

---

### Post by QIII on 2009-09-04
What do you mean by "refuses to run"?

It looks like you can use the restricted drivers in both Jaunty and Karmic.

[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)

Be aware that Karmic is still an Alpha  (Alpha 5) and is not recommended for production.  Also, the menu.list has gone away on a clean install, there are some things you have to work around to get it to recognize other OSs (os-prober has to be installed, for one) and the old menu.lst is gone and it is not recommended that you change the new config file at all.  (You probably won't even be able to using sudo.)  Using the old menu.lst in "legacy" mode may have some issues, and it looks like a bit of work to update to GRUB2 from that state.

I would recommend against using Karmic for the moment.  It'll be out in a month, anyway.  Wait for the release version.

---

### Post by ronparent on 2009-09-04
Try running 9.04 with noapic and/or nolapic.

---

### Post by ZachMitchell on 2009-09-04
It experiences multiple errors and will not boot. I'm constantly using my computer for work and rarely have the time to mess around with it which is why I think just doing a clean install of 9.10 would be the best way to go. I really don't have time to try and work out the errors in 9.04 just to prepare it to be upgraded to a different version. I had it running once but it took a lot of tweaking, which unfortunately I don't have time for. Gotta bring home the bacon. :)

So I guess now the question is if I do a clean install over the hard drive that (only) Ubuntu is on will it detect my other operating systems for GRUB like a normal clean install would?

---

### Post by QIII on 2009-09-05
A clean install of 9.10 (Alpha 5) would be inadvisable.

There are significant changes, like the use of GRUB2, that currently require some work-arounds to get it to let you able to boot to your other OSs.

If you are interested, there is a discussion on Launchpad.

[https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/402795](https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/402795)

This describes the process that I used to get my dual boot Karmic testing machine to give me the option to boot to Windows.  This will be addressed before the final release, but my last download of Alpha 5 a few days ago still presented the same problem.

So, as strange as it may sound, I would recommend going back to Intrepid if you are having issues with Jaunty.

---

