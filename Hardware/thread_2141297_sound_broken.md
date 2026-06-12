---
title: "sound broken"
date: 2013-05-02
forum: Hardware
---

### Post by eagle275 on 2013-05-02
Right out of the Lubuntu 13.04-box the sound on my Alienware Aurora m9700 laptop worked flawlessly - whether audacious or playing movies. 
Then I needed to compile and build wine, so I installed various packages which the ./configure deemed necessary... including OSS and other. 
Now I dont have sound - alsamixer doesnt work saying "File or Directory not found" though I installed alsa-utils
I'm kinda new to linux - so I'm at a loss - so many things Pulse audio ? alsa ? OSS ? ..

One thing I discovered - after installing pavucontrol it says "dummy output" and no hardware output devices - although lspci -v shows that lubuntu is aware of my onboard sound device (nvidia - chipset HD-audio / 97 )
so I think the players all "link" to that dummy output and so I dont hear a thing - how can I set up my lubuntu to use the real sound device again ?

As I dont know what you would need to me to post (logs and so on) please tell if you need further data 

Any help really appreciated

---

