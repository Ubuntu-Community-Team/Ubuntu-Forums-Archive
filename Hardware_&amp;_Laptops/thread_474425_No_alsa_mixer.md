---
title: "No alsa mixer"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by 4tro on 2007-06-15
I have bought a new laptop, everything is working fine, but...
I haven't got an alsa-mixer for some reason.

The only thing that works is the OSS mixer, which only gives mono sound on one speaker/earplug.

the live cd did had an alsa-mixer, but somehow it won't start on my installed feisty system.

i'm a little bit in the dark on where to start.

The system is a Acer 5102 WLMi with:
AMD Turion 64 X2
Ati Radeon XPress 1100 with 265 MB

my lspci recognizes the device:
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
the OSS claims it as a realtek ALC883 soundcard by the way.

*edit*
looks like my IDE controller and my souncard both are running on irq:16.
investigating further
i followed another thread.
[http://ubuntuforums.org/showthread.php?t=452992&highlight=ati+soundcard](http://ubuntuforums.org/showthread.php?t=452992&highlight=ati+soundcard)
although that workaround caused it to not recognize anything at all, removing it afterwards fixed my problem :S
dunno what exactly happened :P

---

### Post by renzokuken on 2007-06-15
well, if it is a ALC883 card, i initially didnt have that working on my laptop either.

i fixed by simply compiling the latset "alsa-driver" from source, and havent had a problem since

---

### Post by 4tro on 2007-06-15
> **renzokuken said:**
> well, if it is a ALC883 card, i initially didnt have that working on my laptop either.

i fixed by simply compiling the latset "alsa-driver" from source, and havent had a problem since
i shall try that, because the fix was temporary :(

---

### Post by csisgro on 2007-06-15
I have the same laptop and the last kernel upgrade broke my sound. after much much research and fiddling here is what made it work:

I editted /etc/modprobe.d/alsa-base and added this line to the beginning:
options snd-hda-intel index=0 probe_mask=3 position_fix=3

I got that info from another thread about Aspire 5050 which is a smilar machine.

---

### Post by 4tro on 2007-06-17
a recompiling of the alsa drivers fixes things as well.

i suspect both have the same fix =)

---

