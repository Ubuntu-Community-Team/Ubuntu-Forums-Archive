---
title: "latest updates killed my Breezy"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by MrCheese on 2006-01-17
I've been running Breezy as a test install on a caddy-mounted disk alongside my Hoary system for a while & decided to take the plunge & reinstall Breezy on the internal Hoary disk. The install went fine, and initial updates were ok. Then the problems started.
(1) The Nvidia packages no longer produce a working X system (was ok in the test Breezy), apparently the system can't find the Nvidia module.
(2) The big update I did last night has killed the system - my partitions can't be loaded at boot as /proc/boot (?) no longer exists. I suspect that the kernel update has done the dirty deed.
(3) HELP!!!!!!!!!! :-O

Has anyone else killed (or seriously wounded) Breezy with the latest updates?

---

### Post by Sef on 2006-01-17
I had a test computer that I did in when I tried to update.  I ended up just using a Breezy install CD.  Would recommend that is the best way to go.

---

### Post by nocturn on 2006-01-17
Do you have an older Nvidia card?  If so, the driver may be in the legacy package instead of the normal one.

Does it boot with the nv driver in xorg.conf?

---

### Post by MrCheese on 2006-01-19
bit of an update to the main "dead Breezy" bit - I found that fstab had somehow got overwritten with all partitions being mounted in /media - eg / had become /media/devf5.

I've rebuilt this box now so I'll keep an eye on the updates this time.

---

