---
title: "Very loud sound."
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by ipodhacker on 2007-10-05
Hi,

I installed Ubuntu Feisty Fawn (7.04) on my Dell Inspiron 9200 laptop and the sound is EXTREMELY loud. It plays sound even when I set the volume down to 0 and put it on mute.
I had the same problem with Ubuntu Breezy Badger (5.10)

Can someone tell me how to fix this please?

Thanks, iPodHacker

---

### Post by ipodhacker on 2007-10-06
bump

---

### Post by Yhippa on 2007-10-06
I have a Dell XPS M170 so I don't know if the models are exactly the same.  I believe that our models have built-in subwoofers (ha!) in addition to the speakers so the software that controls the hardware apparently only take care of the two main speakers.

This was on the Ubuntu 7.04 Live CD.  I do not have a resolution.

---

### Post by nick_h on 2007-10-06
I assume you have already tried altering the levels in the *alsamixer* application.

---

### Post by ipodhacker on 2007-10-08
> **nick_h said:**
> I assume you have already tried altering the levels in the *alsamixer* application.

no?..?

---

### Post by nick_h on 2007-10-08
If you type:
```
alsamixer
```
at a terminal then you have access to all the volume controls of which the volume button only controls one.  I think Ubuntu may be set to change the master volume by default so it might not be of any help.  It is easy to check though.

---

### Post by ipodhacker on 2007-10-12
> **nick_h said:**
> If you type:
```
alsamixer
```
at a terminal then you have access to all the volume controls of which the volume button only controls one.  I think Ubuntu may be set to change the master volume by default so it might not be of any help.  It is easy to check though.

i'll try that later. i'm on openSuSE now

---

