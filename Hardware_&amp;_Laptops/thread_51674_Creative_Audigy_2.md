---
title: "Creative Audigy 2"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by zirus1701 on 2005-07-24
Does anyone know where I can find, or does anyone have the ubuntu driver for the Creative Audigy 2 5.1 surround sound card?


Edit: I feel like such a n00b... I should have read the sticky first.  But I'm still not sure if that will work, since I have a 5.1 surround sound card.

---

### Post by kleeman on 2005-07-24
Exactly which Audigy 2 card do you have? The sticky refers to the value card. Most other versions should work much more easily eg mine which worked out of the box (I have 5 speakers and the surround sound is great). What does
sudo lsmod | grep snd

give?

---

### Post by zirus1701 on 2005-07-25
sudo lsmod | grep snd

snd_bt87x              12932  3
snd_pcm_oss            52132  0
snd_mixer_oss          19680  3 snd_pcm_oss
snd_pcm                94696  2 snd_bt87x,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  7 snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  3 snd
snd_page_alloc          9732  2 snd_bt87x,snd_pcm

I know its not the value card... its the 5.1 surround sound card.

---

### Post by kleeman on 2005-07-25
I strongly suspect you have another onboard soundcard that is conflicting with the audigy. To check this try

lspci | grep -i audio
and post output.

It may be possible to disable the onboard card in your bios. If you do not want (or cannot) to do this then you need to set up for multiple cards in alsa which will require a little work......

---

### Post by aberflasm on 2007-07-31
Hello I have Creative Labs SB Audigy (rev 04) aka Audigy 2 Platinum SB0240P. I need some guidance as to how to enable surround sound on my 5.1 speaker setup. I found [these instructions]("http://www.linuxforums.org/forum/ubuntu-help/94148-surround-sound-ubuntu.html") useful but was hoping for a better solution.

Sorry for bumping such an old thread. I checked the date before replying but somehow missed the year.

---

### Post by kleeman on 2007-07-31
More instructions here:
[http://www.linuxtricks.net/index.php/archives/121/how-to-set-up-surround-51-audio-in-linux-with-alsa/](http://www.linuxtricks.net/index.php/archives/121/how-to-set-up-surround-51-audio-in-linux-with-alsa/)

---

### Post by aberflasm on 2007-08-01
> **kleeman said:**
> More instructions here:
[http://www.linuxtricks.net/index.php/archives/121/how-to-set-up-surround-51-audio-in-linux-with-alsa/](http://www.linuxtricks.net/index.php/archives/121/how-to-set-up-surround-51-audio-in-linux-with-alsa/)

Thank you :)

---

