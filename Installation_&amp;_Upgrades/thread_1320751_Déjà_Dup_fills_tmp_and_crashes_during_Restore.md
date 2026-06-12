---
title: "Déjà Dup fills /tmp and crashes during Restore"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2009-11-09
This is a clean install of KK. Install went thus:

**The day before**: made backup of /home (Jaunty & ext3), using Déjà Dup. Success, external 80gig drive has backup of /home. Excluded /trash in this backup.

**The following day:**

grabbed .iso, ran hash on .iso, clean. Made CD, ran hash on CD, clean. Ran OS from CD. In liveCD session, ran GParted. Reset /sda1 and /sda5 to ext4. Left /swap alone. Exited GParted.

Ran KK install(er). Got to Partition Disk, set /sda1 to / and /sda5 to /home. Completed install. Rebooted per installer request. On reboot set wireless to connect to 'net. Received update instructions for about 22 (maybe 38) packages. Installed those updates. Rebooted. Installed Déjà Dup from the repos. Install reported NO errors.

Called Déjà Dup and ran Restore. Restore ran and failed time-after-time. Contacted developer. He says /tmp is "too small".

Please help me understand how to make /tmp the necessary size. The /home I'm restoring is about 20gig.

---

### Post by Mark_in_Hollywood on 2009-11-09
The devoloper has given me a fix for this problem. I have a separate / and /home and now that he knows that, he is working on a fix.

Thanks, Community.

---

