---
title: "ATI Open source Drivers or FGLRX (Proprietary.)"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Gekkido on 2009-03-31
Ok.  Here is what I think my problem is.  I'm running a ATI Radeon 3450 HD (In an HP laptop) and whenever I update, the updated kernel leads to a blank, or the screen is just off.  I will see the Ubuntu loading screen, but after that is normally when it happens.  There is also no sound after the booting screen as well.  Then when I re-install I see two errors when I am watching the update installing on the fresh install on for the new kernel again.  It just happens to be the same problem over, and over again.  Could it be the open source drivers trying to kick in over the proprietary drivers?  I'm thinking I should probably un-check the open source drivers in this case.

Does this seem right to anyone that has had this problem before?

I see a lot of people having this problem, and I've tried all their work-arounds, and fixes, and none of them seemed to work for me.  I'm going to try this to see if it works.  If it doesn't, I'll try to take screens of the errors when they pass by.


Just said forget the update, and chose to do everything manually.  Just to get the few things to work that I need to work.

---

### Post by Mark Phelps on 2009-03-31
Have done kernel updates and version updates, both when using open source drivers, and when using ATI drivers.  The first have not posed any problems at all.  As long as the xorg.conf file is not getting overwritten, there's no reason I know why kernel updates should affect your display.

Version updates are a different matter.  During one version (I forget if it was 7.10 -> 8.04 or 8.04 -> 8.10), I suffered the dreaded blank screen after update problem.  I learned this was due to compiz being turned on by default in the new version. My ATI card didn't work well with compiz being turned on.

I removed the compiz packages, force the usage of metacity and was able to get a desktop back.  I was then later able to reinstall the ATI drivers and turn compiz on again without losing the desktop.

---

### Post by Gekkido on 2009-03-31
So saying this.. The next time I do an update.  It would be a good idea to turn off, or un-installing compiz before I restart the computer?

---

### Post by Mark Phelps on 2009-03-31
That's what worked for me.

---

### Post by Gekkido on 2009-04-01
Guess I'll try it the next time I do an update.

---

