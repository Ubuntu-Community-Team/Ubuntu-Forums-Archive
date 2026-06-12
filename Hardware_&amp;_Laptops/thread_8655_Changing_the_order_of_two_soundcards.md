---
title: "Changing the order of two soundcards"
date: 2004-12-19
forum: Hardware &amp; Laptops
---

### Post by tfyp on 2004-12-19
I have two soundcards installed, an old soundblaster and a Terratec card. On my previous Linux installation (SuSE 9.1), the soundblaster card got the highest priority, making it the default soundcard for all applications. I switched the priority of the cards in order to fix this using the tools that came with SuSE, but I have no idea how to do this on my new Ubuntu installation, where the same happened. Can anyone tell me how to do this using the CLI? (I hope my description was good enough...)

EDIT: I figured it out myself. I switched the names of /dev/dsp and /dev/dsp1. The problem now is that it gets reset each time I reboot...

---

