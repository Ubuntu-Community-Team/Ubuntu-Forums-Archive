---
title: "System unusable after 8.10 -&gt; 9.04 upgrade"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by lparsons42 on 2009-06-30
I upgraded my laptop from 8.10 to 9.04 last week, and my system is essentially unusable in Kubuntu now.  Mouse response is poor and the system lags terribly when I try to do anything.  I can log in but most applications are unstable to say the least.  Even firefox and konqueror crash regularly and render pages that are nearly unreadable due to the horrible video flicker.  A Konsole window takes about 10 seconds just to come up and has absurd delays of its own.

When I run 'top' I see that Xorg is taking up the vast majority of my CPU - often up to 95% or more.  Even leaving the system running overnight this does not improve.  I tried 'sudo apt-get update plasma' thinking perhaps the fact that plasma is not showing up on top might be telling me something; this did not help.  I tried 'sudo apt-get update Xorg' and that did nothing.  

Is there a way to either re-install or un-install the 9.04 upgrade?  My system was fine in 8.10 but after seeing the improvements of the 9.04 upgrade on my desktop I thought it would be worthwhile to do the upgrade on my laptop.

The laptop in question has a 1.6Ghz P4m with 2gb of RAM, and a Radeon Mobility video card.

---

### Post by lparsons42 on 2009-06-30
I have noticed that response is normal over an ssh connection in to my laptop; however it is unusable when I am actually using it directly...

---

### Post by SigmundFreud on 2009-06-30
You could try to reconfigure the X server (sudo dpkg-reconfigure xserver-xorg) -- most options are correct by default so you only need to press the Enter key a few times. Then reboot.

---

### Post by lparsons42 on 2009-06-30
> **SigmundFreud said:**
> You could try to reconfigure the X server (sudo dpkg-reconfigure xserver-xorg) -- most options are correct by default so you only need to press the Enter key a few times. Then reboot.

I tried this, and found that when I log in locally I still have the same problem of an unusable system, with XOrg at 95% CPU.  Remote logins over ssh are fine.

I have also noticed that Kubuntu trashed a login account (my wife's account).  It no longer allows a log in under that account, stating incorrect password.  However I cannot change the password, it gives me a mismatch error.  I'm not sure how to solve this other than making her a new account and deleting the existing one (very sub-optimal solution).

This is, to say the least, extremely disappointing.

---

### Post by lparsons42 on 2009-06-30
Is there a way to just roll-back the upgrade, or do I have to format and reinstall linux from scratch?  I would very much prefer to have a usable system and this is not usable.

---

### Post by lparsons42 on 2009-06-30
I just rebooted the same system from a kubuntu 9.04 live CD, and I see that here XOrg also uses over 90% of the CPU (making system unusable).

Clearly, I won't be running 9.04 on this system.  I wish I knew what changed between 8.10 and 9.04 to do this.

I do not know of any way to undo this "upgrade" to 9.04; it looks like I will have to wipe my system and start over.  I don't know what would be the better choice this time; wipe the system and go back to 8.10 or wipe the system and go back to FreeBSD.

---

