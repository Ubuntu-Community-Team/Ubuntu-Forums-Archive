---
title: "No sound internal speaker"
date: 2010-04-07
forum: Hardware
---

### Post by wsgts on 2010-04-07
I have a Panasonic Toughbook CF-19 MKII.  The sound works perfect out the headset jack, but I am unable to get any sound out the internal speaker on the front.  I have never been able to on any Linux (tried Fedora as well). 

```
cat /proc/asound/card0/codec#0 |grep Codec
Codec: Analog Devices AD1884
``````

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
```

---

### Post by lidex on 2010-04-08
Open alsa-base.conf for editing (in a terminal="Applications>Accessories>Terminal"):
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom:
```
options snd-hda-intel probe_mask=1 model=3stack

```
Comment out this line - or similar (place a # in front of):
```
options snd-hda-intel power_save=10 power_save_controller=N
```

Save. Close. Reboot. Now check your levels in alsamixer:
```
alsamixer
```

---

