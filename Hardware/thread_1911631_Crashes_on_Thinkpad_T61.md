---
title: "Crashes on Thinkpad T61"
date: 2012-01-19
forum: Hardware
---

### Post by hartz on 2012-01-19
I have a new install of Kubutu (Long time user of mostly Ubuntu but many other distributions also tested, if only briefly)

I have some minor instability issues with kubuntu.

Predominantly plasma crashes (maybe 5 times a day).
Dolphin and Rekonq crashes ocasionally (about 5 times a week)
Muon hangs (especially if anything else also operate on the dpkg database while muon is working)
pulseaudio stops producing sound from video playback (as described in many places, mostly after pausing and then resuming playback)

Some more detail:
Plasma regularly but with no pattern I can find yet, stops working and then gets restarted.

Dolphin and Rekonq also just crashes with no as of yet determinable pattern.  I stopped using rekonq as soon as I got firefox installed though.

Muon doesn't seem to lock out other Apt programs properly. I can start synaptic and run apt commands on the command line even while muon is running (idle).

If muon is busy, eg downloading, then running for example an apt command causes muon to freeze (requiring the process to be killed).

Right now I have even more issues with muon (Though this might be an issue for a separate thread - I'll include it here for completeness' sake).  I decided to add the KDE beta PPA to the repositories.  This was done from the command line through apt, and the package database then "updated" with no issue.  After this muon complained that another application is holing the locks.  I could not find anything so I rebooted.  After that muon seems to think my package database is corrupted (though the update notifier informed me that there are updates available)  When I got this error I decided to try command line, and the normal "sudo apt-get upgrade" appears to be working fine (Still running).

Any ideas!?

For what it is worth I like KDE on kubuntu so far.  I decided to give the KDE RC a try to see whether it is at all more stable that the current 4.7.3.

Cheers

---

### Post by hartz on 2012-01-24
Since I've upgraded to KDE 4.8 RC2 (four days ago) I have not had a single plasma crash.  This is in contrast with on average 5 crashes per day.

---

### Post by cespinal on 2012-01-24
Try to update to the latest 4.7 that went live yesterday. 

Also check on if you have graphic drivers installed.

---

