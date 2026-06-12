---
title: "internal microphone on Toshiba satellite not being picked up"
date: 2011-09-27
forum: Hardware
---

### Post by treeboy on 2011-09-27
Hello

I'm using unbuntu 11.04, with kde. using ALSA for sound

the problem is that my internal microphone on the laptop isn't working. however, I can hear the microphone real time in my headphones. I have everything in alsamixer unmuted, but I can't figure out why it's not receiving the microphone as the main input. 

checked sound recorder, and people can't hear me in mangler/vent on wine.

help much appreciated :D

---

### Post by geo909 on 2011-09-27
> **treeboy said:**
> Hello

I'm using unbuntu 11.04, with kde. using ALSA for sound

the problem is that my internal microphone on the laptop isn't working. however, I can hear the microphone real time in my headphones. I have everything in alsamixer unmuted, but I can't figure out why it's not receiving the microphone as the main input. 

checked sound recorder, and people can't hear me in mangler/vent on wine.

help much appreciated :D

Hmm.. Maybe a wine application is not the best one for a sound check! :)

Anyway, just in case, can you open a terminal, start alsamixer,
then press tab (to go to the "capture" settings), then go to "Mic" and then try the up and down arrows? You should probably get something like "internal mic".. Try to experiment with this,
you may get the appropriate input in the end..

---

### Post by lidex on 2011-09-28
If you can hear mic input then the capture settings are probably at issue. Post your amixer output:
```
amixer
```

---

### Post by treeboy on 2011-12-07
sorry for the awfully late response

```

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 38 [59%] [-26.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [7.50dB] [on]
  Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]                                                                                                                                                                  
Simple mixer control 'IEC958',0                                                                                                                                                                 
  Capabilities: pswitch pswitch-joined penum                                                                                                                                                    
  Playback channels: Mono                                                                                                                                                                       
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 24 [77%] [19.50dB] [off]
  Front Right: Capture 24 [77%] [19.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 24 [77%] [19.50dB] [off]
  Front Right: Capture 24 [77%] [19.50dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 10 [8%] [-25.00dB]
  Front Right: Capture 10 [8%] [-25.00dB]
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-1.50dB] [on]
  Front Right: Playback 22 [71%] [-1.50dB] [on]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]

```

---

### Post by lidex on 2012-01-02
Try unmuting your capture element:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 24 [77%] [19.50dB] [off]
  Front Right: Capture 24 [77%] [19.50dB] [off]
```

---

