---
title: "Upgrade halted - how to resume?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by sptrashcan on 2009-10-30
I started the upgrade process from 9.04 to 9.10 last night.  I ran into a problem in the middle of the upgrade - my /boot partition was full, because it contained several obsolete kernel files, and so the new kernel files could not be written to the partition.  I have since cleared out some space on the partition and run dpkg --configure -a as the update-manager suggests, and that seems to have worked as far as it goes, but now I am wondering how to safely resume the upgrade.

---

