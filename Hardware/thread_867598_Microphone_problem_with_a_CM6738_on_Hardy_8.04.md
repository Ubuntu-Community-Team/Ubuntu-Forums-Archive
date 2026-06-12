---
title: "Microphone problem with a CM6738 on Hardy 8.04"
date: 2008-07-23
forum: Hardware
---

### Post by Legendário on 2008-07-23
I have changed the sound card on my computer, which is working well but I just can't make my microphone work. I've read many topics but couldn't find the answer on any of them.

I can hear my voice on the sound boxes once the mic is connected but they don't work when I open the gnome sound recorder. When i do that, i receive this message (translated): **Your audio capture configurations are not valid. Please, fix them on your multimedia configurations.**

At least in Portuguese, those words don't make my life easier.

arecord shows the following:
```
$ arecord
ALSA lib pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:546: erro ao abrir áudio: Argumento inválido
```

Those are some terminal outputs to help:
```
$ lsmod | grep snd_pcm_dmix
kemel@P4-Kemel:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
kemel@P4-Kemel:~$ arecord
ALSA lib pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:546: erro ao abrir áudio: Argumento inválido
kemel@P4-Kemel:~$ lspci | grep audio
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
kemel@P4-Kemel:~$ lsmod | grep snd
snd_cmipci             36992  5 
gameport               14472  1 snd_cmipci
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                75400  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10504  1 snd_pcm
snd_opl3_lib           12160  1 snd_cmipci
snd_hwdep               9476  1 snd_opl3_lib
snd_mpu401_uart         8832  1 snd_cmipci
snd_seq_dummy           3972  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
snd_rawmidi            24608  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51152  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          8588  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54692  23 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
kemel@P4-Kemel:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%] [0.00dB] [off] Capture [off]
  Front Right: Playback 255 [100%] [0.00dB] [off] Capture [off]
Simple mixer control 'Synth',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [on]
  Front Right: Playback 25 [81%] [on] Capture [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [on]
  Front Right: Playback 25 [81%] [on] Capture [on]
Simple mixer control 'Line-In Mode',0
  Capabilities: enum
  Items: 'Line-In' 'Rear Output' 'Bass Output'
  Item0: 'Line-In'
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 31 Capture 0 - 7
  Mono: Playback 31 [100%] [on] Capture 7 [100%] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Mic-In Mode',0
  Capabilities: enum
  Items: 'Mic-In' 'Center/LFE Output'
  Item0: 'Mic-In'
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [off]
Simple mixer control 'IEC958 5V',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Copyright',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Phase Inverse',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Select',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Valid',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Loop',0
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
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Front Left: Playback 12 [80%] [on] Capture [on]
  Front Right: Playback 12 [80%] [on] Capture [on]
Simple mixer control 'Four Channel Mode',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```

Thanks

---

