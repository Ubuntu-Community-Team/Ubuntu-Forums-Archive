---
title: "[SOLVED] Vaio Notebook Headphone problem"
date: 2009-01-05
forum: Hardware
---

### Post by ribaluigi on 2009-01-05
Hi!
I've got a problem with my Sony Vaio NS if I plug my headphon the speaker does not mute.
I've resolved this thanks to Italian Ubuntu forum (link:[http://forum.ubuntu-it.org/index.php/topic,238622.0.html](http://forum.ubuntu-it.org/index.php/topic,238622.0.html)).
I decided to report the solution here:
1)Open the terminal
2) become superuser (digit: sudo -s)
3) digit: gedit /etc/modprobe.d/alsa-base
4)add the following line:
```
options snd-hda-intel model=sony-assamd
```
5)save
6)reboot

Hope this will be useful!

---

