---
title: "Something wants the cpu 100% all the time"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Moustacha on 2008-01-28
There's something very odd going on. Installed gutsy amd64 on a hp pavillion dv9000. got everything else working, but there's been a consistent problem of the cpu wanting to be at the highest powerlevel the whole time. I have to manually set the cpu to 800MHz or powersave, because if it's on demand it sits at 1.6GHz the whole time. I've checked top and that says only 3 or 4% cpu usage when idle, which SHOULD NOT cause it to bump up to 1.6GHz. The system monitor applet has the faded out blue, showing there's something wanting to do work in the background. I've disabled indexing. What else could it be? It's a real PITA

---

### Post by derred on 2008-01-28
Have you tried installing powertop?
I've used it a couple of times. Turns out my modem driver was causing me all kinds of problems so I just unloaded it (never needed it and never will).

To install it just ```
sudo apt-get install powertop

```
One more thing, You have to run it as root so ```
sudo powertop
```

---

