---
title: "Update installation failed"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by villalcalde84 on 2009-06-16
I'm using Ubuntu 8.04 Hardy Heron and today I got a notification to install some updates. I installed all of them except for one, libtorrent-rasterbar4.

In the images below are the messages than appear when trying to install them. What can I do to fix this?

Thanks in advance.

---

### Post by villalcalde84 on 2009-06-16
As additional information, most of the updates, if not all, I do not remember, were for Deluge, and now I can not run it.

Please, some one tell me how can I fix this.

Thanks.

---

### Post by banana989 on 2009-06-17
+1 ... libtorrent-rasterbar4 and rasterbar2 problems here as well.

---

### Post by jimmy the saint on 2009-06-18
This type of thing happens sometimes with Deluge.  I assume that is what you are using.  It also happens more frequently if you are using the up to date version from the deluge repos as opposed the older version in the Ubuntu repos.  My solution for problematic updates regarding anything deluge or torrent related is to mark deluge and all of its parts for complete removal in synaptic, also python-libtorrent in this case since it is causing issues.  Once they are completely removed, reinstall deluge and everything will be updated.

---

### Post by villalcalde84 on 2009-06-21
Fortunately, the problem was solved using an option from the update manager. I really do not know what it did, but it got fixed.

Thanks jimmy the saint, I was thinking about that, but before I started removing Deluge, the problem was solved. I will keep it in mind if another problem appears.

---

