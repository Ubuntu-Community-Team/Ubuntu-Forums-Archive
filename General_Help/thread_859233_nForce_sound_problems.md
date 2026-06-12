---
title: "nForce sound problems"
date: 2008-07-14
forum: General Help
---

### Post by slackpipe on 2008-07-14
Not sure if i can actually get help on this one.  I've recompiled my kernel (used the old config, all i changed was i added one line to the ch341.c file to recognize the programmer for an ATMega168.)  I had to do this, because I ordered a Nerdkit (which is wonderful, btw)

The new kernel works great, but sound no longer loads.  I'm using onboard sound with the nForce chipset.  Since i have what is basically the exact same kernel, i figured that i could just load the modules that work in the generic 2.6.24-19 kernel i was running.  But i can not figure out how to get them to load.  I've tried modprobe intel8x0 and snd_intel8x0 but both give me module not found.  The nvidia website only has downloads for RH and Suse and says "included in most distributions"

If anyone can help me, it would be greatly appreciated.  Thanks

sp

---

