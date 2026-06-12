---
title: "Speaker Out , doesn't work"
date: 2019-09-15
forum: Hardware
---

### Post by flyinghigh2 on 2019-09-15
Hi my speakers work on my laptop

but the speaker out doesnt, (the mic in does as Ive tested it in audacity)

---

### Post by Skaperen on 2019-09-15
by default, pulseaudio only outputs to one output device at a time.  i believe the reason for this is to keep the lag (time delay) of audio to a minimum for games.  you should learn how to change settings on pulseaudio so you can always do it yourself.  if you need help learning, come bask and ask.

---

### Post by flyinghigh2 on 2019-09-16
yes thats right
when i put the headphone jack in the line out the laptop speakers stop, but nothing comes out the line-out.

---

### Post by guiverc on 2019-09-16
You haven't told us what release (or possibly flavor) you are using of Ubuntu.

After loading `pavucontrol` (Pulse Audio Volume Control) which is listed in my menu under "Sound & Video" (Lubuntu 19.10), the "Output Devices" lets me control where sound goes out using the drop-down list. You haven't told us what release you are running, but have you looked in `pavucontrol` to see if you can control it there?  

It could also be that that output has been muted, if so that's (`pavucontrol`) the best place in my opinion to unmute or fix sound issues (for me it's usually after I drop something on the keyboard, or accidently miss & hit a bunch of unknown keys that the system understood as shortcuts).

---

### Post by flyinghigh2 on 2019-09-17
ubuntu`16.04LTS

I cant see pavucontrol

ouput device is onboard sound but still no sound on lineout

might be the cable - will buy a new cable today and check

---

