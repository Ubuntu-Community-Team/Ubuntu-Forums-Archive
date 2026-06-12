---
title: "ALC1200 SPDIF not working"
date: 2010-02-05
forum: Hardware
---

### Post by tomek.vz on 2010-02-05
Well i dont know what to try anymore. I have an Asus M3N78-EM and cann't get SPDIF to work on karmic. I tried to put :

```
options snd-hda-intel model=6stack-dig probe_mask=1
```to alsa-base.conf and-nothing...i tried to make .asoundrc:

```
pcm.rate_convert {
    type plug
    slave {
        pcm "hw:0,0"
        rate 48000
    }
}

```...still nothing...i really have no idea what to do. The TOS kable lights up but my reciever just does not recognize anything (Jamo DMR40)...aplay -l says:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Am i missing something or what?

---

### Post by jasxun on 2010-03-28
The same here. Kinda lost #-o...

I am using a HP Slimline desktop PC.

---

### Post by tomek.vz on 2010-03-28
I gave up on it,bought the new board and connected optical coax on my reciever and it works like a charm.

---

