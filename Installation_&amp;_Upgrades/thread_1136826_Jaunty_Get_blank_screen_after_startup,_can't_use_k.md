---
title: "Jaunty: Get blank screen after startup, can't use keyboard"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by berlinbrown on 2009-04-25
I just upgraded to Jaunty.  I have upgraded in the past and haven't normally had issues.

I did the upgrade.  Most things went fine.  As Ubuntu us starting up, I get the screen with only the Ubuntu logo and then a skinny progress bar. It looks like the system is starting up.

After that, it just goes straight to blank screen and I can't use the keyboard.

First, I am guessing I need some way to go straight to command line without it trying to start X.

Also, at that point I am assuming I need to reconfigure X somehow.  I bet some X server upgrade is causing this issue.

I have an nvidia card and normally I use the nvidia config applications to configure X and the card.  I wonder if that might be an issue.

Any ideas?  I am non-functional right now.

---

### Post by omeomi on 2009-04-25
Got the same problem here. Upgraded from 8.10 and after rebooting Xserver keeps crashing, but I can't access the command line to fix it.

My videocard is a Nvidia 9500gt

---

### Post by sukumade on 2009-04-25
I also had the same issue - I had to use the previous kernel to boot. Even then I am not able to use desktop effects.

---

### Post by mszilard on 2009-05-03
same problem here. i'm using an ati hd4670 card. on my laptop i didn't have any problems with an ati x1250 onboard gpu.

---

### Post by Holden99ca on 2009-05-24
Same issue. Workaround is: you boot into the recovery mode (sorry I forget what GRUB calls it but it's the second option). Then when you get the list of options, just select "resume normal boot". You'll be good to go. Works every time.

---

### Post by fululian on 2009-05-26
And my boot-up is fine, it's just that the desktop simply isn't there - just the wallpaper, no icons, no right-mouse-click. Grafics card is an Nvidia Geforce Go 6200. Any ideas?

---

### Post by bjm442 on 2009-05-26
> **berlinbrown said:**
> I just upgraded to Jaunty.  I have upgraded in the past and haven't normally had issues.

I did the upgrade.  Most things went fine.  As Ubuntu us starting up, I get the screen with only the Ubuntu logo and then a skinny progress bar. It looks like the system is starting up.

After that, it just goes straight to blank screen and I can't use the keyboard.

If I hit esc at boot up I can get to a command line.  From there I'm not sure how I can fix it.

---

### Post by David Headon on 2009-05-26
have installed UbuntuStudio for the third time for various reasons.
I lost my x.org session after enabling the Nvidea  Geforce FX restricted drivers.

Anyone know which is the stable driver to select?
i chose the preferred option. it didn't work!
not crucial to have but would be nice.
Sometimes i use compiz, so i'd like to have it running.

I AM getting real sick of the installer though...

---

### Post by pmorton on 2009-06-12
> it just goes straight to blank screen and I can't use the keyboard.


Has anyone got a solution to this? I'm as stumped with this problem as I've ever been, trying to get a NVIDIA AGP 6200 card to work on an old Compaq Presario. The onboard Intel graphics adaptor and a AGP ATI card fare no better than the NVIDIA.

I can get a rescue command line, and can install the NVIDIA proprietary driver, although it complains that it needs to be compliled under a run level that starts gdm, and that can't be achieved. The driver doesn't work - gdm hangs as soon as the desktop appears.

Sometimes I think with Linux it's one step forward and two back.

---

### Post by thewang767 on 2009-06-12
I have the same problem, Jaunty won't display the GUI after the progress bar. After hitting Esc in the boot menu, I selected the second option of "ubuntu something (kernel)" and went to "Drop root as shell level with networking." Then I reconfigured my xorg.conf settings, rebooted, and was able to see an error message about how my display settings were wrong. My mouse and keyboard still don't work, however.

---

