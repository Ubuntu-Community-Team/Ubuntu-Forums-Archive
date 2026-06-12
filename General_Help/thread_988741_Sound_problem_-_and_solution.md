---
title: "Sound problem - and solution"
date: 2008-11-20
forum: General Help
---

### Post by shacharh@eilat on 2008-11-20
I wanted to share a problem I've had on Xubuntu 8.10 with sound (I think that it's relevant to other ubuntu variants but I'm no expert, it's just a hunch).
about a week after installing Xubuntu sound suddenly disappeared due to some change I which didn't understand in Alsa settings.

I managed to restore sound by disabling asoundrc.asoundconf.
if you're having a sound problem, it might just be the same kind that I had.
If so, do this: go to the file .asoundrc in your home folder. find a line that references to another file in your home folder, one called .asoundrc.asoundconf - comment it by adding # in the beginning.

Hope this helps anyone.

Oh and I do apologize if this solution has already been posted before. I for one didn't see a post about it.. =)

---

