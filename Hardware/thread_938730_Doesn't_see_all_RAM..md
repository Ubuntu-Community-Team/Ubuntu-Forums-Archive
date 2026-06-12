---
title: "Doesn't see all RAM."
date: 2008-10-05
forum: Hardware
---

### Post by Artess on 2008-10-05
So, I added 2 more GBs of RAM to two I already had, it means it should be now 4. However, it shows me that I only have 2,9 GB RAM. I think I'm using 64-bit Ubuntu, at least I thought so when I was installing it. I'm kinda new to all this, so it would be nice if you could also tell me where can I look it up =)

---

### Post by Idefix82 on 2008-10-05
Type
```
uname -a
```
in the terminal and see if the output contains the letters x86_64 or something similar. If it does then you are running the 64 bit version, otherwise the 32bit version, which I would guess from your problem description.

---

### Post by Artess on 2008-10-05
yeah, it has exactly same letters, so at least I'm using what I thought I was using.

---

### Post by Kevbert on 2008-10-05
> **Artess said:**
> So, I added 2 more GBs of RAM to two I already had, it means it should be now 4. However, it shows me that I only have 2,9 GB RAM. I think I'm using 64-bit Ubuntu, at least I thought so when I was installing it. I'm kinda new to all this, so it would be nice if you could also tell me where can I look it up =)

You may need to set something up in bios.  It may be marked as memory hole remapping or something like that.  This is due to the fact that years ago it was thought that no-one would ever need more than approx 3Gb of RAM and so everything above that amount was allocated to the peripheral devices such as I/O.

---

