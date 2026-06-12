---
title: "sound does not work"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by milou on 2007-01-03
I have Edgy installed on a D900t laptop (like Sager 9860, Peutium 4, ALC 880 realtek sound)
Sound simply does not work. When I try to play sound :

aplay /usr/share/sounds/generic.wav 
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
aplay: main:547: Erreur d'ouverture audio: Argument invalide

This bug appeared in Dapper with my laptop, sound was ok before. In dapper I noticed that compiling alsa from source with debug=detect allowed the sound to work, though at each end of sound, a bunch of debug info appeared in dmeg etc... but at least it worked.

Now, I installed edgy, and sound does not work at all, even with a self-compiled alsa with the debug option activated  !!! I always get the above reported  result. 

I must also mention that surprisingly, alsamixer/amixer seem to work ok, and do not give any suspect results.

Someone can help me please ?

Eric

---

### Post by nkassi on 2007-01-03
Try this: 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
or this 
[http://ubuntuforums.org/showthread.php?t=195434](http://ubuntuforums.org/showthread.php?t=195434)

Nic

---

