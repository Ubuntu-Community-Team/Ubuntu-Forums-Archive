---
title: "Sound Problems in Hoary (Alsa/Reverb)"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by nemnivus on 2005-07-31
I just switched from Debian to Ubuntu, everything went well except that there was a noticeable decrease in sound quality. Both distributions use ALSA, but there is a distinct difference between them using my Soundblaster Live card.  In Ubuntu sound is scratchy and reverb is on by default wheras in Debian sound is clear and there is no reverb.  I'm assuming the loss in sound quality is a result of the default reverb, so I'm wondering if there's a way to turn it off.  

For reference, the multimedia device selector in GNOME is set to ALSA instead of ESD, because the Live can do hardware mixing.

---

### Post by varunus on 2005-07-31
Try muting some of the extraneous channels in "alsamixer" from a console; some of these can cause strange effects.

---

### Post by nemnivus on 2005-07-31
Everything is turned off except for the front speakers, all the LFE and 3D switches are off too, it's very strange.  I might just blacklist Alsa and revert to OSS.

---

