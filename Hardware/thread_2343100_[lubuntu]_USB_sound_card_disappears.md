---
title: "[lubuntu] USB sound card disappears"
date: 2016-11-13
forum: Hardware
---

### Post by lennartp on 2016-11-13
I just installed lubuntu on an old HP T5730w Thin Client. Works like a charm except I can't get my USB sound card working (Cambridge Audio azur 651a). When I try to select it using PulseAudio Volume Control I can see the card listed, when I select it it just disappears. 

Before starting Volume Control aplay -l gives this:
```
lennart@spotify:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And after the card disappears it gives this:
```
lennart@spotify:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Am not really experienced with desktop (l)ubuntu; where do I start?

---

### Post by Yellow Pasque on 2016-11-13
I think I'd look at dmesg right after the card disappears:
```
dmesg | tail -n 20
```

---

