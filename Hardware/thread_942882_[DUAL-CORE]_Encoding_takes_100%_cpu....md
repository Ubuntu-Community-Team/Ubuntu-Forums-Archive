---
title: "[DUAL-CORE] Encoding takes 100% cpu..."
date: 2008-10-09
forum: Hardware
---

### Post by kakyoism on 2008-10-09
My CPU is CUO-2-DUO at 1.83Ghz. But when doing an mencoder job, namely mpeg to x264 conversion, both cores show 99%-to-100% usage from the gnome resource monitor. 

Am I wrong or when doing computationally expensive work, the dual-core CPU is supposed to leave me one nearly idle core for other tasks??

Thanks!

---

### Post by justsomedude on 2008-10-09
That's perfectly normal.

You can use

```
-x264encopts threads=1
```

if you just want to use one core.

---

### Post by kakyoism on 2008-10-09
Thx, but unfortunately it didn't do the trick for me...

Here is my command:

```
mencoder -ovc x264 -x264encopts threads=1:pass=1:bitrate=500 -oac mp3lame "$p_in" -o "$p_out"
```

What part did I do wrong?
Thanks.

---

