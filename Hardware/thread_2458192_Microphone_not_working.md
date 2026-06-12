---
title: "Microphone not working"
date: 2021-02-18
forum: Hardware
---

### Post by maria3791 on 2021-02-18
Hello,
I have an Acer SF314-55 with Ubuntu 20.04 and the microphone is not working. First I experienced while using Zoom or WhatsApp. Today I installed several voice recorder applications and it still doesn't work. Any advice on how to fix it? Thanks!

---

### Post by CelticWarrior on 2021-02-18
Welcome.

First of all please check at Settings > Sound if the correct input device is select and the levels.

---

### Post by maria3791 on 2021-02-18
I just did the following:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio pavucontrol
sudo alsa force-reload
reboot
sudo add-apt-repository ppa:mikhainov/pulseeffects
sudo apt-get update
sudo apt-get install pulseeffects
reboot

After those steps I finally got options in Sound Input area - Analog-what-so-ever was gone. The microphone is working in WhatsApp desktop application, but when I joined Zoom, no audio was working (no microphone, I couldn't hear the other person). Please, advise. Thanks.

Multimedia on Linux is lunacy.

---

### Post by CelticWarrior on 2021-02-18
If the microphone works with one software, it works.

When it doesn't work with one or more specific softwares but, again, works system wide, that's a problem with those softwares. Please check the settings.

---

### Post by maria3791 on 2021-02-19
Thank you!

---

