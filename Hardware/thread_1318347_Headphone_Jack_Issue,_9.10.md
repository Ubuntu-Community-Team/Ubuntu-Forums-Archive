---
title: "Headphone Jack Issue, 9.10"
date: 2009-11-07
forum: Hardware
---

### Post by Jweitz on 2009-11-07
Hello,

I am new to linux, and I have just installed Ubuntu 9.10 on my HP 6735s laptop. Everything seems to be working fine except my headphone jack. Nothing happens if I plug my headphones into it. The external speaker works just fine, but if I plug in my headphones, the sounds still comes out of the speakers. I don't know where to sever start looking for a fix. Any help would be appreciated. Thanks.

---

### Post by stefano_to on 2009-11-08
I had the same problem yesterday evening.

I solved by installing the "Alsa mixer" (from the software center, or from wherever you like!). Then you go to Applications--> Sound and Video --> Alsa Mixer, there you just have to tick the case "Headphone jack sense" and everything will work fine (the computer will automatically disable external audio when you jack your headphones in).
):P

---

### Post by citaworvk on 2009-11-30
Thank you this worked for me too. 

When I first installed 9.10 it worked fine. So either I changed something or an update changed something.

---

