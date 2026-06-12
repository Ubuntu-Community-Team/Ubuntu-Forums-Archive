---
title: "Getting built in mic working in Ubuntu 8.1"
date: 2008-12-10
forum: Hardware
---

### Post by vonweizer on 2008-12-10
Hi I'm trying to get the built in mic working in my Lenovo s9 netbook. I read in different forums people saying everything worked out of the box but I'm guessing they didn't try the built in mic or I'm missing something.

I have tried to unmute the mic by clicking on the mixer, I've tried 'sudo alsamixer' and unmute. 

When I tap the microphone the sound comes out in the built in speaker. 

Here is the output of amixer:

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [off]
  Front Right: Capture 65536 [100%] [off]

Any ideas?

---

