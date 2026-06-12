---
title: "Upgrade to 9.04 breaks sound in MythTV"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by dtgolder on 2009-06-09
Had a MythTV setup running, with everything working fine.

Upgraded (using Update Manager) to 9.04.

Upgrade went smoothly, no errors, and everything works--BUT...

When playing back recordings with MythTV, the sound is "wrong". Very hard to describe--the sound is there--it plays, but characters' voices are "too high"...sounds like they've inhaled some helium. Others have described it as sounding like the "chipmunks" (I think they are describing the same issue).

It's very subtle, but annoying. The video playback doesn't seem to have been sped up, but the voices seem to be.

Playing back the same recordings using another player (e.g Totem Movie Player) and the sound seems normal--so I'm suspecting it's something with how MythTV is dealing with the sound in 9.04 from previous versions.

Doing a bit of research seems to indicate this may be related to playing back at different audio rates? (44kHz vs 48 kHz) but I can't seem to find a fix that works (see [this thread.]("http://www.gossamer-threads.com/lists/mythtv/users/344348"))

Others seem to think this may be related to a PulseAudio conflict, but solutions there seem to be resolving NO sound--I have sound, but it's playing back too high.

Has anyone else experienced this with an upgrade? If so, have you been able to fix it?

Any help would be greatly appreciated. Thanks!

---

### Post by dtgolder on 2009-06-16
Update: I think I was mistaken on this being just a Myth issue...playing back some mpeg files with other players on that computer has the characters giving the same chipmunk sound...so perhaps it's an issue with the sound configuration in ubuntu after the upgrade? 

Any help appreciated...

---

### Post by dtgolder on 2009-06-20
Update: Got frustrated trying things, and did a fresh install of Jaunty...and...the problem persists! Now I really don't have any idea what gives.

Fresh install of Jaunty.
Installed codecs to play an .avi
Tested the playback and the voices are still playing "too fast" - like chipumnks, or the characters are on helium.

I even tried removing PulseAudio, but that didn't seem to help...

Am I the only one with this issue? I sure would like to hear from anyone else with this problem, and a possible solution (other than going back to Ibex...)

Thanks!

UPDATE: The problem goes away with Ibex...so same hardware, same everything--sound is too fast with Jaunty but works fine with Ibex & Hardy...what a disappointment...

---

