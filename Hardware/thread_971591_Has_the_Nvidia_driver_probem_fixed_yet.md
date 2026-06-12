---
title: "Has the Nvidia driver probem fixed yet"
date: 2008-11-05
forum: Hardware
---

### Post by Relayer on 2008-11-05
I have an FX 5500 card and when I first installed 8.10 it broke the drivers. I reinstalled 8.4, and will not upgrade until the issue is fixed. Has Nvidia released a driver that fixes the issue?

---

### Post by RatSAT on 2008-11-05
Nvidia has started making the legacy driver compatible with X.org server 1.5, and a beta can be downloaded [here]("http://www.nvnews.net/vbulletin/showthread.php?t=122139"). It's not on the main nvidia download site yet, and probably also not yet in the ubuntu repo.
So you could try those drivers, or wait until it becomes a little less beta.

---

### Post by macstevejb on 2008-11-05
there are packages for the new beta legacy nvidia drivers available from the proposed repository.

Check out Alberto Milone's blog here:

[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/) 

also look at bug 251107 here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

regards
:p

---

