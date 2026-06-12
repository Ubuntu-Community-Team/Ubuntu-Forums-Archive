---
title: "UbuntuStudio and Intel HDA ICH8 audio"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by maxalken on 2007-10-26
I have installed UbuntuStudio amd64 on my notebook which has an **Intel HDA ICH8 audio** chip. It is quite easy to get the sound chip work with the **generic kernal** by ***sudo apt-get install linux-backports-modules***. However it does not work with the** rt kernal**. It seams that linux-backports-modules-rt does not include the new alsa module which works. I have tried to install linux-backports-modules-rt, but the microphone does not work. I also tried to compile the alsa source manually, it still does not work.

Does anyone know how to make the sound chip work with 2.6.22-14-rt kernel?

---

### Post by HoneyGutClusters on 2008-03-19
Do this in a terminal;

```

sudo /etc/init.d/alsasound stop
sudo /etc/init.d/alsasound start
sudo modprobe snd-hda-intel

```

Does doing that get the sound to work for you? I'm working on this one too. Reloading the module gets sound working for me, Of course, it breaks again on reboot...

---

