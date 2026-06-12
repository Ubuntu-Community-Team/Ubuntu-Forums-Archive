---
title: "Session menu gone, can only log in to failsafe"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Fr33d0m on 2009-11-05
Well I was generally satisfied with 9.10 until yesterday evening.  I got home from work and booted the laptop only to find that when I logged in I went straight to failsafe.  I didn't have time to troubleshoot and I had setup my /home on a separate partition so I simply reinstalled, did what I needed to do and applied updates/installed emesene and liferea.

This morning I am back to booting straight to failsafe and I notice the session menu no longer exists.

I am on a Dell XPS M1330 with Intel video and have the 64bit version of Karmic installed by itself.  

I do not recall seeing an upgrade to the video driver--I've seen other people (mostly with Nvidia) have been left in a similar condition by a driver upgrade.

startx does not start X.  I'll have to try again and post the exact response.

Anyone have an idea on further troubleshooting or fixing?

---

### Post by Fr33d0m on 2009-11-05
startx gives a generic server error and says it is already running which I think is correct.

I tailed the dpkg log and see that the last thing I installed was Cheese and I also remember installing the restricted extras package.  I doubt these could be the issue but will try uninstall/roll back some things to see if I can get anywhere.

I still don't know what to look for.  I tailed several other logs but nothing jumped out at me.  Any help would be appreciated.

---

### Post by Fr33d0m on 2009-11-06
Since nobody seems to have any ideas, I reinstalled and will take a slower approach to patches and other additions.

---

### Post by Fr33d0m on 2009-11-11
I've been stable all week and have installed all the applications and updates that had been installed before with one exception--ubuntu-restricted-extras.  The extras package loads several 32bit libraries and apps.

I did try to recreate the problem by loading the extras package but was unable to so my assumption that the extras package was at fault remains unproven.

---

