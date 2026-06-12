---
title: "sound hardware issues (device doesn't seem to be recognized)"
date: 2014-12-23
forum: Hardware
---

### Post by tcll5850 on 2014-12-23
this is rather hard to explain...
we HAD audio, and then it just stopped...

pavucontrol reports audio feedback on output device but no sound plays through speakers.
every port on output config reports (unplugged)

devices:
- Digital Sterio (HDMI) **x4**
- Digital Surround (HDMI) **x4**

what has been tried: (in order)
```

sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

```
```

sudo add-apt-repository ppa:ubuntu-audio-dev
sudo apt-get update
sudo apt-get dist-upgrade

```
```

sudo gedit /etc/default/speech-dispatcher

```
^blank document

---

### Post by tcll5850 on 2014-12-24
bump
my brother's really complaining about not having audio... it's the whole reason we went from XP64 to Ubuntu...
we had audio on zorin (Ubuntu 12), but after the upgrade to ubuntu 14 we lost it...

earlier I was thinking we had audio after the upgrade, but I guess I was wrong there... heh

alsamixer only has 2 bars labeled PCM and Beep for the primary audio device
the secondary is just 4 spdif bars.


help please

---

