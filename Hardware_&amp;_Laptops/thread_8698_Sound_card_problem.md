---
title: "Sound card problem"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by ReiKn on 2004-12-20
I have 2 soundcards and I'd like to use only the MD-Port AN-1 sound card with alsa-drivers. However, as you can see from the linked picture, there shows up also a soundcard from my motherboard (the Intel one) and my tv card. At the moment all sounds go to the Intel moutherboard card. Also OSS mixer is visible. So what I'd like to do, is use only MD-Port AN-1 with alsa drivers. I don't want to disable the motherboard card from BIOS because I need it when doing music stuff in XP. 
[Picture of my sound mixer](http://www.students.tut.fi/~apajalah/mixer.jpg).
Don't get confused of the finnish language there  :smile:

ps. is there a way to make the mixer fit in the page?

*edit: found out that brooktree was my tv-card-driver*

---

### Post by ReiKn on 2004-12-20
Got it working. Forced esd to use the USB soundcard by esd -d hw:1.

---

### Post by 2424335596 on 2007-05-15
> **ReiKn said:**
> Got it working. Forced esd to use the USB soundcard by esd -d hw:1.


[Eminem skin treatment Yahoo build Equity Line Credit](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

