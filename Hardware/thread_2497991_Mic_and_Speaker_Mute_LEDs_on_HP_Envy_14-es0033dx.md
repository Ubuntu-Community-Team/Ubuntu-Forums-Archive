---
title: "Mic and Speaker Mute LEDs on HP Envy 14-es0033dx"
date: 2024-05-25
forum: Hardware
---

### Post by belecjm on 2024-05-25
Hi,

I am running 24.04 amd64 on kernel 6.9.1. I am trying to get the speaker and mic mute LEDs to work on my HP Envy 14-es0033dx. I have found a few bits of old information on HP machines and tried a few things to get it to work with no success. The most I have been able to do is use the hda-verb command to manually turn the LEDs on and off. I have also tried various snd-hda-intel options in the /etc/modprobe.d/alsa-base.conf file, such as "options snd-hda-intel model=hp-mute-led-mic3", but currently have them all commented out.

```
grep Codec /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC245
/proc/asound/card0/codec#2:Codec: Intel Raptor Lake P HDMI
```

```
#mic mute led on:
sudo hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_MASK 0x16 && sudo hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DIR 0x16 && sudo hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DATA 0x00
#mic mute led off:
sudo hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DATA 0x04
#speaker mute led on:
sudo hda-verb /dev/snd/hwC0D0 0x20 0x500 0x0b && sudo hda-verb /dev/snd/hwC0D0 0x20 0x400 0x08
#speaker mute led off:
sudo hda-verb /dev/snd/hwC0D0 0x20 0x500 0x0b && sudo hda-verb /dev/snd/hwC0D0 0x20 0x400 0x00
```

---

