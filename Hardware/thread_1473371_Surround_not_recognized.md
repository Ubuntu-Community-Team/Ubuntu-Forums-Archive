---
title: "Surround not recognized"
date: 2010-05-05
forum: Hardware
---

### Post by liquidator87 on 2010-05-05
Hi,

I'm on Ubuntu 10.04, my sound card ( HDA Intel - VIA ID 4428 ) is working only in stereo mode, how can I make the surround output work?

Thanks in advance

---

### Post by dino99 on 2010-05-05
install paprefs and gnome-alsamixer (tweak it as you need)

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-05-05
Use the pulseaudio volume control=Alt+F2; enter:
```
pavucontrol
```
Select the correct profile on the configuration tab.

---

### Post by liquidator87 on 2010-05-09
It was a driver problem, updated the kernel and now I can select surround outupd

---

