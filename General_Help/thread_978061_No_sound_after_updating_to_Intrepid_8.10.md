---
title: "No sound after updating to Intrepid 8.10"
date: 2008-11-10
forum: General Help
---

### Post by AlejandroDelLoco on 2008-11-10
So, about a week ago I upgraded to Intrepid with dist-upgrade on my Dell Inspiron 1525n and completely lost my sound.

It's strange - everything *seems* loaded - I can adjust the volume and everything's there (modules loaded etc). I've tried replacing everything with ALSA. I've tried removing pulse-audio and replacing it with ESD (which didn't work so I went back) and I am having basically no luck. 

[alsa-info.sh output]("http://www.alsa-project.org/db/?f=7c2a0f48f366b42dc3258e127e37c8a405262e99")

Halp!

---

### Post by doughnuts64 on 2008-12-17
I have no idea if you have managed to resolve this problem. I had a similar issue on my Dell Dimension E520 PC following the upgrade.

I installed the PulseAudio applet (although don't know if that made any difference), and updated the BIOS for the computer.

After re-boot, I went into volume control, and PCM was right down low. Bringing that up gave me sound (it had been at max previous to the BIOS upgrade, and still rendered no sound).

No idea if that will help.

---

