---
title: "Docking station sound input not working"
date: 2012-09-12
forum: Hardware
---

### Post by jikard0 on 2012-09-12
Hello,

I have a HP 8560W workstation. I installed Ubuntu 12.10. After that i purchase a Docking Station HP 230W with monitor. Everything works fine except Docking Sound-In where i plugged in Microphone.

I have a headset and i plugged into Docking Station Sound In&Out.
Headphones are working well but Microphone do not work. When i move headset connectors to laptop Sound In&Out everything works perfect but on Dock station sound-in is not works as well.

What i found is when i put laptop into the docking Station there is no Dock option in pavucontrol and alsamixer.

Is this a driver issue and how can I fix it.

Thank you in advance for help.


Best Regards
jikard0

---

### Post by jikard0 on 2012-09-12
I miss to mentioned that i do not have section "Dock"
# amixer scontents
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 63 [98%] [0.75dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 3 [20%] [4.50dB] [on]
  Front Right: Capture 3 [20%] [4.50dB] [on]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

---

### Post by jikard0 on 2012-09-12
Also amixer -c 0 sset Dock,0 unmute returns me a error:


#amixer -c 0 sset Dock,0 unmute
amixer: Unable to find simple control 'Dock',0

---

