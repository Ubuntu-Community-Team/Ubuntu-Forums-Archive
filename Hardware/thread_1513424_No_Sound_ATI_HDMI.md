---
title: "No Sound ATI HDMI"
date: 2010-06-19
forum: Hardware
---

### Post by Spechal on 2010-06-19
Hello all.

I have lost sound after an update using the Update Manager on 9.10 desktop x32.

I have uninstalled alsa and pulseaudio and even gstreamer and reinstalled them.  I have downloaded the alsa driver from realtek and installed it.

VLC player plays but I have no audio.
Mute is not on.
Volume is maxed.
alsamixer reports the ati card

lspci | grep -i audio
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

cat /proc/asound/card0/codec#* | grep Codec
Codec: ATI R6xx HDMI

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help would be appreciated.

---

### Post by Spechal on 2010-06-20
:(

---

### Post by kingzing1 on 2010-06-20
I'm also having issues with HDMI sound. Any thoughts?

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Using Intel Core 5, dual monitors (Asus VH242), and nothing is muted. That said S/PDIF is at 00 and I can't figure out a way to increase this.

---

### Post by Spechal on 2010-06-21
My kernel is 2.6.31-22 generic ... hopefully that helps.

---

### Post by rick_ca on 2010-12-10
Anyone ever get this figured out?

I'm having the same problem right now using Ubuntu 10.10 with an ATI Radeon Xpress 1200 Series (RS600).

---

