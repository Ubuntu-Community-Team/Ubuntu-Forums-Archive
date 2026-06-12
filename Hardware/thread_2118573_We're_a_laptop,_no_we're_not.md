---
title: "We're a laptop, no we're not"
date: 2013-02-21
forum: Hardware
---

### Post by echamber on 2013-02-21
Ubuntu 12.04 seems to think my desktop PC is a laptop. This causes my machine to automatically hibernate when it thinks the battery is critically low. I was able to temporarily fix this by following this guy's tutorial ([http://www.youtube.com/watch?v=CQ-SMAK9dNo](http://www.youtube.com/watch?v=CQ-SMAK9dNo)). I'd like to completely resolve the issue though.

Hardware
Mobo: ASRock Z75 Pro 3
Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
nVidia GeForce GTX 460

P.S. The reason for the title

$ laptop-detect -v
We're a laptop (ACPI batteries found)

---

### Post by echamber on 2013-02-22
Bump

Why would Ubuntu think that I have a battery installed in my system? Is this a bug? Can this be fixed?

---

### Post by echamber on 2013-02-22
Fixed!

I just saw a new update to the kernel 3.5. Updated and now all is well.

---

