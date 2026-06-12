---
title: "No sound after suspend on Toshiba Laptop"
date: 2008-11-06
forum: Hardware
---

### Post by xspazmonkeyx on 2008-11-06
I'm running Ibex 8.10 on a Toshiba P105-S6177 laptop. Everything is working as it should except my sound does not work after waking it up from suspend. I have read a TON of posts on the subject, and so far nothing has worked. I have the Intel HDA sound card (ICH7) which apparently sucks. I've edited alsa-base in /etc/modprobe.d/ and added "options snd-hda-intel model=toshiba" That didn't work.I edited /etc/default/acpi-support and added "MODULES=snd_hda_intel" That didn't work either. I've seen scripts posted that say they will kill the sound before a suspend, and bring it back on resume, but they don't seem to work either. Killing and restarting pulseaudio won't bring the sound back. Restarting the ALSA mixer doesn't bring it back. Only hibernating, or restarting will bring the sound back. Does ANYBODY have a solution, or at least a workaround that will bring my sound back without a restart? I'm a bit of a n00b, so let me know if you need me to run any commands in terminal and give you the output. Thanks!:confused:

---

