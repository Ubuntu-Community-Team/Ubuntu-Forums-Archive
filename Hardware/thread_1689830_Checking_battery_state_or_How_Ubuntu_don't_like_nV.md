---
title: "Checking battery state or How Ubuntu don't like nVidia"
date: 2011-02-17
forum: Hardware
---

### Post by janlan on 2011-02-17
I have Lenovo Ideapad V460 with 2 graphic cards (one is integrated, second is nVidia). After installing Ubuntu 10.10 (and also with Xubuntu 10.10) system asked me to update nVidia driver (because that one used wasn't supporting 3d effects and other stuff). So I did it and my laptop didn't boot again. Boot process stopped with Checking battery state. This is quit [common problem]("http://www.google.com/#hl=en&&sa=X&ei=akBdTcTXLY2j4QaymrjBCw&sqi=2&ved=0CBUQvwUoAQ&q=ubuntu+checking+battery+state&spell=1&bav=on.1,or.&fp=b5fc6a07c812d0bf") on Ubuntu, I guess. Does anyone know solution for this? [This one ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/367078")didn't help.

---

### Post by janlan on 2011-02-17
OK, so I have a solution. Is is necessary to turn off switching of graphic cards in BIOS (from switchable to discrete).

---

### Post by panfist on 2011-03-14
I have an integrated Geforce 6150 LE and this didn't work for me, because there is no discrete graphics switching options. This chipset is too old for that.

---

