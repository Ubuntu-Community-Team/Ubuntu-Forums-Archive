---
title: "Added new soundcard, sound broken."
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by Kremlin on 2005-08-28
Hi all,

I had an onboard VIA AC97 sound chipset that was working fine, but I got sick of the xruns in jack and wanted hardware mixing, wavetable, etc, so I've installed my old VideoLogic SonicXplosion card. This is supported as it has the Cirrus Logic CS4614/22/24 chipset, so I know this can work.

I disabled the onboard sound in the bios, and it's definitely not detected by alsa. Here's the beef though - The card is detected, and the module can be modprobe'd (modprobe snd-cs46xx). Alsamixer opens up fine, shows the correct card name, and the relevant channels are unmuted (master, pcm, etc). As far as my limited experience with ALSA goes, it should all be working. And yet, I have no sound.

I've even recompiled alsa using the instructions found [here](http://ubuntuforums.org/showthread.php?t=19307&page=1&pp=10), substituting with the correct chipset, and still no luck.

Basically, I'm stuck, and I turn to you for help. Please help! :)

Here's some relevant outputs from various commands.

```
*lspci | grep audio said:*

0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

``` 

```
*lsmod | grep snd said:*

snd_seq_midi            9952  0
snd_seq_oss            37824  0
snd_seq_midi_event      7744  2 snd_seq_midi,snd_seq_oss
snd_seq                61008  5 snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_cs46xx            100488  1
snd_rawmidi            26528  2 snd_seq_midi,snd_cs46xx
snd_seq_device          9100  4 snd_seq_midi,snd_seq_oss,snd_seq,snd_rawmidi
snd_ac97_codec         78840  1 snd_cs46xx
snd_pcm_oss            62432  0
snd_mixer_oss          21504  1 snd_pcm_oss
snd_pcm               106120  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27396  2 snd_seq,snd_pcm
snd                    68420  14 snd_seq_midi,snd_seq_oss,snd_seq_midi_event,snd_seq,snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10080  1 snd
snd_page_alloc         10500  2 snd_cs46xx,snd_pcm
gameport                4544  1 snd_cs46xx

``` 

```
*amixer said:*

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Front Left: Playback 44 [70%] [on]
  Front Right: Playback 44 [70%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Master',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [on]
  Front Right: Playback 23 [74%] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Center',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control - Switch',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on]
  Front Right: Playback 22 [71%] [on]
Simple mixer control 'PCM Out Path & Mute',1
  Capabilities:
  Mono:
Simple mixer control 'PCM',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [on]
  Front Right: Playback 28 [90%] [on]
Simple mixer control 'Surround',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Center',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 63 [100%] [off]
Simple mixer control 'LFE',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on] Capture [off]
  Front Right: Playback 22 [71%] [on] Capture [off]
Simple mixer control 'CD',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Boost (+20dB)',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Mic',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Video',1
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',1
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Aux',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities:
  Mono:
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix',1
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',1
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 32767 [100%] Capture [off]
  Front Right: 32767 [100%] Capture [off]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 29490 [90%] Capture [off]
  Front Right: 29490 [90%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by Kremlin on 2005-08-28
Interestingly enough, "cat /dev/urandom >> /dev/dsp" does produce static on the speakers, but I can't play any music or sounds (such as with mpg123 or aplay).

I also double checked with the Live CD - it definitely detects it with that and everything works fine.

---

### Post by Kremlin on 2005-08-30
Bump...

---

### Post by Septor on 2005-08-30
Strange that cat'ting stuff to /dev/dsp works... do you have an old asoundrc that is conflicting or something (check both /etc/asoundrc and ~/.asoundrc).  Have you tried programs with the oss emulation (which is what /dev/dsp uses I believe, not sure about this anymore though).

---

### Post by Kremlin on 2005-08-30
[QUOTE=Septor]Strange that cat'ting stuff to /dev/dsp works... do you have an old asoundrc that is conflicting or something (check both /etc/asoundrc and ~/.asoundrc).  Have you tried programs with the oss emulation (which is what /dev/dsp uses I believe, not sure about this anymore though).[/QUOTE]
 Well, I did follow the tutorial to get ESD and Alsa playing together nicely, so I do have an asoundrc. I will move this and see if that fixes the problem. Would that be a likely cause of a problem?

I don't believe I have any programs that use OSS, but I will look and see (perhaps UT does, I'll check it out). Thanks for the reply!

---

### Post by Kremlin on 2005-08-30
Thanks Septor, removing the old /etc/asound.conf fixed the problem. With hardware mixing, I no longer needed it.

---

### Post by Kremlin on 2005-08-30
Well, sorry to triple post, but although sound is working, it's terribly crackly. Not sure exactly how to describe it except that it in music distorts on louder notes, and vocals are terrible. At first I thought it was just ESD (since i had that problem before after switching to ALSA, and fixed it by setting ESD's device to "duplex"), but after listening to an app with gstreamer output using the ALSA sink, it's definitely ALSA.

Any ideas?

---

### Post by Kremlin on 2005-08-30
Bump.... I'm thinking that, since sound is working, this issue of sound quality must be a fairly common one (perhaps it's at the wrong bitrate or something?) Should I look in the hardware forum, or check out somewhere else?

---

### Post by Kremlin on 2005-09-04
Bump... I would like to fix this problem without having to reinstall ubuntu. WIth the sound sounding like it does, it's basically unuseable. :(

---

### Post by Kremlin on 2005-09-13
[QUOTE=Kremlin]Bump... I would like to fix this problem without having to reinstall ubuntu. WIth the sound sounding like it does, it's basically unuseable. :([/QUOTE]
 Okay, I've fixed this problem, which is good.
Reading the ALSA documentation for the cs46xx chipset, one of the last posts mentions distorted sound. Basically, because I had the DAC maxed out, PCM maxed out and master fairly high, it was distorting. Turning the DAC all the way down, PCM down a bit, and only touching the master volume has fixed the problem, and all sounds sweet.

I hope this helps anyone in a similar situation.

---

### Post by DrinkYourOvaltine on 2005-09-14
You guys are my heros.

---

