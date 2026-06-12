---
title: "Sound doesn't work for totem/ mozilla - Hardy"
date: 2008-07-24
forum: General Help
---

### Post by grogger13 on 2008-07-24
I started getting errors for totem with "internal data flow error" then I got "The audio device is busy. Is another application using it?"

---

### Post by majikhotline on 2008-07-24
I have to reformat my HDD and now the sound doesnt work and i also get the same error message.... what is going on here????????

---

### Post by grogger13 on 2008-07-30
No reformat for me, i had this install working pretty good for a while and for no obvious reason with just system updates my totem and mozilla video and sound stopped working

---

### Post by schmidtbag on 2008-08-08
i'm getting that issue too, except only totem xine can't play.  totem gstreamer works, firefox works, everything does but xine, and thats the only form of totem that plays everything i want.


EDIT:
I found out later that PulseAudio is the cause of this.  Just shut it down and everything works fine.  I'm not really sure how much the system relies on it, or whether it does at all.  By the look of the description, it seems important, but the fact that it works on Windows too (which doesn't need it whatsoever) makes me question if its just a convenience for some.

---

