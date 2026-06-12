---
title: "Sound in Dell XPS 13 9360 with Ubuntu 18.04"
date: 2018-07-12
forum: Hardware
---

### Post by muadnu on 2018-07-12
I just installed Ubuntu 18.04 on my Dell XPS 13 9360 laptop (version with Windows pre-installed) and I'm having some weird issues with the sound card. It seems not to be recognized ("lspci | grep audio" shows nothing) and in the sound settings no devices are shown. So in particular I can't use the fn keys to change volume, etc. But many applications do have working sound (chrome, skype and slack as snap applications, rhytmbox), although not all (firefox doesn't, nor for instance the gnome sound recorder application or signal as a snap appl.). Running  "alsamixer output" does yield something, it shows and allows to change settings for "Card: HDA Intel PCH - Chip: Realtek ALC3246". Maybe I'm missing some driver? But I can't find any solution anywhere, even though sound issues with this laptop and Ubuntu have been asked about often on other forums. BTW, sound worked with Windows and some other Linux distros (Fedora 28 in particular).

---

