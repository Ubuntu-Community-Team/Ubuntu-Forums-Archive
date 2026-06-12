---
title: "how do you boot windows with virtual box?"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by jrm91 on 2009-10-14
I am running jaunty jackalope on an external hard drive and i have windblows xp on an internal drive and i already have virtualbox installed but i can't figure out how to boot windblows xp on the virtualbox. can anyone help me out?

---

### Post by Mark Phelps on 2009-10-14
If you're asking about using virtualbox to boot an existing installation of XP external to virtualbox, I don't believe you can do that.  I believe you have to install XP inside virtualbox first.

---

### Post by wazzup on 2009-10-15
> **Mark Phelps said:**
> If you're asking about using virtualbox to boot an existing installation of XP external to virtualbox, I don't believe you can do that.  I believe you have to install XP inside virtualbox first.

I did this one time in vmware.. you could assign the raw partitions to boot from,, but due to the differences of the physical hardware and the simulated hardware by vmware I'd need different drivers (hence different profiles). Afterwards I was still able to boot from the XP-partition (but I hypothetically would only have done that when I would have completely F-U'd  my ubuntu install (and even then it's probably easier to reinstall ubuntu and get it over with.

Later on I found it far easier to re-install XP on a virtual disk in virtualbox and just share the data partition (mount the ext3-partition using virtualbox to the xp install). Even after a reinstall of ubuntu I could launch the XP-image (and data) right after I installed virtualdisk. (keep data separate from system partition though)

So it might be possible under virtualbox. (**IF** it does allow you to attach raw partitions... )

---

