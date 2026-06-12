---
title: "Prepare Partitions(nothing shows up)"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by civicsi on 2009-08-13
Ok i'm running windows xp and i'm trying to install ubuntu but i get to 
step 4 of 7. I get to were it says Prepare Partitions and everything is blanked
and grayed out.
I don't know what to do. Can some1 please help me. 
I want ro get this install asap

---

### Post by ronparent on 2009-08-13
Is it possible that windows is installed on a raid array? If so, do nothing yet.

---

### Post by Mark Phelps on 2009-08-14
Not sure what "everything is blanked or greyed out" means, but it's most likely that the Ubuntu installer is either not detecting your XP installation or not detecting your drive.

If it's the former, you can try downloading a burning a GParted LiveCD from distrowatch.com, booting from that, and if IT detects your drive, use that to shrink the XP partition and create the Ubuntu partitions -- and then select Manual Partitioning when you do the install.  This way, you won't accidentally overwrite your XP installation.

If it's the latter, don't know what to tell you.

---

