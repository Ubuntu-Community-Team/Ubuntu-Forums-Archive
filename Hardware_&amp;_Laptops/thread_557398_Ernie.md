---
title: "Ernie"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by Xernie on 2007-09-22
<< Please fix thread title (I screwed it up!) >>

Hi. I had been using Feisty since it was Beta, and I never had any problems with it. However, I just installed Xubuntu Gutsy (Tribe 5) and I am having some sound card problems.

As you may have guessed, I have the infamous HDA Intel card (which sucks, by the way). My problem, though, is not one of the usual ones.  I have been searching for many hours now and haven't found any problem similar to mine.  My problem is that there is no volume control for playback. In alsamixer, it shows a 'Master' control but it's stuck at 0.

The weirdest thing is that I DO have sound. I can't adjust the volume but I can definitely hear it.  Also, the controls for the capture channels are all there and I can adjust them.  Any ideas?  Here some outputs of stuff that I guess people will ask for:

amixer:
Simple mixer control 'Master',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 11 [85%] [27.00dB] [off]
  Front Right: Capture 11 [85%] [27.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 11 [85%] [27.00dB] [off]
  Front Right: Capture 11 [85%] [27.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 0 [0%] [-6.00dB] [on]
  Front Right: Capture 0 [0%] [-6.00dB] [on]

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks in advance for your help.

Edit: For some reason I forgot to add the title to the thread.  Sorry =(.

---

### Post by ddrichardson on 2007-09-23
UAResolved

---

