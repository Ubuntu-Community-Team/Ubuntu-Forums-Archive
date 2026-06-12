---
title: "Pulseaudio crashes"
date: 2008-11-18
forum: General Help
---

### Post by Morientes on 2008-11-18
I have the problem that pulseaudio quite often crashes on my system.
It has happened on two occasions. The first is when using Totem. If I pause Totem, the system hangs sometimes and then pulseaudio crashes. I also experienced that the simple program speaker-test made it crash.
I can restart it using:
```

pulseaudio -k; pulseaudio -D

```
So at least I don't have to reboot, but it is annoying nevertheless.
Has anyone experienced anything similar? Or has an idea of what might be wrong?
I am upmixing my sound to 5.1. I have an Audigy 2 sound card.

---

### Post by Mr. Bunny on 2009-01-08
I'm having intermittent pulseaudio crashes, too. I think the daemon closes when I have problems, as it fails to kill daemon when I run it after a crash. If it's running, it only complains about being unable to find an original dlopen loader. It works either way. Thanks for that line. I'd been logging out and back in to fix it. >.< It happened as I was typing this. This is very strange... it wasn't this bad until today. I wonder what's going on...

---

