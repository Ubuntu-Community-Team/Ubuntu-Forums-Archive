---
title: "no options in Hardware Drivers"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2009-08-29
I have a motherboard with an ATI chipset and built-in video.  I have had lots and lots of problems with drivers!  I gave-up on the USB compatibility and installed an add-in USB card, and after trying several suggestions to tweak the video finally gave-up and just used the default non-accelerated drivers.

Now there's a new driver from ATI that sounds like it finally works, but there doesn't seem to be any official support from Ubuntu?  Worse, when I go into Administration > Hardware Drivers I no longer get _any_ choices.  Actually, I think the utility is crashing because it doesn't even report "No drivers available" -- the screen just remains blank.

Is there some way to troubleshoot the Hardware Drivers utility, maybe reset it's configuration (so that it generates a fresh one) ?

---

### Post by mikewhatever on 2009-08-30
I suspect you have an older ATI card the support for which has been dropped. Mentioning the model might help verifying that.

---

### Post by Mark Phelps on 2009-08-30
Since you're getting to a desktop in Ubuntu, it already installed the open source ATI drivers for you.

As mike indicated, you need to tell us the model number of your video card/chip.  Most likely, it's one of the legacy models that ATI dropped from their driver support.l  If that's the case, there are no restricted drivers available for it anymore.

---

### Post by bsmith1051 on 2009-08-30
yes, it's an ATI 2100 which is the 'last' model not supported.  I thought I made it clear that I understood there was no official support.

Nevermind.  I thought there was something wrong with my Hardware Options app but maybe it really just is not finding anything to support.

---

