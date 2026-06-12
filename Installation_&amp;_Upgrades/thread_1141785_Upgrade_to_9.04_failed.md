---
title: "Upgrade to 9.04 failed"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by CFO on 2009-04-28
I attempted to upgrade to 9.04 from 8.10 and during installation I receive the following message:"  W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080412)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080412)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead. "

I was upgrading from Upgrade Manager, not from a CD, so I don't understand the problem and do not know how to proceed. Any help will be greatly appreciated.

---

### Post by taurus on 2009-04-28
Go into System -> Administration -> Software Sources and remove the check mark for Cdrom.  Close and see if you can upgrade to Jaunty now.

---

### Post by CFO on 2009-05-02
Taurus

I appreciate your help. After doing your suggestion, the upgrade ran flawlessly.

---

