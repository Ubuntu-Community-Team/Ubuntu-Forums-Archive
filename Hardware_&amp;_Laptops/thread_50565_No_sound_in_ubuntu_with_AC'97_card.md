---
title: "No sound in ubuntu with AC'97 card"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by linuxeiro on 2005-07-20
Hello. I have a Realtek AC'97 soundcard integrated in my PC's motherboard. It is not recognised by ubuntu/kubuntu and I can get no sound. How can I configure Kubuntu/ubunto so that it emulates a default sound blaster card? is there someway so that I can get any sound from my soundcard? If I enter "smod | grep snd" in a terminal, I get this. Thank you


snd_intel8x0 29984 1
snd_ac97_codec 64608 1 snd_intel8x0
snd_pcm_oss 47652 0
snd_mixer_oss 16768 1 snd_pcm_oss
snd_pcm 84872 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd 50276 8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer
soundcore 9824 1 snd
snd_page_alloc 9604 2 snd_intel8x0,snd_pcm

---

### Post by amohanty on 2005-07-21
> It is not recognised by ubuntu/kubuntu 

Do you mean it doesnt provide a name in the device manager, or that in the volume control-> change device it is not listed?

Also try muting everything that says IEC****.

HTH
AM

---

