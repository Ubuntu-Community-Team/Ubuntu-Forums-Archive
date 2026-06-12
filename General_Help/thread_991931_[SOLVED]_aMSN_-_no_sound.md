---
title: "[SOLVED] aMSN - no sound"
date: 2008-11-24
forum: General Help
---

### Post by RuleMaker on 2008-11-24
When i reboot my PC there is a sound, everything works fine until I start opera (flash player). Flash still have sound but aMSN dont.
I tryed in options to change from /dev/dsp to /dev/audio but nothing works, it says: "An error occured when trying to play the sound: could not gain access to /dev/dsp for writing".
So, I think that flash player uses /dev/dsp to play sounds and because of that aMSN cant use it in the same time.
Is there anything I could do about this?

---

### Post by blackfile on 2008-12-04
i solved with 

# apt-get install libsnack2-alsa

bye:p

---

### Post by RuleMaker on 2008-12-04
In order to install libsnack2-alsa I have to remove libasound2 and it takes more than 150 packages with itself (which I need).
Is there a way to replace the libasound2 with libsnack2-alsa without losing a lot of packages I need?

---

### Post by Vince4Amy on 2008-12-04
Go into the preferences and change audio playback to 

aplay $sound

That should solve it because you'll use aplay instead of snack for audio playback.

---

### Post by RuleMaker on 2008-12-04
Doesn't help either #-o

---

### Post by Vince4Amy on 2008-12-05
Are you running Ubuntu 8.04 (Hardy)? There was a bug with pulseaudio when I used it which caused this problem and there is a fix on this forum. I won't post it until I know that you're using Hardy to avoid confusion.

---

### Post by RuleMaker on 2008-12-12
I solved this, here is how:
```
sudo apt-get install esound
```
And in aMSN options check "Use a different program" and type:
```
esdplay $sound
```

Cheers

---

