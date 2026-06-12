---
title: "Poor sound quality using Sigmatel on Dell laptop"
date: 2009-11-01
forum: Hardware
---

### Post by jazzvibes on 2009-11-01
Hi,

I know there is loads of people on the Internet complaining about Dell's Sigmatel sound quality. However, I have just installed Karmic, and it doesn't seem to be resolved. The best solution i have found is this

[http://ubuntuforums.org/showthread.php?t=476146](http://ubuntuforums.org/showthread.php?t=476146) which i believe still worked in 8.10 (i skipped 9.04), but I can't seem to get it to work now.

Any ideas?
Here is some info about my system. 
Dell M1210 XPS

```

$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9221 A1

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa

```
Thanks

---

### Post by jazzvibes on 2009-11-19
bump.

To clarify the problem is crackling sound when the volume is too high.

Does this happen on other setups too?

---

### Post by jazzvibes on 2009-11-19
Hmm isn't this a little embarrassing ... I think i've solved the issue by changing the default output in the Sound Prefernces to Analogue Stereo duplex to a different setting (the x.1's didn't work great either) so i've gone with 4.0 stereo output and an input which looks like it probably matches my three actual plugs on my laptop.

sound is now great from the two headphone sockets... i don't have a 5.1 system to try the full specified capabilities of the card, but this is enough at the moment.

---

