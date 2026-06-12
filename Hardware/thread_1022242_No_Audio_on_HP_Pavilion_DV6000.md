---
title: "No Audio on HP Pavilion DV6000"
date: 2008-12-26
forum: Hardware
---

### Post by rca219 on 2008-12-26
I've inherited an HP Pavilion dv6000 laptop.   I've wiped the drive and installed Ubuntu 8.10 and everything has gone otherwise perfectly, except for the audio.  I cannot get any audio out of the built-in speakers.  If I plug headphones into the jack, the audio works fine.   I've scoured the threads and found a couple of entries regarding modification of the file /etc/modprobe.d/alsa-base, but so far I've not had any luck.    I've checked every setting I can find to determine that speakers are not muted.

I'm stuck at this point.   Any ideas?

---

### Post by bibleman on 2008-12-26
I hate to ask such an obvious question but did the speakers work in the first place with whatever OS it had before you wiped it?

---

### Post by rca219 on 2008-12-26
It's unclear.  I "adopted" this laptop from my father-in-law who was running XP on it.  He claimed that there was intermittent problems with the speakers, but I attributed his audio issues with his lack of understanding of how to properly use the system .... 

I don't understand the relationship between the soundcard, the output jack for the headphones and the speakers.  If sound works through the output jack, are we assuming that there's a physical problem with the speakers?

---

### Post by bibleman on 2008-12-26
Thats my guess. I don't know how your speakers and laid out either but I would think it possible for the the speakers to be broken and the output jack to work. It could be that the connections have come loose. 

Think about it this way... You know that sound is working because you can hear sound through the output jack. This would mean that the correct module is loaded for the kernel. So there must be another source of the trouble. 

If it is hardware then you could send it to HP to repair, but they will load XP onto it. Or you can always try to repair it yourself by ripping it apart and re-soddering the connections.

---

### Post by bibleman on 2008-12-26
As a side note I have an HP Pavilion zt3000 laptop and I have not experienced your problem with my laptop. For me the sound "just worked." My laptop is nearly five years old now too

---

### Post by rca219 on 2008-12-26
Thanks - I'm comfortable enough with the hardware that I may pull it apart and look at the speaker connection.

---

