---
title: "Deleted audio driver"
date: 2012-06-16
forum: Hardware
---

### Post by couvrir on 2012-06-16
I had microphone problems with Skype after installing 12.04 on my Acer Aspire TimelineX 3830T and was googling around for solutions. Unfortunately one of them involve deleting all audio drivers, so now /proc/asound/cards is empty.

- How do I find out which card is on my laptop?

- How do I install the correct driver for this card?

Thanks!

---

### Post by Yellow Pasque on 2012-06-16
The kernel module is snd-hda-intel.ko . You should reinstall the kernel image package. That's the one with all of the sound modules:
```
sudo apt-get install linux-image-`uname -r`
sudo /usr/sbin/alsa force-reload
```

If you still have issues, please link to whatever guide/"solution" you followed. Alsa info would be helpful too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

