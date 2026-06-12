---
title: "Upgraded 8.04 to 8.10, Amarok Broken"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2009-03-02
Ran the upgrade via Synaptic and Update Manager.  I like a lot of things about the new version, but a few problems did crop up.  I tackled most of 'em, but the one I can't figure out is why Amarok now skips like a bad CD.  Not all the time, but after a couple songs have played, it seems to get bogged down or something.  The upgrade seems to have wiped out the MySQL database/server or something for Amarok, I had to install those packages and set the db up again.  I hoped that would solve the problem, but it skipped with the SQLite db and the full blown MySQL db.  It did not skip at all before the upgrade.  Any ideas, this one's got me stumped?

Oh yeah, Dell D820 laptop, 2GB memory, 120GB SATA HDD, 2ghz Core 2 Duo...I think thas all the pertinent info.

---

### Post by nexus_2006 on 2009-03-03
Any clues?  Maybe if this should be in the multimedia forum rather than the upgrade forum, someone could move the thread?

---

### Post by nexus_2006 on 2009-03-04
OK, I don't think the problem is amarok or the codecs, etc.

Two processes, kacpid and kacpi_notify, are together chewing up about 50% of my CPU constantly.  Then with opera and amarok on top of it, the computer gets behind every now and then, and the sound skips.

What can I do to rectify this problem?  I did not notice these processes before the upgrade, and clearly they shouldn't take up this much CPU time.  ???

---

### Post by nexus_2006 on 2009-03-08
OK, still going on, can't figure it out.  A lot of the time it is X.org causing the problem.  I think I'm going to format and downgrade back to 8.04.  Never had issues before.  Is there a known problem with nVidia drivers and the new X.org?

---

