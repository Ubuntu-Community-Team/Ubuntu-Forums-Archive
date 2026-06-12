---
title: "How to upgrade kernel without internet connection?"
date: 2009-07-08
forum: Hardware
---

### Post by m4cph1sto on 2009-07-08
I have a new Eee PC 1005HA, and I'm installing Eeebuntu standard 3.0 (I posted on their forum but thought I'd try here as well).  Everything works great except neither my lan or wireless internet is working.  People report that a kernel upgrade to 2.6.28-12 should solve the wireless problem.  Normally this upgrade is done automatically with upgrade manager, but obviously that won't work for me since I have no internet access.

So, how do I upgrade my kernel?  I assume I could do it from a .deb package downloaded on my desktop computer then transferred to my Eee, but I don't know how to do this.  Note that I want to use the Jaunty version of Eeebuntu, and I'm using the array.org kernels.  

I tried to use my desktop PC following the guide on [www.array.org](www.array.org) for building a custom kernel, but at the last step when I try to do
fakeroot debian/rules binary-eeepc binary-headers
I get an error:
make: *** No rule to make target `binary-eeepc'. Stop.

Anyway, I'm just hoping that somebody has experience building the array.org kernels, or perhaps knows where I can download pre-made .deb packages so I can just install them and get my networking working on my Eee PC!  Thanks!

---

