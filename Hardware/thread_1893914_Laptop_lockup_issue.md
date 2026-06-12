---
title: "Laptop lockup issue"
date: 2011-12-11
forum: Hardware
---

### Post by Whydoe on 2011-12-11
I have a fresh install of Ubuntu 11.10 on an Acer Aspire 5610.  The system appears completely stable until I try to do things like listen to music or watch a video.  Seems if there is no input from the user (keyboard or using touchpad) the computer appears to hang or go into sleep mode of some kind after only about 5 seconds.  Once you press a key or use touchpad - it's back to normal.  The same happens with internet usage.  Tried to disable the touchpad (Fn F7) to see if that helped, but it does the same thing.  The only info I was able to pull off system was the following from the syslog

Dec 11 11:04:27 dan-Aspire-5610 kernel: [ 5085.854039] iwl3945 0000:05:00.0: Queue 4 stuck for 2000 ms.
Dec 11 11:04:27 dan-Aspire-5610 kernel: [ 5085.854052] iwl3945 0000:05:00.0: On demand firmware reload
Dec 11 11:04:27 dan-Aspire-5610 kernel: [ 5085.856650] ieee80211 phy0: Hardware restart was requested
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: The canary thread is apparently starving. Taking action.
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: Demoting known real-time threads.
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: Successfully demoted thread 1346 of process 1340 (n/a).
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: Successfully demoted thread 1345 of process 1340 (n/a).
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: Successfully demoted thread 1340 of process 1340 (n/a).
Dec 11 16:05:23 dan-Aspire-5610 rtkit-daemon[1342]: Demoted 3 threads.  

This is 2 instances in a row when I stopped using the computer while listening to a music file.  Any suggestions?

---

### Post by Whydoe on 2011-12-11
It appears that a BIOS update solved the problem.... so far.  Haven't been able to replicate issue since the update.  Flash update 3.1 for Vista.  Thanks for the help.  Hey don't mention it.  ;)

---

