---
title: "Wrap Alsa devices to Oss"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by Almighty Ju on 2007-08-31
Hi all,

What I'm trying to do sounds really simple to me but i just cant get it to work, my sound card is a cmi8788 chip which works fine with the oss driver, what i want to try and do is get alsa to use the oss devices so when i use the gnome-volume-control it uses the oss device through alsa. Then hopefully i can use the volume control buttons on my keyboard :)

I've looked at google and found out about the oss compatability layer and added the following to /etc/modules.d/aliases which i got from [http://www-old.alsa-project.org/~iwai/OSS-Emulation.html]("http://www-old.alsa-project.org/~iwai/OSS-Emulation.html")
```
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

I Hope someone can point me in the right direction or even easier know of a tray icon to control oss and a way to get my keyboard to change it :D

Thanks,
Julian

---

