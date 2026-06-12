---
title: "Distorted sound on HDMI"
date: 2018-08-04
forum: Hardware
---

### Post by bsder on 2018-08-04
Hi, folks,

I'm trying to debug a sound problem on my laptop with HDMI.  When I play via the internal speakers, things are fine.  When I play via my HDMI speakers, the sound is the correct frequency, but sounds like a machine gun/heavily distorted.  It sounds like buffer underruns.

When I use "speaker-test -D hw:CARD=PCH,DEV=0 -t sine -c 2 -r 48000" the sound comes out just as expected on my laptop speakers.  When I use "speaker-test -D hw:CARD=PCH,DEV=3 -t sine -c 2 -r 48000" I get distorted sound on my HDMI speakers.

I tried the "tsched=0" dance already, but it didn't have any impact.

What should be my next steps to try to hunt this down?

Thanks.

Ubuntu 18.04.1 LTS
LG Gram 13"
i7-8550U @ 1.80GHz
16GB RAM
Intel UHD Graphics 620 (Kabylake GT2)

```
andrewl@andrewl-lg-ubuntu:~$ uname -a
Linux andrewl-lg-ubuntu 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
andrewl@andrewl-lg-ubuntu:~$ speaker-test -D hw:CARD=PCH,DEV=0 -t sine -c 2 -r 48000

speaker-test 1.1.3

Playback device is hw:CARD=PCH,DEV=0
Stream parameters are 48000Hz, S16_LE, 2 channels
Sine wave rate is 440.0000Hz
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
^CTime per period = 3.886604
andrewl@andrewl-lg-ubuntu:~$ speaker-test -D hw:CARD=PCH,DEV=3 -t sine -c 2 -r 48000

speaker-test 1.1.3

Playback device is hw:CARD=PCH,DEV=3
Stream parameters are 48000Hz, S16_LE, 2 channels
Sine wave rate is 440.0000Hz
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.627954
 0 - Front Left
^C 1 - Front Right
Time per period = 0.459427
andrewl@andrewl-lg-ubuntu:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, CX8200 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
hdmi:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 3
    HDMI Audio Output
hdmi:CARD=PCH,DEV=4
    HDA Intel PCH, HDMI 4
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dmix:CARD=PCH,DEV=9
    HDA Intel PCH, HDMI 3
    Direct sample mixing device
dmix:CARD=PCH,DEV=10
    HDA Intel PCH, HDMI 4
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=9
    HDA Intel PCH, HDMI 3
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=10
    HDA Intel PCH, HDMI 4
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=9
    HDA Intel PCH, HDMI 3
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=10
    HDA Intel PCH, HDMI 4
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, CX8200 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=9
    HDA Intel PCH, HDMI 3
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=10
    HDA Intel PCH, HDMI 4
    Hardware device with all software conversions

```

---

