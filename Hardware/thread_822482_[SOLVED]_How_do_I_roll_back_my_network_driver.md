---
title: "[SOLVED] How do I roll back my network driver?"
date: 2008-06-08
forum: Hardware
---

### Post by benbelly on 2008-06-08
I recently upgraded to hardy, and I am having trouble with my onboard network ports now.  The default kernel is 2.6.24-17-generic, and it uses the forcedeth driver version 0.61 for my onboard nforce ethernet.  It doesn't work.

  When I boot with the older kernel 2.6.22-14-generic, my ethernet works.  That kernel is using the forcedeth driver version 0.60.  However, I can't get the desktop to work with my 8800GTS with that kernel , so I would rather use the newer kernel, if I can figure out how to change the network driver to the 0.60 version.

  Can anyone tell me how to roll back forcedeth driver?  Or any driver, and I can figure out the forcedeth specifics.

Thanks,
Ben

---

### Post by benbelly on 2008-06-09
Bump.  This problem has made my desktop effectively useless.  I've posted questions about four times, but I can't seem to get help resolving it.  Am I asking wrong?  In the wrong place?  Please - I really need some help with this one.

Thanks,
Ben

---

### Post by Tom--d on 2008-06-09
Try the lastest kernel, -18 generic.

Its in the repos. See if that fixes your problem.

---

### Post by benbelly on 2008-06-10
Thanks for the suggestion.  The new kernel has the same problem.  :(

  It looks like it uses that forcedeth 0.61 driver too.  I guess maybe I'll track down the support team for the driver itself.

---

### Post by benbelly on 2008-06-10
Well, this is rather embarrassing.  My BIOS was a rev out of date.  I thought I had the latest.  Turns out that the new version fixed some network stuff.  :oops:

So, if any of you have a ASUS P5N32-E SLI, make sure you have the latest BIOS.

---

