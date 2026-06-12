---
title: "Cracking sound on HP compaq NX6310 ubuntu Gusty"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by T0ddan on 2007-10-12
Hello

I have an HP Compaq NX6310 laptop. I just recently installed Ubuntu 7.10 Gusty Testing on it. Every thing works perfect but there is one problem. The sound is cracking, I have been searching after an solution on Google and Ubuntu forums but i haven't found any.

The sound chip in my computer is Intel HDA. Please tell if you need any more information about my computer to solve this problem.

//T0ddan

---

### Post by ricardoec on 2007-10-15
I have the same problem with my HP NX8440 and here is the issue:

In Feisty, I had my email client play a "you got mail".wav soud every time a mail would arrive. (attached). It did it fine.

In Gusty, the wav gets chopped and also crackes and does not repeate


This is Gusty RC

---

### Post by Rien91 on 2007-10-16
I've had the same problem after upgrading to gutsy. In order to solve it, I've set the main volume a bit lower (the volume-control of rhythmbox) - I've had the same problem with Windows XP.

---

### Post by Hakujin on 2007-10-16
Try adjusting the PCM volume (volume control >> PCM volume sliders) down a bit. This should fix your cracking problem. (Too much gain)

---

