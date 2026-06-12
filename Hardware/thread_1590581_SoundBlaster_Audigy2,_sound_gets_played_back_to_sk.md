---
title: "SoundBlaster Audigy2, sound gets played back to skype communication"
date: 2010-10-08
forum: Hardware
---

### Post by LonelyStar on 2010-10-08
Hi,

I have this audio card:

05:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

Works fine, but when I talk to someone in skype, he can here my sound. Is especially annoying when playing games while skyping. I tried around with everything in alsamixer, but I could not fix it.
Any Ideas what I could be missing?

Here my mixer setting:

```

amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 100 [100%] [0.00dB]
  Front Left: Capture 31 [100%] [0.00dB] [on]
  Front Right: Capture 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'PCM',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 95 [95%] [-2.00dB]
  Front Right: Capture 95 [95%] [-2.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 25 [81%] [3.00dB] [off]
  Front Right: Capture 25 [81%] [3.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

Thanks!
Nathan

---

### Post by IcarusR on 2010-10-08
Could be just microphone picking up any sound in that room, including game sound.

Answer turn game volume down, don't Skype & play games at same time ??

---

### Post by LonelyStar on 2010-10-09
Hey,

I am using a headset, so it can not be the sound in the room.
I am using skype during games because I am talking to the people I am playing with :).

I remember having this problem during my gentoo time. I solved it by setting something in alsamixer, but I can not figure out what :(.

Regards,
Nathan

---

