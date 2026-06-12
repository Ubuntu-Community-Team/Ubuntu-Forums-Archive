---
title: "Lost /var/lib/php4 after update to breezy?"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by rdenatale on 2006-01-25
This morning I discovered a problem with my mediawiki installation.

It turned out that php4 wasn't able to save session information, and that the save.sessionpath directory /var/lib/php4 had gone missing from my server.

Looking back at my backups, it seems to have disappeared during the week I upgraded the server from Ubuntu 5.04 to 5.10.

I manually created the directory with the same permissions as those in the last backup which contained it, and the wiki seems to be working as normal again.

I'm not sure if I should report this as a bug or not.  The package which owns this file is php4-common and dpkg -s reports the version as 4:4.4.0-3ubuntu1

---

