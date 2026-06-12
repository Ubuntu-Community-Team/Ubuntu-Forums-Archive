---
title: "Adept tries to force me to upgrade! :("
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Koraq on 2009-01-19
I've always used the Adept notifier and been happy with this way of staying on top of updates.

But, now I have a long list of stuff which I wont install because among the updates are a new kernel, and I'd prefer to stay with the one I have.

So, I try to unselect that package so it wont be installed. The bad thing is it still say "upgrade"!! 

Can I not refuse a kernel upgrade? I don't want it.

---

### Post by ajgreeny on 2009-01-19
Use synaptic and lock the version you have in the **Package** menu.  I think that stops it showing in your update manager until you unlock it.

---

### Post by Koraq on 2009-01-19
I tried to guess this would be independent of GUI, but apparently the KDE Adept package manager don't communicate with Synaptic, which is a Gnome tool. 

*sigh*

Why on earth is upgrading your third party software something which behaves radically different depending on what GUI you use?!?! I'm considering fleeing back screaming to BSD land...

Many thanks for your help, though, ajgreeny! Synaptic seem to be able to lock and hide the kernel from upgrading.

---

### Post by ajgreeny on 2009-01-19
Yes, when I used kubuntu in previous versions, (I now use and prefer gnome so use ubuntu) I still used synaptic, which I think was installed only because I always added kubuntu-desktop to a standard ubuntu.  I could not get on with adept in those days; I haven't tried it for a long time, so can't comment now, but it seems a bit of an oversight if you can't lock a package version with that.

---

