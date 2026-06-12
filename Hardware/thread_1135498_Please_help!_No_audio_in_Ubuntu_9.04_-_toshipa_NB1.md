---
title: "Please help! No audio in Ubuntu 9.04 - toshipa NB100"
date: 2009-04-24
forum: Hardware
---

### Post by moneer961 on 2009-04-24
Please help!
No audio in Ubuntu 9.04 
i have toshipa NB100
:(

---

### Post by rauder on 2009-05-24
I also had a problem with sound from my NB100, until I figured out that I was getting sound from the headphones, but nothing from the speakers. No great loss, the speakers are not that good... I was initially confused by this, as the snd_hda_intel module was loading and I couldn't find any obvious errors.

FWIW, the "fix" was to go to alsamixer and increase the level of the Speaker control. Doh!

Oh, and I'm running Jaunty UNR from a netboot image, I couldn't get USB booting to work. NB100 is a PLL10A-01E02H. Otherwise everything worked fine out of the box. Jaunty UNR is great!

---

