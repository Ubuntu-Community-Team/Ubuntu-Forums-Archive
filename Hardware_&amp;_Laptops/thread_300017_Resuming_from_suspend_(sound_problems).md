---
title: "Resuming from suspend (sound problems)"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by catfox on 2006-11-15
I have a sony vaio FE 28H and with Edgy it sleeps and resumes fine apart from the sound upon resume. It stutters uncontrollably and is unusable until I reboot the machine.
I've tried unloading the snd_hda_intel module and a load of others but they can't be unloaded ("being used by another module" etc...), and I've also tried restarting the alsa-utils service, but that has no effect.

Any ideas?

lspci shows my sound card as: Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

thanks

---

### Post by Compaq Armada 7800 on 2006-11-15
it could be the wrong driver

---

### Post by gregorygreg on 2007-07-09
I'm having exactly the same problem.  Let's see this resolved as it is the only drawback to using fiesty on my vaio laptop.

---

