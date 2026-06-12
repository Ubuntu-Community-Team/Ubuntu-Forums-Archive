---
title: "Internal microphone not working - asus UX370UAF - 18.04.04 LTS"
date: 2020-03-27
forum: Hardware
---

### Post by s-terenzi on 2020-03-27
Hello everyone,

Laptop is asus zenflip UX370UAF with ubuntu 18.04.04 LTS in dualboot with win 10, where mic is working normally.
It is a problem I can't fix already for some time and it would be great if anyone has any lead. 
I tried different solutions on related posts in other forums, but no luck.
Any idea?

Here some info:

amixer output:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',4
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 63 [100%] [30.00dB] [on]
  Front Right: Capture 63 [100%] [30.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 78 [65%] [9.00dB]
  Front Right: Capture 78 [65%] [9.00dB]
Simple mixer control 'Headset Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%] [20.00dB]
  Front Right: 2 [67%] [20.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%] [20.00dB]
  Front Right: 2 [67%] [20.00dB]

```

arecord -l output:

```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Attached is pavucontrol screenshot

Thanks!

---

### Post by n4113032 on 2020-04-28
It's a bit of a nightmare to fix on the UX370UAF.  I had the same problem with 18.10 LTS.  I just updated to Ubuntu 20.04 LTS Focal Fossa and it did not work in that OS either.  

The "answer" is the Asus Zenbook Flip S UX370UAF has ONE and only ONE built in microphone.  So the recordings are MONO.  After lots of searching, I discovered one has to split the audio for the microphone L and R using the usual GUI pavucontrol.  Then lower any one of L or R channels to ZERO.  It works fine now.  I'd still call this a bug.  I don't need to do this when I boot into Windozzz.

---

### Post by s-terenzi on 2020-04-28
> **n4113032 said:**
> It's a bit of a nightmare to fix on the UX370UAF.  I had the same problem with 18.10 LTS.  I just updated to Ubuntu 20.04 LTS Focal Fossa and it did not work in that OS either.  

The "answer" is the Asus Zenbook Flip S UX370UAF has ONE and only ONE built in microphone.  So the recordings are MONO.  After lots of searching, I discovered one has to split the audio for the microphone L and R using the usual GUI pavucontrol.  Then lower any one of L or R channels to ZERO.  It works fine now.  I'd still call this a bug.  I don't need to do this when I boot into Windozzz.

Yes I noticed it is a nightmare. Though I am pretty sure I had fix it at the beginning (last year same month more or less) and it is been working until one point, and now it is not anymore by a few months.
I researched a lot too and i think i have came across the same thing about the mic in mono and lowering to zero L or R, but at the very moment I can't find how to make it work even if i have done it.
I am not sure if there is a config file where to se that? because if i put it from pavucontrol or alsamixer, when i close it and open again something changes i think and anyway i didn't work after a quick try. i will try more but if you have any hints please share as it is pretty difficult to solve a problem for a not so common laptop. 
I attached a screenshot of alsamixer and pavucontrol.
Thanks a lot for your answer!

---

