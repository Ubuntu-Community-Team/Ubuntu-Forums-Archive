---
title: "RAID or backups"
date: 2008-06-28
forum: Hardware
---

### Post by jbrown96 on 2008-06-28
I am trying to create a fairly serious server to act as a MythTV backend and general media server. I've decided that I'm going to go with a pair of 500GB drives, but I want some sort of redundant storage. I have read some pretty crazy stuff about how surprisingly unreliable RAID 0 can be during a disk failure. What's the best way to go? RAID 0 or have a backup manager running. It would be software raid, and I have no where near enough to fill either drive (probably 6-10 months before I would). I also have an external 250GB firewire/usb hard drive that I have no use for. 

Any suggestions?

Thanks for the advice.

---

### Post by |{urse on 2008-06-28
raid 1, speed + a mirror. That might be more what you want. so long as its a real hardware raid. Even more secure (my favorite) is a raid 5 + 1 hotspare.

---

### Post by NetworkGuy on 2008-06-28
IMO  Backups

People and companies have systems with RAID setups, but even RAID setups can fail.  I've personally seen it and have been very glad to have our backup copies.

---

### Post by |{urse on 2008-06-28
oh and stick with 3ware (best overall supported in linux) raid controllers if possible. Onboard fakeraids are usually too slow to bother with.

---

