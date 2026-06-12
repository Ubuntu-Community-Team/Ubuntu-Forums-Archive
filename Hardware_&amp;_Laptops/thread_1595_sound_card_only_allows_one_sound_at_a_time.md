---
title: "sound card only allows one sound at a time"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by Vulc on 2004-10-22
k not sure whats going on but when I try to play 2 sounds at once (xmms + aim) it refuses to play the second noise like its always being ignored or something, how do I fix this?

---

### Post by xkcdmagic8 on 2004-10-22
its not a real "problem" its just that ur hardware doesnt support multiple sounds at the same time (forgot word for that :-). And thereof the software is acting stupid and not sure of what to do, check lsmod and make sure only ALSA is running (no oss) and then try it. If not ull have to look into what shit is starting

---

