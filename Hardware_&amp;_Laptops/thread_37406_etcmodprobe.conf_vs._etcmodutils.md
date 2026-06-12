---
title: "/etc/modprobe.conf vs. etc/modutils"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by Crass Spektakel on 2005-05-27
I have somewhat successfully succeded to use my Soundblaster AWE32. Even the EMU8000 is working mostly flawless but it was a lot of work as Ubuntu saw nothing of the AWE (or an alternate SB16) at all - Ubuntu seems to ignore all ISA-PNP-Stuff. So yes, it is working but I am not sure if it is done the right way.

First I have to load drivers from /etc/modules by adding the lines "snd-sbawe" and "snd-emu8000-synth". I always thought adding stuff to /etc/modules is some cowards last resort but times are tough...

Next I created /etc/modprobe.conf so my Wavetable gets initialised:
install snd-emu8000-synth /sbin/modprobe --ignore-install snd-emu8000-synth && /usr/bin/asdxload /usr/local/share/awe32/synthgm.sbk
(I also set startup-mixer-settings in a similiar way but do not have the lines at hand right now)

While I think this is the right way to do it I am VERY confused about /etc/modutils/: This directory should be überobsolete but is filled with lots of config stuff which on one hand never ever will get executed at all (remember, we use /etc/modprobe.conf nowadays) but still contain stuff which looks "usefull" for other people. At least /etc/modutils was the wrong place to initialize my Wavetable.

So now I ask myself: Have I overlooked the real place to configure stuff or is this halfbaked by design? Or even more stupid question, where is some command-line-die-hard alsa-setup-for-ubuntu?

---

