---
title: "soundcard vanished"
date: 2008-05-12
forum: Hardware
---

### Post by Zyphrexi on 2008-05-12
no sound.

checking preferences > devices doesn't show a sound card. Nothing really changed afaik, it just poofed.

---

### Post by zenwalker on 2008-05-12
modprobe will tell u if a sound driver has been loaded r not. If not, u can download a Alsa package and install.

---

### Post by Zyphrexi on 2008-05-12
well I honestly don't know what module it uses. And alsa is a soundserver...

EDIT: ok apparently there's something with the module and the 2.6.24-17-generic kernel... I'll have to stick with the 2.6.24-16-generic for now.

---

