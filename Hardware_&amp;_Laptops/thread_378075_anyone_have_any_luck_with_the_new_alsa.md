---
title: "anyone have any luck with the new alsa?"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by pixeldotz on 2007-03-06
i configured and installed alsa rc3 and finally got my mic to 'record'.

i say it like this because it doesn't record input from any the mic plug on the side of the laptop.
using audacity i can see that what gets recorded are the little pops and clicks that occur when you plug or unplug the mic from the mic slot.

anyone have any different luck?

also i noticed from rc2 to rc3 that the name of my card was changed from CXT5045 to CX20549 venice.

configured everything as default    --with-cards=hda-intel --with-oss=yes

---

### Post by kazakh on 2007-03-08
the same here.

also, i've noticed that the headphone jack sense doesn't work properly anymore...
now i have to mute/unmute each time i plug the headphones to get them working

---

### Post by peabody on 2007-10-01
**Edit: I found a fix for my laptop.  Open Audacity, set the default sample rate to 48000 and the Sample Format to 16-bit.  Then select OSS /dev/dsp for playback, and the alsa hw0,0 for recording.  Then CLOSE Audacity and open it again.  It should work, if not, try launching it with the aoss wrapper script.**

I having the same problems with this card on my laptop.  I fixed the speaker issue by adding 'options snd-hda-intel model=laptop position_fix=1' to the alsa-base file.  But for the life of me, both Audacity and jokosher are refusing to work with the mic, which is driving me nuts because I know that they work!  Skype, flash quick capture on youtube and recordmydesktop all use my mic correctly!

I can get audacity to use the mic if I use oss as the input and output source, but there's a horrible feedback recorded with my voice.

---

