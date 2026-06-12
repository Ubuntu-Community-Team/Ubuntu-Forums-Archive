---
title: "graphic login screen gone/damaged"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by cronos on 2009-11-10
Hi all,

I am running Ubuntu 9.10, and everything was running fine until I tried to boot Ubuntu after a power failure caused my computer to switched off while Ubuntu was running/idling.

So, when I try to boot, the white Ubuntu logo would show up as normal, but then it would display a text login screen.  The brown/black screen does not show up at all.

Sometimes the text login screen would flicker while displaying "starting firewall", as if it is in some kind of loop.  It is hard to type when this happens.

If I login, I don't know what to do.  I tried typing "startx", but it can't find my screen?

Some other stuff that is worth noting before this problem...

I installed firestarter, and I adjusted the settings; I only opened some ports for Amule.

When I installed a program using CLI, I noticed that a Nvidia package was listed as no longer needed.  I don't know if the package was automatically removed.  But, I know I did not remove it, and would not remove it, because I do not trust removing unneeded packages.

If there is any other information that you require, please let me know.

I hope someone can help me.  Thanks.

---

### Post by werdberd on 2009-11-10
Well, the first thing you should probably do is login and type sudo touch /forcefsck and then reboot.  This will check your filesystem(s) for errors and is generally a good idea if the computer ever loses power unexpectedly.

---

### Post by cronos on 2009-11-10
Thanks. I will do that now.

I just realised that I put this in the wrong thread. Sorry.  Please close/remove this thread.

---

