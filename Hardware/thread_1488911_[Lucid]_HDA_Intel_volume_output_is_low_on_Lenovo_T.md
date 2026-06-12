---
title: "[Lucid] HDA Intel volume output is low on Lenovo Thinkpad"
date: 2010-05-20
forum: Hardware
---

### Post by NightW01F on 2010-05-20
Hi, I've problem with my volume output. it's really low in ubuntu (both in karmic and lucid) compared to windows. my laptop is Lenovo Thinkpad T61 and the sound card is HDA Intel.
I extracted this using lshw:
```

*-multimedia
     description: Audio device
     product: 82801H (ICH8 Family) HD Audio Controller
     vendor: Intel Corporation
     physical id: 1b
     bus info: pci@0000:00:1b.0
     version: 03
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=HDA Intel latency=0
     resources: irq:17 memory:fe020000-fe023fff

``` I've read some manuals in internet, but didn't understand well enough.
please note that I'm newbie.

---

### Post by wieman01 on 2010-05-20
Please open a terminal window (i.e. command line) and issue:
> alsamixer
You should be able to adjust the master volume there. Use tab to jump from output device to output device.

---

### Post by NightW01F on 2010-05-20
I've tried it before. it's in max level (both master and pcm)

---

### Post by NightW01F on 2010-05-24
any answers?

---

### Post by dino99 on 2010-05-24
install paprefs and gnome-alsamixer and set your prefs

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

