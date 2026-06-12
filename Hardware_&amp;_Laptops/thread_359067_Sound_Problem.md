---
title: "Sound Problem"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by srt5 on 2007-02-11
Before I start, can I just show my support to all those who make an effort by offering help and advice through these forums. I have found many answers to my questions by browsing through the posts online and this has encouraged me to offer advice where I can.

I have recently made the switch from Windows XP to Ubuntu 6.10, and I definitely don't regret it! However, I am having some teething problems getting the sound to work with my laptop.

I am currently running Ubuntu on an Acer 5051 AWXMi laptop. The problem that I am experiencing is that no sound is played through my laptop speakers, but when I plug headphones in sound does come through (although only in mono).

I will be honest, I am not sure where to begin. Is this a sound card problem? Or is it just something that needs to be configured? It may also be worth noting that I can play CD's and audio tracks fine, but still I have to use headphones for this.

Any help or advice that anyone could provide will be much appreciated. Thanks in advance :).

---

### Post by budgie9 on 2007-02-11
As an Edgy user I think you will find this is a common thread through the forums. Perhaps a search of some like problems will help you.

---

### Post by srt5 on 2007-02-12
It seems as though there is a lot of problems regarding sound and Edgy. I can't seem to find a post which deals with my specific problem. I thought it may be a driver issue, so I followed the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") but still no joy :( .

It seems as though a sound device is being detected, but it doesn't know what the device is as I get "Unknown Device" appearing next to the audio device when i execute

```
lspci -v
```

in terminal. Does anyone have any other suggestions or has anyone encountered the same problem?

Hope you can help!

---

### Post by srt5 on 2007-02-13
Okay an update and maybe this will help people who are having simiar problems. After searching through a bunch of posts I came across one which suggested that adding a boot option:
```
pci=noacpi
```
when installing ubuntu will solve the sound problem. I've tried this and indeed it does :) Don't ask me why! It just does! The only pain is that I had to re-install Ubuntu. Don't suppose anyone knows how to change the boot options after installing!?

Cheers

---

### Post by surge89 on 2008-02-19
I think there is a way to update the boot option on ubuntu, but this is an install option is it not?

---

