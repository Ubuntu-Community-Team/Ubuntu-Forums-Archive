---
title: "What should I be concerned about before upgrading to Jaunty?"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Erik765 on 2009-07-01
I really want to upgrad to Jaunty (from Intrepid), especially since I found out it has built in xbox controller support.

I've had bad luck in the past when upgrading other distrobutions and just want to hear some experiences and some thing I should be aware of or concerned about before hitting the upgrade button.

From what I would guess, all the packages installed from repositories would get upgraded, but other programs I've installed outside of the repositories will not, and I'll have to upgrade them manually.

Is this correct?

Let me know your thoughts please ;)

E

---

### Post by lparsons42 on 2009-07-01
> **Erik765 said:**
> I really want to upgrad to Jaunty (from Intrepid), especially since I found out it has built in xbox controller support.

I've had bad luck in the past when upgrading other distrobutions and just want to hear some experiences and some thing I should be aware of or concerned about before hitting the upgrade button.

From what I would guess, all the packages installed from repositories would get upgraded, but other programs I've installed outside of the repositories will not, and I'll have to upgrade them manually.

Is this correct?

Let me know your thoughts please ;)

E

What kind of system are you about to run the upgrade on?  I just ran the upgrade from 8.10 to 9.04 on my laptop and I wish I would have just ran my system over with my car instead, it would have been much more useful.

There is a significant problem with certain ATI video drivers (or related to them) in 9.04 that causes XOrg to go berserk.  My system is completely unusable for a local user now, I am still trying to figure out how to fix this.  I have uninstalled and reinstalled the drivers but I am no better off.

So my advice to you is, tread lightly - especially if you have an ATI video card.  I think the Intel and NVidia cards do OK but there does not appear to be a way to roll back the "upgrade" once it is done.  I will likely have to wipe out my linux partition in the coming days to get back to anything remotely useful.

So in other words, in terms of what to be concerned about, be concerned about your video drivers.  Be very, very, concerned.

---

### Post by lparsons42 on 2009-07-01
I should add to that, you can probably tell if the video driver problem will affect your system by first booting a live CD on your system.  I found that the live CD on my system behaves just as badly as the install (XOrg at 95% CPU or more at all times).  Unfortunately I did not have the foresight to try that first.  I would say burn a live CD first, boot from it, wait a few minutes for the system to stabilize and then check 'top'.  If XOrg is at a normal CPU level (less than 15%) you should be OK.

---

### Post by raymondh on 2009-07-01
> **lparsons42 said:**
> I should add to that, you can probably tell if the video driver problem will affect your system by first booting a live CD on your system.  I found that the live CD on my system behaves just as badly as the install (XOrg at 95% CPU or more at all times).  Unfortunately I did not have the foresight to try that first.  I would say burn a live CD first, boot from it, wait a few minutes for the system to stabilize and then check 'top'.  If XOrg is at a normal CPU level (less than 15%) you should be OK.

+ 1 ..... the liveCD is a good indicator.

---

### Post by Erik765 on 2009-07-01
Thank you for replies ;)

I'm running an Nvidia 8600 and the live cd worked fine for me, except for the font sizes, which I've figured out the fix for.

I will try the live cd again before I go for it just to be sure.

What about in regards to the programs themselves? Was I correct in my assumption that the packages installed outside of the repositories will not be upgraded?

Thanks again for the heads up. Any one else? ;)

---

### Post by colin.p on 2009-07-01
I just did an upgrade from intrepid to jaunty this afternoon. So far no issues and no freeze-ups.
I don't know for certain but I would think that any programs not in the repositories would have to be manually updated. But then again, I haven't installed anything that wasn't in the repos.

Colin

---

