---
title: "Patching"
date: 2008-07-12
forum: General Help
---

### Post by sparrowkc on 2008-07-12
As far as I can tell, there isn't a tutorial in the forums or on the wiki that describes how to apply patches.  I have a specific problem, but I would like for there to be an answer in this thread that other people can use.

I want to use the PC-Speaker driver found here [http://www.geocities.com/stssppnn/pcsp.html](http://www.geocities.com/stssppnn/pcsp.html) on a Gutsy box.  It gives a patch for the "alsa driver" but I have no idea what that is or how to patch it.  I think that I have to get the source, patch that, and compile it, but I don't know.  Could someone help?  Again, I would like this thread to contain iformation on patching the kernel also.

---

### Post by sparrowkc on 2008-07-12
I feel bad for bumping my own post, so I'll only do it once.

---

### Post by geraldm on 2008-07-12
The kind of PC speaker that is being referenced is the much older speaker used on early PCs.  It is like a cheap radio speaker, and can play varying frequencies.
Newer PCs use piezoelectric speakers whose frequency range is quite limited and may not be what you are looking for. 
Check your system motherboard manual before going to the trouble of patching.

The alsa project sources can be downloaded from [www.alsa-project.org](www.alsa-project.org).
You should be familiar with programming and already have the build-essential
package set up.  

There are instructions on compiling from source in the alsa packages.  You need to take them in proper sequence, alsa-drivers, alsa-libs, alsa-utils.  Do back your system up before attempting these changes so you can recover if you make a mess.  You should check the patch to be sure that the patch will work for the version of alsa that you are using.

Good luck,

Gerald

---

