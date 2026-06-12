---
title: "Sound problem solved in 9.04 amd64."
date: 2009-04-25
forum: Hardware
---

### Post by marcoslai on 2009-04-25
I'm using 9.04 amd64 on my Conpaq Presario CQ40-115AU notebook. It was mute after clean installation,but now the sound is crispy & loud! What i did is :

Open terminal,key in: sudo gedit /etc/modprobe.d/alsa-base.conf

Insert the following :

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

save & restart.
:-P

---

