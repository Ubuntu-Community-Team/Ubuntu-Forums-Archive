---
title: "Getting Hardy to recognize more than 4GB of RAM without a kernel recompile"
date: 2008-08-19
forum: Hardware
---

### Post by BrantlyMedders on 2008-08-19
Is it possible?  Is there a kernel image out there that has highmem enabled?

I built a kernel once before (back when I was using Slackware), but I've forgotten most everything I knew about linux since then.

---

### Post by Loaded.len on 2008-08-20
If you're running the 64-bit version then I would think it would automatically see over the 4GB threshold.  If you're running 32 bit, then there's no way you'll see more than 4GB.

---

### Post by ggaaron on 2008-08-20
This bug might interest you.
[https://bugs.launchpad.net/ubuntu/+bug/116842](https://bugs.launchpad.net/ubuntu/+bug/116842)

---

