---
title: "ALSA Jack sense fails on Fujitsu p7120 Xubuntu 10.10"
date: 2011-01-14
forum: Hardware
---

### Post by robthebob93 on 2011-01-14
The sound chip is Intel HDA, ALC260. I have tried setting 

options snd-hda-intel model=fujitsu 

in /etc/modprobe.d/alsa-base.conf, but this hasn't made any difference. There is no "Jack Sense" option in alsamixer. I've also tried a couple of values for fix_position.

I've tried following the ubuntu wiki pages for Intel HDA and sound debugging in general, to no avail. When doing the jack sense test recommended on [https://wiki.ubuntu.com/ALSA/JackSense](https://wiki.ubuntu.com/ALSA/JackSense) the two files generated with and without the headphones plugged in were identical. This makes me think it is a driver problem. I attach the output of `cat /proc/asound/card*/codec*` in case this is of any help.

Really stumped, so thanks for any suggestions.

---

