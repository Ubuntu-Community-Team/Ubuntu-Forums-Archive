---
title: "cx88-alsa distorted &amp;&amp; audio kernel patching the ubuntu way"
date: 2008-06-10
forum: Hardware
---

### Post by charles_elwood on 2008-06-10
I've been having issues with the analog (svideo and composite) inputs on both of my HVR-1300 cards. I think I've run into the race-condition as describe and fixed in [http://linuxtv.org/hg/~tap/v4l-dvb/rev/31860d2a60bf](http://linuxtv.org/hg/~tap/v4l-dvb/rev/31860d2a60bf)

I intend to have a play with the above patch and see what happens, but this is where I'm running into problems, I'm cool patching and building from source, but I don't know the ubuntu way* of building kernels. I will need to roll out a fix on a number of machines and would like to be able to make .deb packages available (and distribute via my website and or launchpad PPA). To make things more complicated I'm already having to use the version of linux-ubuntu-modules in Stefan Bader's PPA. Can anyone point me at a guide for doing this the ubuntu way?

* As in being able to provide a source .deb and then build it rahter than the easy but unhelpful way of patch, make, make install...

---

