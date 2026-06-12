---
title: "Sound stoped working after update."
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by dlkb1240 on 2008-02-26
Hi all, I recently updated my installation of 7.10 for the x64. My sound was working fine before the update. Restarted and Ubuntu didn't even see my card. Re-installed ALSA and now it sees my card but nothing comes out of my speakers or headphone jack. I have a HP tx1120us with a Checked alsamixer and nothing is muted that shouldn't be. 
Here's the cat /proc/asound/cards:
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 9

```

Here's the amixer output:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 250 [98%] [-1.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 28 [90%] [28.50dB] [on]
  Front Right: Capture 28 [90%] [28.50dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic'
  Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 41 [64%] [-23.00dB] [on]
  Front Right: Playback 41 [64%] [-23.00dB] [on]

```
Any other info needed let me know. Thanks for your time.

---

### Post by erginemr on 2008-02-27
Please see this thread:
[http://ubuntuforums.org/showthread.php?t=708952](http://ubuntuforums.org/showthread.php?t=708952)

esp. the external link given therein, which looks very promising.

---

### Post by dlkb1240 on 2008-02-27
Wow how unbelievably retarded. Anyone else having this problem go here and follow directions:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/family-rev-3-sound-card-to-work-in-gutsy/")

Thanks erginemr you're the man...or woman.

---

### Post by erginemr on 2008-02-27
:) Man actually. Let me rephrase the link:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

Alternatively, those having problems should install:
```
sudo aptitude install linux-backports-modules
```
to patch / update their ALSA drivers to the latest version.

Take care yourself. :popcorn:

---

