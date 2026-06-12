---
title: "First gen Audigy has no Capture capability"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by NoUse on 2005-09-21
EDIT:
I figured out that Audigys don't use capture toggles but rather go off of the capture volumes.



I can hear sounds from my Audigy card just fine through alsa.  However, I can't toggle capture mode while in alsamixer and the Capture tab doesn't even show up in the gnome mixer.

From what I can tell, the audigy card has Capture mixers (cvolume) but no Capture toggles (cswitch).  I just don't know how to convince ALSA to give Audigy Capture toggles.

```


ALSA Audio Debug v0.0.9 - Wed Sep 21 03:21:45 CDT 2005
http://alsa.opensrc.org/?page=aadebug

Kernel ----------------------------------------------------
Linux kal-el 2.6.10-5-k7 #1 Thu Sep 8 06:54:12 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1            98116  1
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               9476  1 snd_emu10k1
snd                    55268  11 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Sep  8 2005 for kernel 2.6.10-5-k7.
0 [Audigy         ]: Audigy - Sound Blaster Audigy
                     Sound Blaster Audigy (rev.3) at 0xb800, irq 16
  0: [0- 0]: ctl
  4: [0- 0]: hardware dependent
  9: [0- 1]: raw midi
  8: [0- 0]: raw midi
 18: [0- 2]: digital audio playback
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
00-00: EMU10K1 (FX8010)
00-00: emu10k1 : EMU10K1 : playback 32 : capture 1
00-01: emu10k1 mic : EMU10K1 MIC : capture 1
00-02: emu10k1 efx : EMU10K1 EFX : playback 8 : capture 1

Dev Snd ---------------------------------------------------
controlC0  midiC0D0  pcmC0D0c  pcmC0D1c  pcmC0D2p
hwC0D0     midiC0D1  pcmC0D0p  pcmC0D2c  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(TM) XP 2100+
cpu MHz         : 1736.220

RAM -------------------------------------------------------
MemTotal:       256712 kB
SwapTotal:      498004 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)


```

```

amixer output

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 60 [60%]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Limits: 0 - 40
  Mono: 19 [48%]
  Front Left:
  Front Right:
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Limits: 0 - 40
  Mono: 19 [48%]
  Front Left:
  Front Right:
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 48 [48%] Capture 48 [48%]
  Front Right: Playback 48 [48%] Capture 48 [48%]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 98 [98%]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Front Left: Playback 0 [0%]
  Front Right: Playback 0 [0%]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%]
Simple mixer control 'Music',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Line2',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 48 [48%] Capture 6 [6%]
  Front Right: Playback 46 [46%] Capture 4 [4%]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 68 [68%]
  Front Right: Playback 0 [0%] Capture 64 [64%]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 6 [6%]
  Front Right: Playback 0 [0%] Capture 6 [6%]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

