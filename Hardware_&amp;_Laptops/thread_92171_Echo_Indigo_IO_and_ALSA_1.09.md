---
title: "Echo Indigo IO and ALSA 1.09"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by imrazor on 2005-11-18
I'm trying to get an Echo Indigo PCMCIA card to work in Hoary. There's apparently no support built into the ALSA bundled with Hoary, so I thought I'd download the latest ALSA (which supposedly does support my card) and try to compile it. However, when I attempt to compile ALSA I get three warnings: 1) That ALSA is already compiled into the kernel, 2) that there is no predefined kernel compiler and 3) that there is no Makefile.conf in alsa driver source directory. It sounds like I need to remove the ALSA 1.08 from the kernel and compile 1.09 modularly. How do I go about this? Where do I find a Makefile.conf for ALSA?

Any help would be appreciated...

---

### Post by 23meg on 2005-11-18
I haven't done this myself but I think you should start with a vanilla kernel, without ALSA support built in. For help on compilation do a search on the forums with the keywords "kernel compilation" and a few helpful threads will come up. 

For help on getting your card working, consider posting to the linux-audio-users mailing list. The folks there are have good knowledge and up to date info on the status of (semi)pro soundcards in Linux.

---

