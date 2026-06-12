---
title: "How to prefer CD for upgrade (minimising downloads)"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by xurizaemon on 2009-06-07
Hey, I just completed a network upgrade to 9.04 but I wish I'd known the best way to prefer the CD and download only required files.

When loading the CD (9.04 live CD), it tried to autorun, but this didn't do anything useful. I'm sure I remember being prompted with previous CDs "You've inserted an upgrade CD, would you like to upgrade now?"

I added the CD via apt-cdrom and then ran update manager. Upgrade Manager prompted me to upgrade to 9.04, but when it did this it did the full download (1.1GB) rather than using files from CD first.

I know that updated files should come from the network, but I figure that there must be a method to get the CD to be the preferred source.

The 9.04 CD is the first entry in /etc/apt/sources.list - the network sources all appear after that.

Thanks in advance!

---

### Post by zvacet on 2009-06-08
You need alternate CD to do upgrade.

---

