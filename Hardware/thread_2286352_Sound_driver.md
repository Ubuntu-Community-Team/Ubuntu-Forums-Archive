---
title: "Sound driver"
date: 2015-07-11
forum: Hardware
---

### Post by lizard2014 on 2015-07-11
Hello. It seems that I need a driver for proper sound in Ubuntu 14.04.2 LTS. This is because after installing the audio driver in Windows 8.1, the sound is pretty loud but in Ubuntu, it is very low even with 100% volume level. How can I install the sound driver?

---

### Post by lizard2014 on 2015-07-11
In an attempt to install the driver from the RealTek website, now there is no sound at all. Someody please help. Here is the output of **sudo aplay -l**
```
aplay: device_list:268: no soundcards found...
```

---

### Post by lizard2014 on 2015-07-12
In an attempt to further install the sound driver, the system was unable to boot! Not even the recovery mode was loading. I finally had to format it. Now the sound is low but not as powerful as it is in Windows. Is there any driver in the Ubuntu archives itself so that it works and is safe to install?

---

### Post by dino99 on 2015-07-13
> sudo apt-get install paman
sudo apt-get install paprefs

then goto 'sound & video' menu > 'pulseaudio volume control' and set your tweaks as you wish

---

### Post by lizard2014 on 2015-08-04
I have finally come to know that my sound card is Realtek - ALC3227. Linux HDA drivers are available on Realtek's website, but this codec is not supported by any of those drivers. What can I do?

---

### Post by lizard2014 on 2015-08-04
After a lot of Google searches, here is a driver which I have found which has my codec menitoned. It is a C language code. What should I do with that driver? How do I install it? Here is a link of the driver which I have found: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c)

---

### Post by Yellow Pasque on 2015-08-04
The driver is already built into the kernel you are using (or else you wouldn't hear any sound at all).
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by lizard2014 on 2015-08-04
The driver I am using as of now is ***snd_hda_intel*** (but I have a Realtek sound card).

---

### Post by Yellow Pasque on 2015-08-04
> **lizard2014 said:**
> The driver I am using as of now is ***snd_hda_intel*** (but I have a Realtek sound card).

That's correct. Intel designed the standard ( [https://en.wikipedia.org/wiki/Intel_High_Definition_Audio#Host_controller](https://en.wikipedia.org/wiki/Intel_High_Definition_Audio#Host_controller) ), so any chip conforming to it uses the snd-hda-intel driver. You still haven't give a link to your detailed information as requested in the last post..

---

