---
title: "Help with my hp dv9000 quickplay buttons!"
date: 2008-05-06
forum: Hardware
---

### Post by cespinal on 2008-05-06
One thing that a really liked about hardy was the fact that the quickplay buttons of my pc worked out of the box: I was able to mute the sound and change the volume with those small touch sensitive buttos just right above the keyboard. 

Now, I was trying to fix my soundless microphone and I ended up with this: Microphone still does not work, and now the mute and volume quickplay buttons are not working!. I could see that opening alsamixer now these buttons are trying to control the internal mic volume!!!

my pc is and hp dv9000 
AMD 64 Turion dual core
3gb RAM 
HDA Nvidia sound card


this is my out put from amixer: 

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
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
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 78 [98%] [4.00dB] Playback [on]
  Front Right: 78 [98%] [4.00dB] Playback [on]
Simple mixer control 'External Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]

I definitely need to put things back up and make a clean start over to solve my mic problem without affecting those buttons. any help would be REALLY appreciated!!

---

### Post by cespinal on 2008-05-06
solved my problem with the quickplay buttons...now im back to my useless microphone thing...

---

### Post by agnes on 2009-05-05
Could you tell me, how did you solve the issue with the quickplay buttons?
I have a quickplay button that does not work (gives me the same keycode as the "v" letter).

---

