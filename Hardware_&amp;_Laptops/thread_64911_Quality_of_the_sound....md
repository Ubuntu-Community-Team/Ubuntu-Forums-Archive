---
title: "Quality of the sound..."
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by sweetthdevil on 2005-09-12
Hi, i'm using Ubuntu on a Hp pavilion zd7377ea, with harman/kardon speaker, and the quality compare when in use with windows is crape, 

How can i do to improve the quality?  :roll:

---

### Post by Waqas on 2005-09-13
[QUOTE=sweetthdevil]Hi, i'm using Ubuntu on a Hp pavilion zd7377ea, with harman/kardon speaker, and the quality compare when in use with windows is crape, 

How can i do to improve the quality?  :roll:[/QUOTE]

I thought my ears were wrong, but then I realized the same thing.. every MP3 files in XMMS seems to easily reached it peak.. Or distorted at some loudest point. I suspect something to do with audio driver.

---

### Post by snop on 2005-09-14
Hi,

Same happened here. The only way I was able to solve this was tweaking alsa to use dmix (you should search the forums to find how to do this. Look for asound.conf or dmix). 

I believe that the problem is related to frequency transformations i.e. the card (or alsa, I don't know) works at 48Khz but esd (the sound server) at 44.1Khz

Note that with dmix esd might not be needed because is alsa how does the audio mixing.

SnOp

---

