---
title: "Multichannel audio"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by code-breaker on 2007-01-26
On windows, we use the port-audio library and asio (in a matlab dll called pawavplay) to access all 6 outputs of our Echo Gina 3G soundcards. 

I am considering a move from Matlab to octave (and a corresponding move from Windows to Ubuntu). I understand that asio is apparently not an option on linux for multichannel audio. Is there a different (any?) way to achieve multichannel playback?

---

### Post by 23meg on 2007-01-26
It's safe to say that the counterpart of ASIO in Linux is [JACK]("http://jackaudio.org/").

---

