---
title: "GNOME takes THAT MUCH ram memory!!??!?!!?"
date: 2008-06-24
forum: Hardware
---

### Post by aalr1986 on 2008-06-24
hey guys.....

I think I have a pretty good system, like it's not amazing, but it has enough:

Intel Core2Duo 2.0ghz, 2gb DDR667, 160gb HDD, NVidia GeForce 8600M GT 256mb.

Now, I just turned on the computer, and I opened some programs, like rite now I just have firefox, transmission BitTorrent, Audacius, aMsn, and that's it......

and I type "free -m" in terminal, and it says that it has 1.8GB of ram taken already......

is this true?!??!?!' and if so, then how come'!???! what is takin sooooo much ram?!?!?!?!

btw, I'm using Ubuntu Hardy Heron...

---

### Post by XAVeRY on 2008-06-24
I have the same system (funny thing!), and free -m also says that there are only 58MB RAM free. However, the system monitor says that there are only 526MB occupied.

Why such a big difference?!

---

### Post by aalr1986 on 2008-06-24
wait wait......

what system monitor are u talkin about!??!? where can I find that?!??!

---

### Post by Gannon8 on 2008-06-24
Cache, most likely. Programs are pre-loaded into ram, so that they can start up faster. There is nothing wrong with your system.;)

---

### Post by sdennie on 2008-06-24
As Gannon8 said, it's the cache.  For example:

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          4049       3213        836          0        426       1769
[COLOR="Red"]**-/+ buffers/cache:       1017       3032**[/COLOR]
Swap:         4000          0       4000

```

The line in red is the interesting line for figuring out how much memory your applications are actually using.

---

