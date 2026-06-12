---
title: "Integrated microphone doesn't work only with voip apps"
date: 2010-08-22
forum: Hardware
---

### Post by xaber1488 on 2010-08-22
Hi guys!

I have a huge problem! I bought a packard bell dot s2 134 and I installed uuntu 10.04 netbook on.
All the hardware is well recognised: the only problem is the microphone with voip apps.
If I use the sound recorder preinstalled in ubuntu, the microphone works great. I already activated all the tabs via alsamixer -Dhw and, I repeat, the sound reorder works great.
But when I use a voip app (skype, google talk or also amsn during its configuration) everything works great except the microphone, which the voip apps can't succeed in using with success.

Also, I tried to plugin an old logitech webcam with microphone and this one works totally great.

So, the problem is that the netbook integrated microphone works great with voice recorder, but when I use a voip app, it fails to work (also, skype and amsn do not provide any alternative config for the microphone: they refer to the alsamixer config if I am not wrong. They only have the pulseaudio(local) option).

Can anyone of you help me out? It's really important.

Thanks in advance!

---

### Post by xaber1488 on 2010-08-22
Sorry guys! Only a little up!

---

### Post by xaber1488 on 2010-08-23
Another little up!

---

### Post by roy913 on 2010-08-23
as far as i know, skype doesnt like pulseaudio. if you eager to get this working, try uninstall pulseaudio and install alsa. that's what i did for my netbook.

read this thread which there is an url to show how to achieve this:
[http://ubuntuforums.org/showthread.php?t=1159613&highlight=acer+aspire+d150&page=2]("http://ubuntuforums.org/showthread.php?t=1159613&highlight=acer+aspire+d150&page=2")

---

