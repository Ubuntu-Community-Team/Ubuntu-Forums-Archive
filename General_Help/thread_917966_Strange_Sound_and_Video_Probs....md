---
title: "Strange Sound and Video Probs..."
date: 2008-09-12
forum: General Help
---

### Post by bluet0oth on 2008-09-12
Currently running Hardy on a sony vio n350n

Default media player is movie player, first time i run it from either a reboot or a relog, its works without error

If i close it, reopening another movie regardless of format, the video lags and theres no sound unless i hit "Sound -- Volume Up" in the program itself

Trying another media player, the video will play flawless, but no sound

Ne Ideas???

---

### Post by timcredible on 2008-09-12
are you sure totem (movie player) is closing, or is it leaving itself running in the background?  if so, that could cause the problem you're seeing.

if no sound, check to see what sound server it's using.  totem defaults to pulse now, and most others will default to alsa.  you can't have 2 different sound servers running at once, so you have to quit everything using pulse in order to get sound out of an app that uses something else.

---

