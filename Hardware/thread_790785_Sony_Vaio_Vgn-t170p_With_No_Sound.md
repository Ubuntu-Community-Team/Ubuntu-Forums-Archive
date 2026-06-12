---
title: "Sony Vaio Vgn-t170p With No Sound"
date: 2008-05-11
forum: Hardware
---

### Post by stargateQ on 2008-05-11
hi everybody 

i have a sony vaio vgn-T170 P ,and i installed the ubuntu 8.04 version , so far everything goes smooth except i don't have sound ,,
could anybody help me how i can manage with sound ?

thanks in advance 
:confused:

---

### Post by dishguy123 on 2008-06-08
I have a Sony Vaio VGN-T370P & I'm experiencing the same thing.  Everything works EXCEPT the sound!  Solution would be very helpful...

---

### Post by Nepherte on 2008-06-08
Let's figure out what sound card you have:
```
lspci
```
Look for an multimedia controller related to audio.

Does
```
aplay -l
```
gives you something?

---

### Post by bigsky34 on 2009-07-20
I am running with the latest version of Ubuntu Desktop 9.04 and having the same sound problem with a Sony Vaio vgn-t170p.

using lspci there appears to be no sound card found.  
Have done a number of google searches on this problem and still have not been able to get sound working.

Has anyone been able to get sound to work on this vaio model?

---

### Post by Niccity on 2009-07-26
Sadly this issue seems quite common. I have the same no sound problem running JJ 9.04 on a Vaio VGN-T1XP.

I have tried modifying the alsa mixer config file several ways as suggested on other fora  - however these were described as fixes for other vaio models - so I was not overly surprised they didn't work. 

Someone did suggest rolling back to HH 8.0x but that is a bit dramatic, and there doesn't seem to be a guarantee it would work anyway.

Any advice would be very welcome.

---

