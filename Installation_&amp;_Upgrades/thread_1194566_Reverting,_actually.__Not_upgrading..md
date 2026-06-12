---
title: "Reverting, actually.  Not upgrading."
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Philsco on 2009-06-22
I'm having more issues with Jaunty than I care to deal with at the time, and I'd like to switch back to Intrepid while saving as much of the work I've done to get Ubuntu to where it is (Wine tweaking, aps installed, hardware work-arounds I've put in place, etc).  What steps should I follow to maintain as much of my current Ubuntu set-up as I can while going back to Intrepid?

I just [very] recently upgraded to Jaunty.

---

### Post by Scunizi on 2009-06-22
There's only one way to go back, reinstall.  If your /home is in a seperate partition that helps a bunch as you can keep it intact.  You may want to copy off all the hidden files and directories (anything preceeded with a "." dot.  After copying them off delete them as they may not play well with the new "older" system.  Once the reinstall has been done, reinstall those programs, like wine, that you installed directly.  Add back, one by one, the .<file/directories> you saved, testing them in the process to make sure that they don't mess with your system.  If those file/directories are duplicates of what the new install put on the drive then prior to moving the saved files, rename the new ones to something like .<file/directory.backup> just in case there are issues and you need to put them back into play.

Don't fool yourself, there is no perfect way to revert and it's always fraught with headaches.  For those specialized configurations (wine etc) you may just have to rebuild the configs.

---

### Post by Philsco on 2009-06-22
Well, I was afraid the answer was going to be something like that, but it was expected.

Luckily I have a 1TB 2nd external HDD that I can copy all of those things to.  Thanks for the advice, dude.

---

### Post by Mark Phelps on 2009-06-23
Actually, the answer we generally provide is that there is no way to do a rollback to a previous version -- because of all the problems you're likely to encounter in the process.

And true, while MOST of your customization and other such stuff is somewhere under /home, there are also customizations in other places, such as /etc (fstab file and others), boot (grub menu.lst file and others), and other things such as printer drivers (and ppd files).

And that's NOT including anything you built from source and installed to /usr/bin or /usr/local/bin or usr/sbin.

And, anything else you did -- like installing NDISWrapper to get wireless working.

So, really, the list can go on ... and on ... and on.

What I've done is to have two versions of Ubuntu installed -- the most current, and the one previous. When it's time to upgrade, I wipe the oldest version, and install using the same partitions.  That keeps all my customizations intact for the (new) old version, plus it gives me a working version to use while I take my time replicating my customizations to the new version.

---

