---
title: "Power shut down while upgrading from 8.10 to 9.04"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by beakdan on 2009-05-15
Been lurking for a while, and made use of a lot of great info here.  This is my first real post, though.

So, I was upgrading from Intrepid Ibex to Jaunty Jackalope- I had downloaded all the packages, and installation was nearly complete, when the power plug jiggled loose (I'm working on that problem, too).  The system had not reached the cleanup phase.

I plugged it back in and restarted; the splash screen and login screen were both the Jaunty version.  However, I never saw my desktop or menu bars.  So something is obviously very confused.

My data is safe; I have a second internal HD that I back up to periodically using rsync.  I can even boot from it if I use the oh-so-savvy technique of swapping the cables (I could probably change the boot drive, too, but this works).

I'm not sure what the best option now is.  I am hoping it's possible to fix this without downloading all the packages again (which took ~4 hrs at my connection speed), but I can certainly do that.  I also have a 8.10 live CD handy.

Any suggestions?

Dan

---

### Post by milton1 on 2009-05-15
Can you get a terminal up? If so, try this:
```
sudo dpkg --configure -a 
```

---

### Post by beakdan on 2009-05-15
From the login screen, I was able to select the option to change my session to "Failsafe Terminal".  I then ran the dpkg command and now the system seems to be fine.

I'll keep an eye on it for the next few days, but this seems like a fix.

Thanks!

Dan

---

