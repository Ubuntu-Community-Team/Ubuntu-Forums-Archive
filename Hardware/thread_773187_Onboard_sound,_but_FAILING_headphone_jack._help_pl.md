---
title: "Onboard sound, but FAILING headphone jack. help please!"
date: 2008-04-28
forum: Hardware
---

### Post by tmtan on 2008-04-28
Hey guys,
Im still learing Ubuntu, I know I have a ways to go, but I just installed Hardy Heron and the same issue that scared me away gusty gibbon came up.I LIVE on music! So heres the problem, I installed ubuntu on a Sony Vaio VGN-FZ140E, and the onboard speakers work(though the volume ratio is WAY off, but thats not the issue here), however the headphone jack does not, as with it the mic jack. When headphones are plugged in, the sound still plays through the onboard speakers, and nothing in the headphones. Help please! if yall have any questions, please ask, i would love to get this problem resolved, i will respond ASAP! Thanks guys!

Tyler

---

### Post by teaker1s on 2008-04-29
sounds like alsa issue, in terminal 
```
lspci
```
lets see what you have

---

### Post by tmtan on 2008-04-29
hey man, thanks so much for getting back to me! actually i figured out the problem, well, i fixed it anyways, i just followed another suggestion that i found @

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and had to manually specify the module parameters.

thanks again though man!... actually, the headphones work, but the volume ratio(when the volume is at 50%, there is ZERO sound) is off, and there is only sound in the left ear when the headphones are plugged in. if you know anything there that could help it would appreciated.

---

### Post by mano_j85 on 2008-08-20
hey guys...im using Asus A8v - vm motherboard...has installed Ubuntu linux...now im unable to record my voice through heradphone mic....do any one have any suggestions....pls...help me in resolving it....

---

