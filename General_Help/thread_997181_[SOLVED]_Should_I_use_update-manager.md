---
title: "[SOLVED] Should I use update-manager?"
date: 2008-11-29
forum: General Help
---

### Post by josephellengar on 2008-11-29
Does it show the final updates, or does it show prereleased updates?  I wasn't sure, and frequently I run update-manager and it tells me there are updates that didn't show up in my notification area.

---

### Post by jgoguen on 2008-11-29
The update manager shows new packages for all repositories.  If you've enabled the intrepid-proposed (or the proposed repo for your Ubuntu version) then you'd be getting pre-release updates.  If not, then you're only getting final updates.

To check, go to System -> Administration -> Software Sources and click the *Updates* tab.  If the check box for **Pre-released updates** is unchecked then you're only getting final updates.  I'm not sure why Update Manager would show updates and no tray icon though.

---

