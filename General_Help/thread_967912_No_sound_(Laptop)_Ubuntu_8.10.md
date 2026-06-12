---
title: "No sound (Laptop) Ubuntu 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Danny1337 on 2008-11-02
Well first I have to say I'm new to Ubuntu, I just installed it yesterday on my laptop (Acer Aspire 6920G)
Everything seemed to work perfectly well except the sound. There was a red cross next to the speaker icon, until i installed alsa drivers. The cross disappeared but the sound still doesn't work. Any ideas?

[[IMG]http://img220.imageshack.us/img220/5306/screenshotwp1.png[/IMG]](http://imageshack.us)
[[IMG]http://img220.imageshack.us/img220/screenshotwp1.png/1/w1366.png[/IMG]](http://g.imageshack.us/img220/screenshotwp1.png/1/)

---

### Post by probin51 on 2008-11-02
Hi Danny,

if you look at the picture yo snt, you'll see that the "PC Speaker" is still turned off (under the two slider controls).

Click this (so that the red coss is away) and you should get sound.

---

### Post by Danny1337 on 2008-11-02
I just tried that but it didnt work =/

---

### Post by onfyreforjesus on 2008-11-03
sudo killall pulseaudio

sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

---

### Post by deaimon on 2008-11-04
I actually have the exact same problem, and the exact same laptop.

So far those solutions haven't worked, :(.

---

### Post by N00bB00b on 2008-11-04
Acer Aspire 3680 - same problem - no sound - solutions no help

---

