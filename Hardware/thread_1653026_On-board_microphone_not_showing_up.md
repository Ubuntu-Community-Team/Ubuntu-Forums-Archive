---
title: "On-board microphone not showing up"
date: 2010-12-26
forum: Hardware
---

### Post by Hsiu on 2010-12-26
Hello,

I'm trying to get the on-board microphone on my ASUS C90 working. When I open KMix, capture devices shows only Internal Audio Analog Stereo.

Please let me know any other information that would help in diagnosing this problem.

EDIT: For those having a similar problem, I solved this by running alsamixer (I thought alsa was superceded by pulseaudio, I didn't realize they're complimentary), tabbing or hitting F4 to get to the capture screen and changing input source to "Front Mic" instead of "Mic". There's a second one, Input Source 1, which I left as Mic. For good measure I made sure the mic volume was up and put the mic and front mic boost up a bit.

---

