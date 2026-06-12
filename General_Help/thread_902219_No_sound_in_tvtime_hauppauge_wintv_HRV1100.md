---
title: "No sound in tvtime hauppauge wintv HRV1100"
date: 2008-08-27
forum: General Help
---

### Post by ene_dene on 2008-08-27
I use tvtime to get analog picture from my Hauppauge card. I get the picture but no sound. I found out that you need to route sound, whatever that means, by a command:
```
arecord -D hw:1,0 -c 2 -r 32000 -f S16_LE -t wav | aplay -
```
Now I get the sound, but have a synchronization problem, there is an offset between picture and sound by, lets say 0.2s, which is quite visible.
Does anyone know the solution to this problem?

---

