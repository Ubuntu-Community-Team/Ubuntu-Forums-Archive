---
title: "What happened to my UPDATE MANAGER?"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by naqibsalim on 2009-06-28
i received this:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Anyone can help me with this prob?

---

### Post by starcraft.man on 2009-06-28
Easy problem to fix, means that the software sources is set to look at the install media you used to install Ubuntu when you do any installs. To fix this simply go System > Administration > Software Sources > Then at the bottom deselect the CD/DVD listed there. They won't be checked anymore for packages. Not needed anyway, since packages on the install media mostly become obsolete in a few weeks.

---

### Post by naqibsalim on 2009-06-28
thnx man...

---

