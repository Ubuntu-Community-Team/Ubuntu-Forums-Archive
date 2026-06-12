---
title: "Swap Problems"
date: 2008-11-07
forum: General Help
---

### Post by scot.mcpherson on 2008-11-07
It appears as if some people have identified a problem during installation where the swap partition isn't getting mounted automatically.

It appears the UUID of the swap partition isn't being identified correctly, and getting the UUID from the command blkid -m and copying the UUID from their to /etc/fstab will solve the problem.

I didn't know if anyone had seen this yet, and I wanted to make sure that the ubuntu community was aware of it.

Scot

---

