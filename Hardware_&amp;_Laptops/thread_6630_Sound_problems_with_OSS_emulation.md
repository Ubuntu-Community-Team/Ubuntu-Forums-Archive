---
title: "Sound problems with OSS emulation"
date: 2004-11-30
forum: Hardware &amp; Laptops
---

### Post by wande on 2004-11-30
Hi,

I got alsa working with my second soundcard by editing ~/.asoundrc. Now I have problem with mplayer, which uses alsa OSS emulation by default? How I can choose the device for OSS sounds?

--
  Wande

---

### Post by wande on 2004-11-30
I managed to correct the problem by editing my /etc/modprobe.d/aliases file, now all Firefox plugins, mplayer, etc. work with sounds.

I added following lines to /etc/modprobe.d/aliases

alias snd-card-0 snd_emu10k1
options snd_emu10k1 index=0

alias snd-card-1 snd_cmipci
options snd_cmipci index=1

--
  Wande

---

### Post by Beastux on 2004-11-30
Thank you so much, Wande.

I had the same problem with my SB Live! Value and the MB sound chip and it works perfectly with your solution.  =D>

---

