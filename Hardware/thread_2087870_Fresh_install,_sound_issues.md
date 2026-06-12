---
title: "Fresh install, sound issues"
date: 2012-11-24
forum: Hardware
---

### Post by binaryperson on 2012-11-24
Hello.
I installed Kubuntu 10.04 LTS AMD 64 and I didn't have any audio at  all. Realtek ALC887 appears to be the audio chip. I fixed the problem by following the instructions here:

[HTML]http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html[/HTML]```
sudo gedit /etc/modprobe.d/alsa-base.conf
```I added the line:
```
options snd-hda-intel model=generic
```The volume works but it seems a bit low. But if I turn it up to max it is all right. The main issue is that my mic doesn't work at all. Neither rear nor front jack. Another issue is that when I plug in my headphones into the front jack, the rear jack remains on so I have sound coming out of my speakers and headphones at the same time. Is there a way to have the rear jack disable when I plug in the front?

---

