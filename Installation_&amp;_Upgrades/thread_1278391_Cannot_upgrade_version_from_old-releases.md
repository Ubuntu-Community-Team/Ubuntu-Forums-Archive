---
title: "Cannot upgrade version from old-releases"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2009-09-29
When an Ubuntu installation (for example v7.04 or v7.10) has the "sources.list" configured for the server old-releases.ubuntu.com , the update manager cannot upgrade distribution to a version available in the server archive.ubuntu.com (for example to v8.04)

The upgrade application tries to only replace the "gutsy" word by "hardy" (for example), and when "hardy" is not available in old-releases.ubuntu.com , fails to continue the upgrade process.

In my opinion it's convenient to distribute a new upgrader package for all versions, to solve this issue.

---

### Post by snowpine on 2009-09-29
Ubuntu has no official support whatsoever for releases prior to 8.04 Hardy Heron. Whether you argree with this policy or not... that's how it is.

You can simply change 'old-releases' to 'archive' and continue the upgrade.

(edit) In my opinion, if you are using 7.10 or older, you should perform a fresh re-install of the current version.

---

### Post by drs305 on 2009-09-29
The old-releases archives are simply to get you up to the last of the unsupported release updates. Once you have done that, you transfer to the current repositories to continue the update.

---

### Post by narcisgarcia on 2009-09-30
In the archive.ubuntu.com there isn't any 7.10 package, including the upgrade tool. Then:
a) Using old-releases.ubuntu.com cannot find 8.04 packages.
b) Using archive.ubuntu.com cannot find 7.10 upgrade tool.

In both ways the user cannot do a version upgrade, because the update-manager doesn't find each package in the "version upgrade" process: the system is designed to access 8.04 and 7.10 files from the same server.

It may not be a software bug; the problem is the Canonical strategy to move old versions to another server (old-releases.ubuntu.com). Leaving all materials in archive.ubuntu.com there wasn't any problem.

---

### Post by drs305 on 2009-09-30
Are you following the guidance of the EOL (End of Life) Ubuntu wiki pages? It includes notes about having to install *upgrade-manager* and *upgrade-manager-core*. 

Start at the top of the page, complete the initial steps, and eventually it will give instructions for upgrading from a specific release.

[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

I still support the 'clean install' option, but there is guidance in place to help with an upgrade. Best of luck.

---

