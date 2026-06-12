---
title: "Update borked my sound, too (AC 97 sound card)..."
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by Q4U on 2005-06-11
Updated Hoary, lost my sound: no event beeps, no music (neither from CD nor from MP3 in the HDD), nothing. 

No errors either, just no sound. Used to work perfectly with Warty and (initially) with Hoary too.

Tried to check that the channels are not muted, everything seems all right (see amixer output below).

Also tried the tweaking in [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)... no joy 

Some modules conflicting perhaps?!... Help, I'm going crazy on this issue! ](*,) 

Thanks. Q4U
_______

$ lspci

0000:00:00.0 Host bridge: Intel Corp. 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller ** #HERE IS MY SOUND CARD A PLAIN VANILLA AC 97**
0000:00:02.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:00:04.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)0000:00:06.0 PCI bridge: Toshiba America Info Systems: Unknown device 061b (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corp. 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corp. 82440MX Power Management Controller
0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:01:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
_______

$ cat /proc/asound/cards

0 [I440MX         ]: ICH - Intel 440MX
                              Intel 440MX with YMF743 at 0xfd00, irq 11

$ cat /proc/asound/modules

0 snd_intel8x0
_______

$ lsmod | grep oss

snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe

$ lsmod | grep snd

snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

_________

$ amixer

**Simple mixer control 'Master',0**
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31** [100%] [on]**
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [on]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
**Simple mixer control 'PCM',0**
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31** [100%] [on]**
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities:
  Mono:
Simple mixer control 'Line',0
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
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [on]
Simple mixer control 'Aux',0
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
  Front Left: Capture 14 [93%] [on]
  Front Right: Capture 14 [93%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

---

### Post by solkar_saruman on 2005-06-12
[QUOTE=Q4U]Updated Hoary, lost my sound: no event beeps, no music (neither from CD nor from MP3 in the HDD), nothing. 

No errors either, just no sound. Used to work perfectly with Warty and (initially) with Hoary too.

Tried to check that the channels are not muted, everything seems all right (see amixer output below).

Also tried the tweaking in [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)... no joy 

Some modules conflicting perhaps?!... Help, I'm going crazy on this issue! ](*,) 

Thanks. Q4U
_______

$ lspci

0000:00:00.0 Host bridge: Intel Corp. 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller ** #HERE IS MY SOUND CARD A PLAIN VANILLA AC 97**
0000:00:02.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:00:04.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)0000:00:06.0 PCI bridge: Toshiba America Info Systems: Unknown device 061b (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corp. 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corp. 82440MX Power Management Controller
0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:01:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
_______

$ cat /proc/asound/cards

0 [I440MX         ]: ICH - Intel 440MX
                              Intel 440MX with YMF743 at 0xfd00, irq 11

$ cat /proc/asound/modules

0 snd_intel8x0
_______

$ lsmod | grep oss

snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe

$ lsmod | grep snd

snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

_________

$ amixer

**Simple mixer control 'Master',0**
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31** [100%] [on]**
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [on]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
**Simple mixer control 'PCM',0**
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31** [100%] [on]**
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities:
  Mono:
Simple mixer control 'Line',0
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
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [on]
Simple mixer control 'Aux',0
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
  Front Left: Capture 14 [93%] [on]
  Front Right: Capture 14 [93%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on][/QUOTE]
 Same problem here, but in another thread.

---

### Post by scoon on 2005-06-12
Hey there, 

Have you tried muting and unmuting and changing volumes with alsamixer ? 

regards, 

scoon

---

### Post by solkar_saruman on 2005-06-12
[QUOTE=scoon]Hey there, 

Have you tried muting and unmuting and changing volumes with alsamixer ? 

regards, 

scoon[/QUOTE]
 That's not working for me.

---

### Post by bmwboy on 2005-06-12
[QUOTE=solkar_saruman]That's not working for me.[/QUOTE]
 I cant even run alsamixer with this soundcard!

---

### Post by Q4U on 2005-06-12
Scoon: I tried indeed...

My understanding is that the "Master and "PCM" channels are the important ones. I made sure that they are unmuted and that the volume is 100%. No reaction.

I also messed around with a few random channels, such as "External Amplifier": some people on this forum recommend muting it... I tried both mute and unmute with no luck.

I have seen several posts complain about Hoary and AC 97. I am starting to believe that it is a bug. Should we report it?

Another question: with no sound whatsoever, will my (win)modem work? I have no way to verify it now, but I shall leave soon for my holiday home, which is on dialup only. I would dread to be offline for two weeks...

Q4U

PS:  If you go to Slashdot now you'll see an article about a leading FOSS developer ditching Linux in favour of OS X precisely because of sound problems... guess it's a bit of a sore spot for our favourite penguin.

---

### Post by scoon on 2005-06-14
[QUOTE=Q4U]Scoon: I tried indeed...

My understanding is that the "Master and "PCM" channels are the important ones. I made sure that they are unmuted and that the volume is 100%. No reaction.

I also messed around with a few random channels, such as "External Amplifier": some people on this forum recommend muting it... I tried both mute and unmute with no luck.

I have seen several posts complain about Hoary and AC 97. I am starting to believe that it is a bug. Should we report it?

Another question: with no sound whatsoever, will my (win)modem work? I have no way to verify it now, but I shall leave soon for my holiday home, which is on dialup only. I would dread to be offline for two weeks...

Q4U

PS:  If you go to Slashdot now you'll see an article about a leading FOSS developer ditching Linux in favour of OS X precisely because of sound problems... guess it's a bit of a sore spot for our favourite penguin.[/QUOTE]


Hey there, 

They are the obvious ones.  For example, I have an audigy zs2 and from time to time new kernels will mute "Audigy Analog/Digital Output Jack".  This results in no sound whatsoever.  The first time it happened it took me a few hours to figure that simple one out.  So what I meant for you to understand is to fiddle with ALL of the controls, even the one that doesn't seem to make any difference. 

regards, 

scoon

---

