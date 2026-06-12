---
title: "Upgrade from Jaunty to Karmic resulted in catastrophic failure"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by eOgas on 2009-11-01
So I've just "upgraded" to 9.10 and I have some big problems.

First, I should probably explain my upgrade experience.  The first attempt failed half way through downloading all the necessary packages with a generic "Could not access these repositories, etc, list of repositories" error.  I figured it was just a result of my terrible connection cutting out, so I had another go.  This one made it almost all the way through installing all of the packages until the very end. I don't remember the exact package that it failed on, but it basically said "Install of package [packagename] failed, fixing broken packages."  And I left it at that.  I figured that I would have to do a fresh install, which I really didn't want to do.

I rebooted, in hopes that that might make my last attempt more successful.  I was presented with my good old 9.04 grub screen with the same old entries, leading me to believe that the install had reverted correctly.  Which is why I was so surprised to see the logon screen for Karmic.  At this point, I knew something was terribly messed up.  After logging in, I was presented with a perfectly working copy of Karmic Koala (except sound, which is completely and utterly broken).

The only problem is that it's only starting Karmic because Grub is trying to start Jaunty, and it's failing, and out of some work of magic, it has figured out that Karmic is installed instead and that it should boot to Karmic.  If I run update-grub, it claims to have updated menu.lst with entries for the latest kernels.  But I can assure you, it has not updated menu.lst, and Karmic is running on 2.6.28-15, not the 2.6.31-14 that it claims to have added to menu.lst

I will attempt to delete my old menu.lst (with a backup of course) before running update-grub again, but it's looking pretty grim at the moment.  I may have to just do a clean install.  If anyone has any suggestions, they would be greatly appreciated.

---

### Post by eOgas on 2009-11-01
Okay, so it looks like deleting the old menu.lst has fixed the issue.  All I need to do now is add my custom entries again.  Sound is even fixed (probably because I'm running on the correct kernel now).  Consider this issue solved.  I really need to learn to mess around with stuff a little more before I post.

---

