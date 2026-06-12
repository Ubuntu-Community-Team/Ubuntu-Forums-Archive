---
title: "HDD Mount Oddity"
date: 2014-05-11
forum: Hardware
---

### Post by david211 on 2014-05-11
I made an account to ask this question so I'm definitely new here, and I apologize if this is in the wrong category. A few weeks ago I followed the Home Linux Server Guide (for the most part) because I had a box that wasn't being used, and I figured learning a linux server has no downside. I've had a few stumbles but managed to work through it, but this one is a little odd, and I'm wondering if someone might have an answer as to what's going on-

I am running Server 12.04 (no GUI) and using it as a media/file/game server (and slowly adding more features to it because, hey why not?). I've got 5 HDD's in it right now; OS, movies, music, photos, and storage. I have them all being mounted at boot and the issue pops up when I restart the server through the OS versus a hard shutdown.[INDENT]
Shutdown -r restarts it like normal, however it for some reason won't mount the movies or photos drives, and doesn't let me mount them manually either. 
Shutdown -h then powering on via the button mounts the drives no problem. 
[/INDENT]

They fail to mount ~80% of the time with soft restarts, but **never **fails when it is being powered on physically. Is there any reason this might be happening? Since it isn't just a crapshoot as to whether or not it works, it leads me to believe it isn't a connection issue with the drives themselves, however I'm wondering if it might be a **power **issue. The four storage drives are actually parked in removable front bay trays (where CD drives and stuff go). The unit itself has four bays, each with its own SATA port, and the four drives share either two Molex or SATA power cables. It seems unlikely, but I was wondering if somehow the soft reset isn't pushing enough power to the unit or something and maybe that is causing the trouble. Otherwise I can only assume it is a software issue.

It isn't really a big deal in the grand scheme of things, as I know how to fix it, but I'd still like to know for my own peace of mind. Any thoughts?

Thanks for reading through and helping!

---

### Post by tfrue on 2014-05-12
Would you post the output of:
```
cat /etc/fstab
```
Also:
```
dmesg | tail 
```
Thanks,
Chris

---

