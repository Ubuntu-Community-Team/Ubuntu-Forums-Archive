---
title: "Sound in acer 6920G"
date: 2009-01-28
forum: Hardware
---

### Post by matmat07 on 2009-01-28
In the firsts boot of kubuntu, I had no sound. The aplay -l command worked. I tried to seek solutions which got things worst. One of them was the attached script. I tried to remove some of the things it did, but I'm a new users and I don't understand every command. Anyway, now the aplay -l command doesn't show the devices. I must do the following command to make the sound work:
```
sudo modprobe snd-hda-intel
sudo /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

```
But I must do them at each boot for an unknown reason. After booting kubuntu, the sound doesn't work again. Here's the output of the command when it works:
```
**** List of PLAYBACK Hardware Devices ****       
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by applefreakpeeps on 2009-04-23
You neednt manually type it in everytime.. just add this hda-verb command alone to your /etc/rc.local file before the exit line

---

### Post by matmat07 on 2009-04-26
Thanks for your help, I found out later this was the step I missed

---

