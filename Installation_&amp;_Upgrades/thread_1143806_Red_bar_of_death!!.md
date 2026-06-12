---
title: "Red bar of death!!"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by EvanKroske on 2009-04-30
I was running Intrepid Ibex 8.10 until I tried to upgrade to Jaunty 9.04 through the gui package manager; now I'm not running anything except Vista. The only warning I got during installation was an error saying that libphoto couldn't be installed properly. Apparently that was a pretty serious error, because the installer then ran dpkg --configure -n or something like that.

I shut down the computer (it didn't automatically restart after the installation), and when I tried to start it back up, it didn't work. I selected the kernel I wanted (Jaunty 9.04) and it started booting. The progress bar appeared and filled up, then things started getting weird. The loading cursor appeared in the center of the screen and a thin red bar materialized about a centimeter from the top of the black screen. The screen alternated between blank black and the cursor screen several times; sometimes without the red bar. After about ten repetitions, the screen became fixed with the red bar and the cursor and stopped changing. It never got past that step.

Even when I try to boot up one of the older kernels, I get the same broken boot sequence (I get the kernel select screen because I have Vista installed, too.) I don't think this is a problem I can handle, so I'd like to know how I can revert to Intrepid without fully booting up. Thanks.

---

### Post by Mark Phelps on 2009-04-30
> **EvanKroske said:**
> ... so I'd like to know how I can revert to Intrepid without fully booting up. Thanks.

Sorry to hear about your upgrade problems.  9.04 seems to be producing a lot more than its share of such problems (which is why we generally recommend against doing an upgrade).

As to reverting, sorry (again), there's no simple way to do that because an upgrade not only replaces packages it also removes them.

---

