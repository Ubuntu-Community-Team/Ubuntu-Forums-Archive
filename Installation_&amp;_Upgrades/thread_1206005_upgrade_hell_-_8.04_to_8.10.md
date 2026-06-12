---
title: "upgrade hell - 8.04 to 8.10"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2009-07-06
Well, the automatic upgrade was broken for me.

Yes, I was all up-to-date first.

Still two errors popped up:

"the upgrade will continue but the 'libpam0g' package may be in a not working state.  Please consider submitting a bug report about it. 
subprocess post-installation script returned error status 2".


followed by

"the upgrade will continue but the '/var/cache/apt/archives/cups-pdf-2.4.8-ubuntu1+i386.deb' package may be in a not working state.  Please consider submitting a bug report about it. 
predependency problem".

A little while later it decided it couldn't go on and started reversing itself after bringing up my browser and trying to submit bug reports.

The rollback did not leave me in the previous state either.

Fortunately I had made a full-disk backup.

Well, the heck with that.  I'm tired of googling for help and finding a bunch of happy-path HOWTOs that show a bunch of screen shots when all goes well.  (when all goes well, such HOWTOs aren't necessary!) The only reason I want to go to 8.10 is to go to 9.04.  But if it's that much trouble ...

perhaps I should consider installing 9.04 on a reformatted drive and then moving over my "stuff".  What's the easiest way to do that?  Almost all  my "stuff" is in my home directory.  And I've done lots of apt-gets over the years that I would like to somehow be able to replicate without a lot of fuss and bother.  Is there an easy way to get all that into a script that I can run post install?

Unless someone can point to how to get over these particular errors so that an automatic upgrade would have a reasonable chance of succeeding.

---

### Post by elitenoobboy on 2009-07-06
I don't think I can help you much on the upgrade problem. The full version upgrade has never worked to well for me. If you do want to try to fix it however, I recommend trying to upgrade with synaptic instead of the normal ubuntu updater, especially after a broken upgrade.

If you want to do a full install (which is usually better from my viewpoint; it makes things faster and more reliable), then backing up and restoring your home directory (be sure to include all of the user settings, usually stored in the hidden ".*" directories) would be the way to go. I am not aware of any script that will reinstall the apps themselves, however, you won't have to reconfig them once you copy over all of the user config setting directories.

---

### Post by stevecoh1 on 2009-07-09
> **elitenoobboy said:**
> If you want to do a full install (which is usually better from my viewpoint; it makes things faster and more reliable), 

You're right!  The new install WAS faster than trying to debug all the goofiness.  I was back up and running in 3 hours.

---

