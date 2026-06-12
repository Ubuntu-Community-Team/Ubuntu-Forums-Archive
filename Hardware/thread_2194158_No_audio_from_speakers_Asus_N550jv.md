---
title: "No audio from speakers Asus N550jv"
date: 2013-12-16
forum: Hardware
---

### Post by Bisneff on 2013-12-16
Hi everyone

I have an asus n550jv. 

After install Ubuntu 12.04 everything worked fine. (I didn't erase Windows 8 partition)

Today I was trying to make the SonicMaster work then I start to follow some links online.

[http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm](http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm)

I do what the second answer say and... first I have problems with system, it report a bug on pulseaudio. Then I try to erase the line I added in the files, but my speakers stopped to works.

The headphones works. 

I try to format and reinstall Ubuntu, but I still have no sound from speakers...


Can someone help me?

Thank you

I add some :

[http://www.alsa-project.org/db/?f=32e3c129faec0280f3746b106d27ef14c9638e29](http://www.alsa-project.org/db/?f=32e3c129faec0280f3746b106d27ef14c9638e29)

> :~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
> 

:~$ lspci -v | grep -A7 -i "audio"
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Intel Corporation Device 2010
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f7a14000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 11cd
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel



> ~$ amixer -c 0
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]



> :~$ amixer -c 1
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 38 [60%] [11.25dB] [on]
  Front Right: Capture 38 [60%] [11.25dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'



this is my /etc/asound.conf
> 
defaults.ctl.card 1
defaults.pcm.card 1
defaults.timer.card 1

> :~$ cat  /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel



---

### Post by mörgæs on 2013-12-17
Have you tried 13.10?
It's a brand-new notebook and it deserves the newest software.

---

