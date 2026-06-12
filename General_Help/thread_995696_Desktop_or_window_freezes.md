---
title: "Desktop or window freezes"
date: 2008-11-28
forum: General Help
---

### Post by helmut_ibm on 2008-11-28
Hi.

I hope, this forum is apropriate for my question since it is most likely X11 related.

I have a Radeon 9200 graphics card. If I turn on 3D effects (System->Preferences->Appearance->Visual Effects) to Normal or Extra, sometimes my whole desktop (Gnome) sometimes freezes. Then I'm not longer able to do anything on my desktop. I have to telnet to the system remotely and restart it.

If I set the visual effects to None, the desktop freeze doesn't happen. Instead if a particular prompt window shows up, only this one window sometimes freezes. I can release this freeze by switching to another workspace and then back.

In both cases the problem happens seldom. I think about once or twice a day. My feeling is, that it happens, if a window is about to pop up.

I read something about setting the AGPMode in xorg.conf, but that did not help.

I have attached my xorg.conf to this posting.

Since I have a workaround the problem is not critical, but I would be interested in getting it fixed.

I use Ubuntu 7.10 and upgrading to 8 is not really an option yet. I have too many dependencies on my system.

Greetings from Gurk
Helmut

Helmut

---

### Post by madverb on 2008-11-28
When it freezes can you get to console 'alt+ctrl+F1'?

---

### Post by helmut_ibm on 2008-11-28
No, that was not possible either. Therefore I had to use a remote connecton.

---

