---
title: "Multiple DVD drives with multiple region codes, possible?"
date: 2019-10-16
forum: Hardware
---

### Post by simple_impulse on 2019-10-16
I live in Finland, which uses region code 2 (Europe) for DVD drives DRM system. However, there are some DVDs which I would like to watch not available in region 2 (or regionless 0). 

So if I have a drive I normally use for region 2 and if I buy external drive for region 1 DVDs (and let it lock to region 1), will this work? I assume this is not normal, but I don't know enough to say if this is workable solution. Basically one drive would continue to be region 2, external drive would be region 1 and they would work without knowing about each other. I would use only one to play at any time.

Workable?

---

### Post by jimmyrus on 2019-10-16
> **simple_impulse said:**
> I live in Finland, which uses region code 2 (Europe) for DVD drives DRM system. However, there are some DVDs which I would like to watch not available in region 2 (or regionless 0). 

So if I have a drive I normally use for region 2 and if I buy external drive for region 1 DVDs (and let it lock to region 1), will this work? I assume this is not normal, but I don't know enough to say if this is workable solution. Basically one drive would continue to be region 2, external drive would be region 1 and they would work without knowing about each other. I would use only one to play at any time.

Workable?
should work since its the drive firmware itself thats region locked. And if it doesn't you can return it and get your money back. But why do that at all if your going to watch movies on your pc? Rip the DVD down to an iso image, mount it via loopback mode, and enjoy.

---

### Post by simple_impulse on 2019-10-16
> **jimmyrus said:**
> should work since its the drive firmware itself thats region locked. And if it doesn't you can return it and get your money back. But why do that at all if your going to watch movies on your pc? Rip the DVD down to an iso image, mount it via loopback mode, and enjoy.

But if I put region 1 DVD to region 2 DVD drive for ripping, what happens? If the region code is wrong, I believe it tries to change the DVD drive's settings for that. It can be changed limited amount of times, I believe. This was the original reason I asked; I have no idea what happens. Years ago I received (as a bonus gift for some hardware) region 1 DVD and if my memory serves, it asked if I want to change region code. 

But with two drives I guess it's OK? It does not try to snoop other drive's codes...? I'm paranoid, but not always wrong. :D

---

### Post by jimmyrus on 2019-10-16
Far as I know the regions only are for viewing, not ripping. if you mount it as a data disc, you get data. You can always just use dd to clone the entire device to a file, and loopback mount it.

---

