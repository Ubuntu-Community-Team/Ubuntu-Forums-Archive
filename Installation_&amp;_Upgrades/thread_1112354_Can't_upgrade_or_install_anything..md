---
title: "Can't upgrade or install anything."
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by BlessedThief on 2009-03-31
This is part of the errow message I get when I try to install or upgrade from Dapper Drake.
I hate the thought of going back to Windows. Any help?


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by finer recliner on 2009-03-31
someone correct me if i'm wrong, but when doing an upgrade from aptitude, you can only upgrade to the next chronological version, and I dont think edgy eft repositories even exist anymore because its so old. Even if they are around, if you were to upgrade one version at a time, you're very likely to encounter some terrible errors along the way. you're better off doing a fresh install of intrepid ibex (the latest version of ubuntu). 

remember to back up your files :)

---

### Post by 123456789123456789123456 on 2009-03-31
tell the version of ubuntu, to upgrade to any new distributions.  not just long term supported versions.  I think this is under synaptic.  After this, reload repositories, then go to update manager, the distribution listed should be 7.04.  go through this until you get the newest one 8.10.  If 7.04 is not listed.  A fresh install is the only option you have.

I know from 7.10 I can upgrade all the way to 8.10.  I don't know if that is possible with 7.04, since 7.10 does not exist for download from ubuntu main site anymore, but it is available elsewhere.

you can try upgrading from each one, if you have a cd of each distribution, however that causes problems.

---

### Post by Partyboi2 on 2009-03-31
You can follow [[COLOR=Blue]these[/COLOR]]("https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS") instructions to upgrade to hardy. With LTS releases you can upgrade straight to the next LTS without having to do all the normal releases in between.

---

