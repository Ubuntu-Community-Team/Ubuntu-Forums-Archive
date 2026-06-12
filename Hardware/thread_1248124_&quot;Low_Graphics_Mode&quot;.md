---
title: "&quot;Low Graphics Mode&quot;"
date: 2009-08-23
forum: Hardware
---

### Post by Mentiroso on 2009-08-23
So, I have a Dell XPS M1530. It has had ubuntu pre-installed on it.

Recently, my computer has been insisting it will run in only "low graphics mode" as it claims it cannot detect the screen or the driver (I'm also having OpenGL issues, but I imagine these are connected). I'm pretty sure I did nothing to encourage this, though I could be wrong. 

What could be making this happen? It was detecting perfectly fine until a few months ago. If there's any information I could supply, please tell me exactly what to type and/or run to get that information to you all.

---

### Post by Sam Lars on 2009-08-25
Could you post the output of
```
lspci | grep VGA
```
in a terminal?

---

### Post by Brightbelt on 2009-08-26
I'm having the same issue on my HP Mini netbook. I'm using Ubuntu Netbook Remix; everything seemed fine, then "Low Graphics Mode" hit.

---

### Post by Mentiroso on 2009-08-26
I managed to fix this by running EnvyNG. I have no idea what that program did, but my computer and graphics are both working fine now.

---

