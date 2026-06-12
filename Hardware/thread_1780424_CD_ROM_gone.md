---
title: "CD ROM gone"
date: 2011-06-12
forum: Hardware
---

### Post by RicardoE on 2011-06-12
Hello,

I installed Ubuntu 10.4 a long time ago, but ever scince my CD/DVD-ROM stoped working, I didn't care because I dont use this too much, but now I really need it. I tried mounting it, and every solution online with no luck, the CD-ROM works because I installed ubuntu with a live CD, and when I input a CD it reads but seems like never mounts.

Thanks guys.

---

### Post by dandnsmith on 2011-06-12
I feel you're saying the CD device works on too little evidence.
"I installed Ubuntu 10.4 a long time ago"..."the CD-ROM works because I installed ubuntu with a live CD" - all that says it that, at that time the device worked.

Reading a CD goes in 3 stages:
- device recognises a CD is inserted and starts it rotating
- device positions to the index track (innermost) and tries to read it
- index track info passed to OS to deal with.

It sounds like the first stage is successful, but, possibly, not the second, and almost certainly not the 3rd.

Can you try booting from your liveCD again, to verify that it really does work?

If it doesn't, then you could try a lens-cleaner CD to see if that will enable the CD to read.

---

