---
title: "HDMI Choppy Audio Problem"
date: 2014-10-23
forum: Hardware
---

### Post by rockwinder on 2014-10-23
Hello everyone,

I am using a desktop PC with Asus M5A97 EVO R2.0 mainboard and a Turkish branded (Vestel) HD TV connected to my ATI 7790 graphics card via HDMI. 

In Windows 7 and 8, I needed to change some settings in Device Manager that I don't exactly remember, in order to get audio from TV (as I remember I had to install audio driver and uninstall it back, then choose AMD Hdmi Audio Driver in Device Manager).

I faced similar audio problem in my fresh install Ubuntu 14.04. This time, unlike Windows gave no audio at all before changing settings, in Ubuntu there are cracky, choppy, distorted - or whatever it called in English- sounds as you can hear in the video: [http://youtu.be/XWF4paWUL7A](http://youtu.be/XWF4paWUL7A)

This is not Ubuntu specific, I tried other distributions like Mint, Xbmcbuntu and Fedora.

I'm desperately waiting for your solutions.

Thanks in advance

---

### Post by Vladlenin5000 on 2014-10-24
Hi, welcome.

HDMI sound relies solely on your graphics card, apparently some AMD/ATI, and may require proprietary drivers to work properly.

---

### Post by Yellow Pasque on 2014-10-24
Try this (it's easy to undo if it does not work): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
Easy copy/paste command:
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Reboot and see if it works.

---

### Post by rockwinder on 2014-10-24
> **Temüjin said:**
> Try this (it's easy to undo if it does not work): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
Easy copy/paste command:
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Reboot and see if it works.

Tried but no success. I don't have a Intel hardware, is it related?

> **Vladlenin5000 said:**
> Hi, welcome.

HDMI sound relies solely on your graphics card, apparently some AMD/ATI,  and may require proprietary drivers to work properly.

I tried all of them: open source, fglrx, fglrx-updates. Still same.

I also changed some settings in /etc/pulse/daemon.conf as suggested in another post:
default-sample-rate=48000
alternate-sample-rate=96000

Now, it's a bit better but still not pure audio. It cracks randomly. In local or online video files, audio can be heard with small cracks (only the endings of sounds). But in games, it is ear-bleeding :)

Any other suggestions?

Best regards

---

### Post by rockwinder on 2014-10-27
Any help please? I don't want to turn back to Windows...

---

### Post by asansc on 2014-10-27
Hola, mi dispositivo de audio HDMI no aparece listado..

---

### Post by Yellow Pasque on 2014-10-27
Wouldn't you want the alternate sample rate to be 44100?

---

### Post by rockwinder on 2014-10-27
> **Temüjin said:**
> Wouldn't you want the alternate sample rate to be 44100?

I have no idea about the difference, but I tried changing it to 44100, still same...

---

### Post by rockwinder on 2015-05-09
This answer solved my problem in Ubuntu 15.04.

[http://askubuntu.com/a/529137](http://askubuntu.com/a/529137)

---

