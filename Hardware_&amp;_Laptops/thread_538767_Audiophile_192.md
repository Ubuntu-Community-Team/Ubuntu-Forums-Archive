---
title: "Audiophile 192"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Scheater5 on 2007-08-30
The forums has a couple of posting about this card, but few people seem to be able to get it to work and none of their methods seem reproducable (compiling the newest ALSA sources yeilded no appreciable result for me).
I have what seems to be a common problem - horribly distorted, entierly too loud sound.  But here's the reason for my post:  the card works find on my hardware in Sabayon.  I'm posting this from the x86 3.4e Sabayon live CD, and the soundcard works like a champ.  How do I find out what Sabayon is doing that Ubuntu isn't?  Is there a particullar config file I should try comparing, or perhaps a library or program that Sabayon has an updated version of?

EDIT:  It is apparently the kernel.  The change-logs of the kernel show that one of the newest revisions added support for the Audiophile 192.  The Gusty repos have a kernel new enough, and I've managed to upgrade my Ubuntu Studio 7.04 to have 2.6.22-10-generic, but I still can't do any audio work as JACK requires a low-latency kernel.  Where do I find 2.6.22-10 (or -9) low latency and how do I install it?

---

### Post by stmiller on 2007-09-19
```

sudo apt-get install linux-lowlatency

```

Or you can [compile your own kernel]("http://ubuntuforums.org/showthread.php?t=311158") from kernel.org.

---

