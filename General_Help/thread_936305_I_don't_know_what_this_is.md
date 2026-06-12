---
title: "I don't know what this is?"
date: 2008-10-02
forum: General Help
---

### Post by thomashome on 2008-10-02
Hi sorry about this but did you know in Ubuntu 8.04 Hardy Heron! When I try to use Firefox and flash etc. sound works perfectly but when I try to use VLC... No Sound??? when I do it the other way around try using VLC then go onto Firefox to play flash there is no sound. Is this something to do with the 100,000 mixers in ubuntu or is it a bug! When I see crap like this I don't know what to say!

---

### Post by Ryadt on 2008-10-02
Just do ```
killall pulseaudio
```
Go in System > Preferences > Sounds and switch everything to ALSA.

---

