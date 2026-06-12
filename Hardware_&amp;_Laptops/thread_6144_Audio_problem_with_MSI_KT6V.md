---
title: "Audio problem with MSI KT6V"
date: 2004-11-25
forum: Hardware &amp; Laptops
---

### Post by ghetto on 2004-11-25
Hi all,
I've just installed Ubuntu on a PC with a MSI KT6V motherboard.
There is no errors from the system but the audio don't work.

The audio card is onboard:

AC'97 link controller integrated in VIA 8237
5.1 channel audio supported by Realtek ALC655 codec

Any ideas?

Thank you

ghetto

---

### Post by taygan on 2004-12-10
have you double checked that you turned the mute off under multimedia>volume control?  I've got an ASUS k7v600-x with the via8237..  Sound does work with the alsa82xx driver, but I've heard there's a new patch in the 2.10 kernel that will specifically work with the 8237, as the 82xx only officially work through 8235 (I believe).

good luck.

---

