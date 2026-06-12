---
title: "sound &amp;  test is negative"
date: 2009-12-28
forum: Hardware
---

### Post by m3asmi on 2009-12-28
[SIZE=4]I recently bought a netbook, a Compaq Mini 110c, and immediately, hop hop hop:
uninstalled Windows. To Ubuntu 9.04

I made 2-3 rapid test for me quickly realize that, oh misery, **[FONT=Comic Sans MS]no sound[/FONT]**. With the headsets, yes, but not with HP.

I tried 2-3 manip ', including reinstalling alsa-drivers, and monitoring combined 2-3 on the web which I have not greatly advanced.

rachid@EL-GHAZI:~$ cat /proc/asound/card0/codec#* | grep Codec 
```
Codec: IDT 92HD81B1X5
```

rachid@EL-GHAZI:~$ amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Line In',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Mono Mux',0
  Capabilities: enum
  Items: 'DAC0' 'DAC1' 'Mixer'
  Item0: 'DAC0'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Amp',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'DAC0',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'DAC1',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Analog Inputs'
Simple mixer control 'Digital Input Source',1
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1' 'Digital Mic 2'
  Item0: 'Analog Inputs'
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]

```
[/SIZE]

---

### Post by m3asmi on 2009-12-29
Hi 
can you help me please

---

### Post by m3asmi on 2009-12-30
I don't know why person reply me?!!!

---

### Post by daka on 2010-04-09
same problem for me... finally did a google search and windows people also have problem with sound...i suspect it might have something to do with the one jack for headphones and mic.... compaq problem... still trying to investigate this... let me know if you have it fixed please

sean

---

### Post by daka on 2010-04-09
suggested solution is to install bcmwl-kernel-source with apt-get install or synaptic .... I did this and am now testing it out

sean

---

### Post by daka on 2010-04-09
Still no luck with Mic .... Anyone else have success with this problem?

sean

---

### Post by lidex on 2010-04-09
Check your levels in alsamixer:
```
alsamixer
```

---

