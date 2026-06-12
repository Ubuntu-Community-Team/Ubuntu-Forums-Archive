---
title: "Sound issues on HP dv2210us"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by jiasheng on 2007-04-12
Hi,

I recently bought my new laptop, HP dv2210us which is one of the dv2000z series, using amd cpu, nforce chipsets and Conextant CX20549 sound chip.  Unfortunately, I cannot get the sound work within Kubuntu Feisty beta.  The sound card can be recognized correctly after the installation, but there is no sound at all.  I've checked the mixer settings and also tried the newest alsa driver which is 1.0.14rc3, but nothing has changed.  I also tried to add some model parameter after the module, which is the best way to make my sound card work properly on my Asus laptop, but got a failure this time.  As the driver seems to be installed correctly, no errors, no conflicts and the sound card can be recognized, I may guess there is some setting problems with the channels.  I only have very limited channels in the mixer, however.

I did a search on the web as well, it seems that someone who is using the same sound chipset also has problems with the headphones, but the speaker can provide sound.  In my case, neither the speaker nor the headphone can provide any sound.

Any help or suggestion would be appreciated.  Thanks all.

---

### Post by earthcreed on 2007-04-20
I have installed final 7.04 and tried the newest alsa driver, and this is still the case.  I have the same dv2000z, no sound at all.

---

### Post by jiasheng on 2007-04-20
ok, I have solved this problem and I think my guess was correct.
1.  Download and extract the newest HG alsa driver which has been patched for the chipset using by dv2000z.  I can not remeber the link, but I am sure I got it from a post in this forum.
2.  ./hgcompile
3.  sudo make install
4.  edit /etc/modprobe.d/alsa-base, add "options snd-hda-intel model=test".
5.  restart or reload alsa
6.  you may find a channel called "speaker" which is set to the lowest level by default, adjust the volume.  The "model=test" parameter makes it possible to control all the channels.  So if still no sound, please try to tune other channels.
7.  when you have sound, change the previous "model=test" to "model=laptop" and restart.
8.  now you can have the sound and the blue keys work properly, including the speaker auto-mute when headphone is plugged in.
good luck

---

### Post by hhemken on 2007-05-03
Jiasheng, could you please post the link? I have a fully updated Edgy Eft on a dv2210us and the headphones do not work, although the speakers do. Does anyone know if this is fixed in Feisty Fawn? Is the driver mentioned by Jiasheng newer or older than the current updates?

---

