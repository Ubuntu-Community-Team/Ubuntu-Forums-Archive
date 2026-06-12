---
title: "[SOLVED] Zalman ZM-RSSC soundcard not working"
date: 2008-10-01
forum: Hardware
---

### Post by gorelshv on 2008-10-01
Hello,
i have the zalman USB external soundcard plugged to my hp laptop.
i bought it so ican passthrough surround (AC3,DTS) sound to my receiver.
it works fine on windows XP (i'm Dual Booting) but the problem is that ubuntu identifies the card as USB AUDIO (as it should) but when i test it in
the control panel i hear no sound. the card itself has a LED the flashes when the card is receiving data. when i run the test the LED flashes but no sound coming out. i checked the mixer setting and i've tried using various players but nothing seems to help. help PLEASE!!!!:-k

Benny.

---

### Post by gorelshv on 2008-10-01
managed to solve the problem!
i went to synaptic package manager, searched for every thing that contained
the string "alsa" and marked every already installed package for reinstallation!

---

