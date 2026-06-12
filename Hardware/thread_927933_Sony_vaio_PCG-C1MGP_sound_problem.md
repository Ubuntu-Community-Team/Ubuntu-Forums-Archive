---
title: "Sony vaio PCG-C1MGP sound problem"
date: 2008-09-23
forum: Hardware
---

### Post by decjedrek on 2008-09-23
Hi,

I have Sony Vaio PCG-C1MGP notebook with xubuntu 8.04 running.
The problem is that i can't listen to music while working in console (trying to play mp3 or ogg with mp3blaster or mplayer). I can hear the sound but it's more like it came from under the water. The issue is gone when i use totem or any other software running in graphical mode.

printout from lshw

```
 *-multimedia:0
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
```

---

