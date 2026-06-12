---
title: "I solved sound card problem for Toshiba T2080"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by adameye on 2007-05-10
sudo apt-get remove alsa
then just follow: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
to install three packages alsa-driver, alsa-lib,alsa-utils.
(note: I use the newest one on that page,**1.0.14rc4.tar.bz2 ) 

but I bet you will met a problem about "curses lib" when you type ./configure in  ./alsa-utils-1.0.14rc4
so you also need to run [COLOR="Red"]sudo apt-get curse* [/COLOR]



thanks for those people who updated Alsa-1.0.14rc4!!!

---

