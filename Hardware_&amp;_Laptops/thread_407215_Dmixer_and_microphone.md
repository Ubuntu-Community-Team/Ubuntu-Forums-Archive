---
title: "Dmixer and microphone"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by survient on 2007-04-11
Ok, got the dmixer working for alsa, trying to get my microphone working. Nothing doing. I tried using OSS, but to of no avail. I know dmix is only for output, I just am trying to figure out how to get my microphone working on feisty with alsa, with the dmixer enabled.

---

### Post by naseem on 2007-04-16
I have same trouble here, since I set the dmix the micro is not recognized anymore, if I run a test this is what I get: gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Risorsa occupata o non disponibile.

ok just tested and to get the micro back I set in sound settings all to asla, backuped and delated the .asoundrc file in home and I have my micro back to work.

now I'd like to have it working with the 5.1 surround and the dmixer so I can also use virtualbox and hear both os sounds.

since the trouble is fore sure in the .asoundrc file, can anyone post a good configuration of this file to get all tree things working at a same time

dmix
5.1
and micro working.

thanks!

---

