---
title: "[SOLVED] missing files from update manager"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by AlanInVancouverBC on 2008-12-07
This bugs me:
I go to update software and end up, **always**, with this message:
(see screenshot)
Suggestions?

---

### Post by taurus on 2008-12-07
Close down update-manager.  Then go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and remove a check for Cdrom.  Click Close and then the Reload button.  That should remove CDROM as the source from your /etc/apt/sources.list.

---

