---
title: "libglib2.0-0 Jaunty Security update (possible issue)"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by jay_tee on 2009-10-06
FYI - there _**may**_ be a problem with the recent Jaunty Security update to libglib2.0-0 (2.20.1-0ubuntu2.1). After allowing Update Manager to update libglib2.0-0 and libglib2.0-data to version 2.20.1-0ubuntu2.1, and rebooting, the keyboard / mouse on my Xubuntu laptop became inoperable.

After 7 or 8 reboots, thru dumb luck, I regained access to the keyboard /  mouse functionality. Then, using Synaptic Pkg Mgr, I did a Force Version on libglib2.0-data, downgrading to the previous version (2.20.1-0ubuntu2). This seems to have resolved the problem I was having.

---

