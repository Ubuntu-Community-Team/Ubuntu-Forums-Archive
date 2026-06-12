---
title: "Strange Sound Problem"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by Tsuki on 2005-09-05
Yesterday, I had sound working fine using esd.  Today, it just doesn't work.  In the meantime it's been moved from one house to another in the boot of a car, but I'd rather not wonder if the sound card could be broken in case there might be a software problem here...

Testing esd in gstreamer-properties results in "Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'".  (It says the equivalents for OSS and ALSO too.)

Running esd from the terminal results in "/dev/dsp: No such file or directory".

I guess it doesn't look good for my sound card, what with there not being a /dev/dsp - or am I misunderstanding what /dev/dsp is?

Any ideas, anyone?

Thanks in advance

---

### Post by s_p_a_r_k_y on 2005-09-05
try a live CD like ubuntu or Knoppix and see if any of them can detect it

---

### Post by ninerkz on 2005-09-08
I've also experienced the same problem recently.
I tried to check the sound w/ a live CD and it does work.

Do you know how I can re-install the default or original sound system from the live CD? I thought I could just copy over some config files, but that didn't seem to work.

I recently tried to follow someone's advice in the Ubuntuforums about getting multiple sound sources to work at the same time... it made the sound come out horrible. When I tried to revert to what it was before, other things started breaking and now my wireless card is having difficulties connecting.

~j

---

### Post by ninerkz on 2005-09-08
Well, I fixed the problem...
I guess the network was having problems, not my wireless card.

And after switching around sound systems, somehow the PCM volume got muted. I turned it back on using [alsamixer].

~j

---

