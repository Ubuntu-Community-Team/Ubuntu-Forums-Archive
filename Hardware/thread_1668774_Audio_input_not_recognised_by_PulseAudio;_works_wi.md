---
title: "Audio input not recognised by PulseAudio; works with ALSA."
date: 2011-01-16
forum: Hardware
---

### Post by Graham A on 2011-01-16
[FONT=Georgia]I believe this is a similar issue to the one described in this thread here: [http://ubuntuforums.org/showthread.php?t=1504904](http://ubuntuforums.org/showthread.php?t=1504904).

Since newer versions of **Skype** only support PulseAudio, I'm forced to use it for my audio I/O which is fine and dandy for playing sounds, output works a treat in PA and all other applications. However it does not believe me that there is audio input. This is the device I use for my audio. (Integrated [/FONT] [FONT=Georgia]**VIA VT1708S** audio codec 8-channel audio on an **ASUS M4A785TD-M EVO**).

[/FONT]```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```[FONT=Georgia]

Using the command [/FONT] [FONT=Georgia]**$ arecord -f dat -d 20 -D hw:0,0 test.wav** I'm able to record my voice into the .WAV file *which I can hear playback clearly!* Obviously my sound card works with ALSA. Using the command **$ arecord -l** I'm able to get this output.

[/FONT]```
**** List of CAPTURE Hardware Devices **** 
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```Here's some useful ALSA output.
[FONT=Georgia][http://www.alsa-project.org/db/?f=5e...532a9d75ec54b2]("http://www.alsa-project.org/db/?f=5efe65dfd4ae6a64030745347a532a9d75ec54b2")[/FONT]

---

