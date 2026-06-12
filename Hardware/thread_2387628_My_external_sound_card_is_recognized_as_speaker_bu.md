---
title: "My external sound card is recognized as speaker but not microphone"
date: 2018-03-21
forum: Hardware
---

### Post by reinhardvdd on 2018-03-21
Hi everyone !

I'm a new ubuntu user. I use ubuntu 16.04 LTS
My external sound card is a Focusrite Saffire USB 6 that i used on windows to record sounds.

When i connect it on ubuntu, the sound settings of ubuntu show it as output connection like my speakers, but not as input connection (my microphone is connected to my card). I especially need it to record on audacity.

I found very few informations about that problem. Apparently, that card  should works fine on ubuntu, the problem is the step for to make it work  correctly. 
Some users use jack (with the same card, but they dont really have the  same problem like me, so even if i follow what they do, my problem isnt  solved.

Do you have any idea of what i should do ? Steps to follow ?

Thank you in advance for your help [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]

```
0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf320000 irq 323
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdf080000 irq 17
 2 [USB            ]: USB-Audio - Saffire 6 USB
                      Focusrite Saffire 6 USB at usb-0000:00:14.0-5, full speed
```

---

### Post by Yellow Pasque on 2018-03-21
Start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

