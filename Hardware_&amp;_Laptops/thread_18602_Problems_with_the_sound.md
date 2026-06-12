---
title: "Problems with the sound"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by ziania on 2005-03-07
Firstly say that it's the first time I have posted here, and that I hadn't used english in years so for that reason I could have a bit of problems. But I expect that someone could understand and help me.

I've been using Ubuntu for three weeks, and I'm not a linux professional, so I have some problems managing it. 

The problem that I have is that some days ago I started to couldn't hear or listen anything but, before It happened everything works well... In my opinion the problem started when I installed the ogg'module, but I'm not sure at all.  :-k 

All what I can explain about the error is that when I started Ubuntu, before it apears the shell to put the user and the password, It apears some warnings and errors... I pasted next:

modprove: WARNING: Error inserting snd_timer (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-timer.ko): Unkown symbol in module, or unkown parameter (seedmesg).

modprove: FATAL: Error inserting snd_pcm (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-pcm.ko): Unkown symbol in module, or unkown parameter (seedmesg).

modprove: WARNING: Error running install command snd_pcm.

modprove: FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.8.1-3-386/kernel/sound/usb/snd-usb_audio.ko): Unkown symbol in module, or unkown parameter (seedmesg).

modprove: WARNING: Error inserting snd_raw_midi (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-rawmidi.ko): Unkown symbol in module, or unkown parameter (seedmesg).

I wish that someone could help me  :roll:

---

### Post by alastair on 2005-03-07
What changed?

What sound card? What chipset? (NForce/NVidia?)

---

### Post by ziania on 2005-03-08
I talked with a friend and explained me that this could happen because of  sound's permission, so I have tried with:

chmod 666 /dev/dsp*
chmod 666 /dev/mixer*

And sound was fixed.

Thanks

---

