---
title: "Changing kernel versions"
date: 2008-11-09
forum: General Help
---

### Post by warbread on 2008-11-09
Long story short: I'm using Intrepid with - mostly - success.  However, I need to use a real time kernel and 2.6.27-3 sucks ferociously. 2.6.24-21 is in the repos, and I have booted into it.  It seems, though, that alsa has now decided to stop working.entirely.  It works in 27-3-rt and the generic kernel.  My sound card is not being detected at all.

What do I do from here?  Is there some other configuration that needs to be done when booting to an alternate kernel version than just adding the appropriate information to menu.lst?

---

### Post by sdennie on 2008-11-09
Generally, no, there is no extra configuration for installing a new kernel.  However, it's possible that the 2.6.24 kernel simply doesn't have support for your sound card.  One solution would be to grab the latest ALSA drivers from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and then build and install them while running the 2.6.24 kernel (it's possible to then get the drivers to load without rebooting but, probably easiest to reboot).

---

### Post by warbread on 2008-11-09
Well, 2.6.24-rt worked in Hardy, and the version I got was straight from the Hardy repos.  Still, I don't know what else could be so different to cause my problem.  I will try building drivers from source later when I wake up.

---

