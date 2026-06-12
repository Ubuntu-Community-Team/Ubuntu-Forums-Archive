---
title: "sound outputs fine from builtin speakers, but only sometimes from headphone jack"
date: 2010-12-17
forum: Hardware
---

### Post by swordsmanluke on 2010-12-17
I just bought an Asus X52F-X1 and installed Ubuntu 10.04.1 64-bit on it.

It mostly works, but I'm having issues with the headphone jack. First, it wouldn't output from the jack at all, so I followed the instructions at [http://ubuntuforums.org/showthread.php?t=1489935](http://ubuntuforums.org/showthread.php?t=1489935)

That eventually led me to manually upgrade Alsa to version 1.0.23. 

Now my problem is that - sometimes - my laptop will play sound from the headphone jack AND the built in speakers; but mostly it only plays from the built in speakers and the headphone jack is muted.

I also tried following the instructions at 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But I wasn't sure what to do when I couldn't find my codec listed in the HD-Audio-Models.txt file referenced therein.

For reference, I ran the command:
```

cat /proc/asound/card0/codec#* | grep Codec

```
and this was the result:

```

Codec: Conexant CX20585
Codec: Intel G45 DEVIBX

```

---

### Post by swordsmanluke on 2010-12-19
Some more information:
It appears that if I put the laptop to sleep and then wake it up, the headphone jack sometimes starts working again. (I still get sound from the main speakers, but at least the jack is also producing signal.)

---

