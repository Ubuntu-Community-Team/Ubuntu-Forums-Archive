---
title: "What's my graphics card?"
date: 2010-06-27
forum: Hardware
---

### Post by lukster91 on 2010-06-27
Hey,

Is the a software program or a terminal code to tell me what graphics card I have? 

It's not built into motherboard, it's just plugged in. The graphics card isn't labelled (it fell off a few months ago and I lot it).

So just wondering if there is a piece of software or a code I can punch in to give me my magic answer?

I'm running Ubuntu 10.04 LTS 32-bit.

Thanks.

Luke Bellamy

---

### Post by GreenN00b on 2010-06-27
Try running
```
lspci | grep VGA
```
in a terminal.

---

### Post by lukster91 on 2010-06-27
Thanks. Worked beautifully.

---

### Post by GreenN00b on 2010-06-27
You're welcome. Please mark thread as [solved].

---

### Post by lukster91 on 2010-06-27
I don't know how to do that.

---

### Post by GreenN00b on 2010-06-27
Look in thread tools menu above the first post.

---

