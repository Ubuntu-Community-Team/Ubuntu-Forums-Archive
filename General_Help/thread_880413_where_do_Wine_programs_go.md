---
title: "where do Wine programs go?"
date: 2008-08-05
forum: General Help
---

### Post by dh003i on 2008-08-05
Hi all,

I installed Wine on my Ubuntu setup. Wine seemed to Install ok, and I can even open up notepad or other simple programs. However, I attempted to install my Olympus Master software from my Olympus E3 CD. It appears to install fine (no errors). However, then I go into my wine folder, and it isn't there:

/home/user_name/.wine/drive_c/Program Files

It just shows the following

Common Files
Internet Explorer
MSXML 4.0
QuickTime
Windows Media Player

Why no Olympus Master software program? huh?

---

### Post by p_quarles on 2008-08-05
You should just have a look through the simulated C: drive hierarchy, since it should be on there somewhere. For easiest browsing, use the Windows Explorer clone that comes with Wine:
```
winefile
```

---

### Post by dh003i on 2008-08-05
> **p_quarles said:**
> You should just have a look through the simulated C: drive hierarchy, since it should be on there somewhere. For easiest browsing, use the Windows Explorer clone that comes with Wine:
```
winefile
```

I don't even see the winefile program.

---

