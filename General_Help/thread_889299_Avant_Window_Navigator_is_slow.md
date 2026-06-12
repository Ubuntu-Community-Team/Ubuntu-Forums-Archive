---
title: "Avant Window Navigator is slow"
date: 2008-08-13
forum: General Help
---

### Post by specvthis on 2008-08-13
I have a fresh install of Heron 8.04 and i have installed both the bzr version and standard repo version of Avant and the awn-manager. The problem is that it steals all of my CPU (Dual core - 1 CPU is at 100%) and runs like a dog. Any idea what could be causing this problem? Help?

---

### Post by moonbeam on 2008-08-14
If I was to guess I'd probably need to focus on the fact that you're using an Nvidia card.  I'm guessing the proprietary drivers are being used?

The following assumes that it's one of the wonderful Nvidia is acting with 2d acceleration bugs...  before following that route it might be worthwhile to remove any running applets (except Launcher/Taskmanager) to make sure it's not an appplet run amock.


A quick summary...  on some, system configurations, with some Nvidia hardware, seemingly also varying by driver version in some cases, there are issues with 2d performance especially when xrender is used.

This is not to say that Nvidia drivers aren't wonderful, glorious pieces of software but they do seem to have this issue :-)  

A good place to start reading is probably:  [http://www.phoronix.com/forums/showthread.php?t=11044](http://www.phoronix.com/forums/showthread.php?t=11044)

Good luck.

---

