---
title: "Keyboard enermax aurora premium / usb sound card works with hardy but not with gutsy"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by ansicplusplus on 2008-03-01
Hy,
while trying to get the usb sound-card of my enermax aurora premium keyboard to work with gutsy, I discovered, that it's already supported with hardy alpha 5. Same is for Knoppix 5.3, therefore I suspect kernel 2.6.24 is needed. I guess I will wait till hardy is available and stop trying. However the sound was awfully crackling when I tried.

In case anyone got it working with gutsy I wouldn't mind a hint. The sound card gets detected but amixer und aplay fail with weird errors:

```
$ aplay -D plug:hw:1 /usr/share/sounds/info.wav
Wiedergabe Wave '/usr/share/sounds/info.wav' : Signed 16 bit Little Endian, Samplingrate: 44100 Hz, Mono
aplay: set_params:961: Hardwareparameter konnten nicht installiert werden:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 44100
PERIOD_TIME: 125000
PERIOD_SIZE: (5512 5513)
PERIOD_BYTES: (11024 11026)
PERIODS: (3 5)
BUFFER_TIME: 500000
BUFFER_SIZE: 22050
BUFFER_BYTES: 44100
TICK_TIME: 4000
```
```
$ amixer -c1
amixer: Mixer hw:1 load error: Invalid argument
```

dmesg just says:
```
5:1:1: usb_set_interface failed
```

From what I discovered using google usb sound cards on usb hubs are quite tricky. Unfortunately the solution using an onboard usb port is no option in this case ;-)

Patiently waiting, ansicplusplus

---

### Post by ansicplusplus on 2008-05-24
It doesn't work in hardy yet.
Still waiting, ansicplusplus

---

