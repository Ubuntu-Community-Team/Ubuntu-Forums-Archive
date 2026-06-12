---
title: "Dell Studio 15 Ubuntu 9.10 No Sound (fresh install)"
date: 2010-02-10
forum: Hardware
---

### Post by ftaylor on 2010-02-10
Hello,

My shiny new Dell Studio 15 laptop was delivered this morning, and I can't seem to get the sound to work.

[http://www.alsa-project.org/db/?f=d7136df5fcf3064b9b77244990ff786c6d3846b9](http://www.alsa-project.org/db/?f=d7136df5fcf3064b9b77244990ff786c6d3846b9)

I haven't tried implementing any changes or fixes, as all the guides I have read say "if you can type X into terminal and it comes up Y then fix/hack this", and when I type X into terminal, I always get the normal result rather than the problem.

Any ideas?

Thanks,
Finbarr

---

### Post by riksweeney on 2010-02-10
Stupid question time:

Have you checked the mixer and made sure all the volume meters are at the top?

I only ask because it took me about 30 minutes of web searching before I checked properly and raised the PCM volume...

---

### Post by ftaylor on 2010-02-10
Where are the mixer levels?

edit:

just ran alsamixer. All at max.

---

### Post by ftaylor on 2010-02-10
I managed to fix the problem. Added the following line

```

options snd-hda-intel model=dell-m6

```

to

/etc/modprobe.d/alsa-base.conf


Apparently many laptops need a line similar to this added to the alsa-base(.conf) file for the sound to work - it is specific to the model of laptop you have and Google will yield all the answers. You need to replace PulseAudio or restart PC for this to take effect.


Finbarr

---

### Post by arsham on 2010-02-24
I'm having the same problem here
I tried lots of googleing and seems this solution was fitting my situation.

But it just enables the OSS , and pulseaudio doesn't work at all
Has anyone solved this problem yet?

---

