---
title: "Lost sound"
date: 2012-08-20
forum: Hardware
---

### Post by p0o9I on 2012-08-20
Hello,
My sound suddenly stopped working. I dont know what and where happened.

I have Kubuntu 12.04 x64. (Czech version, so everything is translation)
Kmix says something like "Empty output", theres no visible sound card, nor Phonon or Pavucontrol sees any sound device.

On the other hand, Alsamixer sees all the sound devices (3), according to "lspci -k" the cards are connected and using proper driver.

"cat /proc/asound/conf" also returns list of all cards. "aplay --v something.wav" seems working (print some information and such) but is not hearable

I tried unninstaling the pulseaudio -> soundcards were visible in Kmix but not usable :( So I tried installing it back and everything is as described originaly.

From windows is sound working quite nice.

Thanks a lot.

---

