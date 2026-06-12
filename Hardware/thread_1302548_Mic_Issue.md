---
title: "Mic Issue"
date: 2009-10-27
forum: Hardware
---

### Post by macd3v on 2009-10-27
Hey guys/gals

Im coming to you today with something that i think is most likely a common issue. I have googled the hell out of this and have seen a few threads around this forum with similar issues and I have tried some of the "fixes" for it but im still having no luck. I am still relativly new to ubuntu / any linux os for that matter.

Im not completely stupid with these things and consider myself a pretty quick learner im in college right now doing intro to os right now were just doing windows but we will be moving onto linux after this semester and i wanted to get a jump start on it. i've managed to get my wireless card, webcam, and a few other things up and running but this is the one thing thats been giving me an issue( other than getting my wireless card into monitor mode) but i'll ask about that on a later date.

The problem im having is with my built in mic it doesnt seem to want to work properly or I can't get it to anyway.

Running:
Acer extensa 4420 Laptop
XP / Ubuntu

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Acer Incorporated [ALI] Device 0123
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
```
http://www.alsa-project.org/db/?f=97c48573568e8b43f0cdb61cce4bc42beebf518c
```


Any help would be greatly appreciated I hope I have provided enough info for you guys if you need anything else lemme know and i'll be prompt to get you the info as i really want this fixed hah.

---

### Post by macd3v on 2009-10-27
bump

anyone any ideas please???

---

