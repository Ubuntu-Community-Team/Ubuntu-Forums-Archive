---
title: "install Soundcard under &quot;Ubuntu Server&quot;??"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Led_Zeppelin on 2009-01-15
Hi

I have ubuntu Server 8.10. I want to install my Audigy2 soundcard.
I tried this things:

```
server:alsamixer: function snd_ctl_open failed for default: No such device
server:~$asoundconf list
server:~$Names of available sound cards:
server:~$Audigy2
server:~$lspci | grep -i audio
server:~$02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
server:~$modprobe -l | grep snd | grep audigy
server:~$modprobe -l | grep snd | grep creative
server:~$

```
I can't find a driver for this soundcard. But with Ubuntu 8.10 gnome I can use my soundcard.....


and if i want to play some mp3 (I've installed gstreamer-codes and alsa-utils/base)

```
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Audigy2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:583: audio open error: No such device
```

thank you for help!!:lolflag:

---

### Post by HuckBerry on 2010-02-12
*bump*

I'm having the same issue, 9.10 server as well.

lshw output:
```
*-multimedia:1
             description: Multimedia audio controller
             product: Vortex 2
             vendor: Aureal Semiconductor
             physical id: f
             bus info: pci@0000:00:0f.0
             version: fe
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=au8830 latency=64 maxlatency=12 mingnt=4
             resources: irq:3 memory:f4000000-f403ffff ioport:1838(size=8) ioport:1830(size=8)

```lspci output:
```
00:0f.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
```aplay -l output:
```
aplay: device_list:223: no soundcards found...
```

---

