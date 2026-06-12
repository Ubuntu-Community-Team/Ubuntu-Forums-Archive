---
title: "Auto mount partition so that amarok can read?"
date: 2008-09-18
forum: General Help
---

### Post by spark29 on 2008-09-18
I have a fat32 partition so I can use it for files I want to get from linux or windows os's. It has all my music on it, but I always need to mount the partition and then load it in amarok. Is there a way I can have it auto mount on boot to fix this? Thanks.

---

### Post by mb_webguy on 2008-09-18
Add an entry for the partition to fstab.  [This link]("http://www.psychocats.net/ubuntu/mountwindows") should help.

Then add the new directory to Amarok's library.

---

