---
title: "[SOLVED] sound problems, with headphones i hear only from left"
date: 2008-10-17
forum: General Help
---

### Post by crazyfuturamanoob on 2008-10-17
When I use headphones, I can hear only from left side. Before, sounds worked ok.

There is no problem with my headphones. Wires are all ok. I know this because
when I test theses headphones with another computer they work, or if I test them on this computer, but with windows.

Problem is in the sound drivers. But how to fix it?

Edit:

Result of amixer. See the 8th line, Front Right: ... [off]? How to switch it on?
```

arho@ohra-laptop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 40 [62%] [-24.00dB] [on]
  Front Right: Playback 40 [62%] [-24.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Line In Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%]
  Front Right: 0 [0%]
arho@ohra-laptop:~$ 

```

---

### Post by ajmorris on 2008-10-17
hi there,
have you tried running a mixer (such as alsamixer from a terminal) and checking that both left and right volumes are turned up?
also, if you use alsamixer, check for a 'M' (for mute) under both of the volumes

AJ

---

### Post by crazyfuturamanoob on 2008-10-17
Right channel is was muted, as you can see from my first post.
I managed to fix it by downloading alsamixergui with synaptic and
switching right channel on with it. :)

---

