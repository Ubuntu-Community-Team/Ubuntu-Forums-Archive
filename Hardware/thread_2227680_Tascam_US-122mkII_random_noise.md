---
title: "Tascam US-122mkII random noise"
date: 2014-06-03
forum: Hardware
---

### Post by piratemathew on 2014-06-03
Hello,

I just got my hands on a Tascam US-122mkII which worked out of the box. The only thing I'm running into is the device generating random static noise in the high frequency range. It doesn't happen all the time, just randomly every x seconds. Googling the problem didn't really help, and after struggling for a few hours, I guess I should just ask here and hope someone can help me out.

Some information:

```
$ sudo cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 23
 1 [MKII           ]: USB-Audio - US122 MKII
                      TASCAM US122 MKII at usb-0000:00:02.1-1, high speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfddfc000 irq 41

```

```
$ sudo cat /proc/asound/card1/stream0 
TASCAM US122 MKII at usb-0000:00:02.1-1, high speed : USB Audio

Playback:
  Status: Running
    Interface = 1
    Altset = 1
    Packet Size = 47
    Momentary freq = 44100 Hz (0x5.8333)
  Interface 1
    Altset 1
    Format: S24_3LE
    Channels: 2
    Endpoint: 2 OUT (NONE)
    Rates: 44100, 48000, 88200, 96000
    Data packet interval: 125 us


```

```
mathijs@milenniumfalcon:~$ sudo cat /proc/asound/card1/pcm0p/sub0/sw_params 
tstamp_mode: ENABLE
period_step: 1
avail_min: 87760
start_threshold: 18446744073709551615
stop_threshold: 6206523236469964800
silence_threshold: 0
silence_size: 0
boundary: 6206523236469964800



```

```
$ sudo cat /proc/asound/card1/pcm0p/sub0/hw_params 
access: MMAP_INTERLEAVED
format: S24_3LE
subformat: STD
channels: 2
rate: 44100 (44100/1)
period_size: 44100
buffer_size: 88200

```

More info can be provided on request.

Ubuntu version is 13.10, kernel version is 3.11.0-15

---

### Post by luch3 on 2015-05-05
Hi piratemathew... I have the same trouble, have you found a solution? thanks!

L.

---

