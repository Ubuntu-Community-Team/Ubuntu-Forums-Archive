---
title: "Microphone not functioning - Toshiba laptop"
date: 2011-07-02
forum: Hardware
---

### Post by dandaman96 on 2011-07-02
I can't seem to get the mic on my laptop to function properly.  I've spent the night reading every post I could find and I'm come up blank. 

External mics work fine.  The internal works fine under Windoze.  But in 11.04, all I get is static when I use the internal mic.  

[http://www.alsa-project.org/db/?f=9ac7ed7c89b0e4a7f1b95f5b3b5d0466f722a4c2](http://www.alsa-project.org/db/?f=9ac7ed7c89b0e4a7f1b95f5b3b5d0466f722a4c2)

Any thoughts?

---

### Post by Peashooters on 2011-07-12
I am using 10.04 and I have a a similar problem.  It plays back as if I wasn't shouting at it at all.  Static sort of background noise it puts out.

---

### Post by eGlyph on 2011-07-13
There were several threads on this subject already, none of them being marked [Solved].

I have this problem on Toshiba Satellite 500 series, though the mic worked perfectly until 10.x branch of Ubuntu. Switching to ESound and/or recompiling ALSA didn't help much.

---

### Post by lidex on 2011-07-14
> **dandaman96 said:**
> I can't seem to get the mic on my laptop to function properly.  I've spent the night reading every post I could find and I'm come up blank. 

External mics work fine.  The internal works fine under Windoze.  But in 11.04, all I get is static when I use the internal mic.  

[http://www.alsa-project.org/db/?f=9ac7ed7c89b0e4a7f1b95f5b3b5d0466f722a4c2](http://www.alsa-project.org/db/?f=9ac7ed7c89b0e4a7f1b95f5b3b5d0466f722a4c2)

Any thoughts?

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=toshiba" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by slotto on 2012-05-05
Thanks anyway. I've been battling with my internal mic since 10.04. But after installing 12.04 all of my problems are solved!

---

