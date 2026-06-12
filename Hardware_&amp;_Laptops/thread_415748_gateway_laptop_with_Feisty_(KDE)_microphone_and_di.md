---
title: "gateway laptop with Feisty (KDE): microphone and display"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by scarab on 2007-04-20
I did the official upgrade (via update manager) from kubuntu 6.06 to 6.10, and then to 7.04... (all AMD64)

I have one problem (display) that begun with the update to 6.10 and continues in 7.04, and another that has been only partially resolved in 7.04 that persists since 6.06.
hope someone will can give me some tip on how to solve them, I am not an absolute beginner, but do not have many experience yet...

my notebook is a gateway mx6447

1. I cannot more set up monitor brightness... in dapper, I did it by pressing Fn and up/down arrow.... now it does work only when booting up, but not inside kubuntu. volume setting with Fn and PgUp/PgDn works perfectly. that is important for me because I work in a place with very variable external light. In dapper it worked perfectly, in edgy it simply stopped working... in feisty it does causes some "disturbance" in the display area where in dapper it showed the bright regulation, but bright does not change, and that "disturbed" display area (a square in extreme up left corner) has no readable things, only small coloured squares that appear while I press the briht setting keys...
under K>System Configuration> Display (sorry, it is in Portuguese, maybe names would vary...), hardware is configured as generical plug and play. there are SEVERAL Gateway monitors, I do not know if I could check one, but in that case which one?
in all other aspects display works perfectly.

2. I have sound only for output, not input. sound card is recognized by alsamixer as HDA ATI SB with a SigmaTel ID7634 chip. opening alsamixer, "capture" has two mixers that appears to be activated (neither is mute). Under dapper or Edgy, "capture" was simply empty and the output had only two mixers instead of five actually. I have already compiled alsa-drivers' last version (rc3), and that persists. It is something I really need to fix up, as I need to use Skype.
here some info that maybe of help on this problem:
scarab@scarab-laptop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 4
  Mono: Playback 4 [100%] [40.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 4
  Mono: Playback 4 [100%] [40.00dB] [on]
Simple mixer control 'Line In as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'

is there any other information I could supply that would be of help?
any suggestions? I already know my sound card is a problematic one, and already tried some suggested solutions for similar (not exactly same) problems found in other forums, with both dapper and edgy.

thanks in advance!!!

---

### Post by DrewB on 2007-05-08
Hi Scarab, 
I have a Gateway MX6440 laptop and I am getting the same problem as you with the screen brightness and volume Fn keys with Feisty.
The volume and brightness do adjust when I use the function keys but I get a "distrubance" or glitch, which is a  rectangular area of messed up pixels, in the top left hand corner of the screen. Also, I get a volume bar when I adjust the volume but no brightness bar when I adjust the brightness.
Did you ever find a solution to this?
Any help anyone can provide would be very gratefully received.
Thanks

---

### Post by icechen1 on 2007-05-08
> **DrewB said:**
> Hi Scarab, 
I have a Gateway MX6440 laptop and I am getting the same problem as you with the screen brightness and volume Fn keys with Feisty.
The volume and brightness do adjust when I use the function keys but I get a "distrubance" or glitch, which is a  rectangular area of messed up pixels, in the top left hand corner of the screen. Also, I get a volume bar when I adjust the volume but no brightness bar when I adjust the brightness.
Did you ever find a solution to this?
Any help anyone can provide would be very gratefully received.
Thanks

Hello,I have the same laptop as yours and has the same problem.

---

### Post by bobbydale on 2007-05-09
I have the same problem with my Gateway laptop.

---

### Post by icechen1 on 2007-05-09
Looks like most inboard sound card cant use microphone :(

---

### Post by treesurf on 2007-05-21
Hda Intel/Sigmatel microphones on Gateway laptops seem to be a complete loss as far as I can tell, and I've tried just about everything I could find on this forum and others.

---

