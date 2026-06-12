---
title: "[SOLVED] Windows finally open on the correct screen! Yay!"
date: 2008-08-02
forum: General Help
---

### Post by Clappy on 2008-08-02
I am running Ubuntu 8.04, with an Nvidia card, running twinview with a Samsung 226BW on my right and a TV on my left.

My problem was that programs would open on my TV instead of the monitor. I found some old patches for Metacity from bug reports that would fix the problem, but I don't have the know-how to be able to apply the patches and rebuild Metacity properly.

I found a workaround which fixed another problem I was having which caused me to have to turn off visualization effects under Metacity.

The fix? Use Compiz instead of Metacity! here's how:

run from console:
```
compiz --replace &
```

and bingo! *All your problems are solved. I'm not sure exactly how it's doing it, perhaps it's choosing the screen with the mouse on it, or maybe it remembers the last setting, but it works for what I want it to do.


*Ok, not all your problems, but let's face it, you weren't going to fix those other ones anyway :)

---

