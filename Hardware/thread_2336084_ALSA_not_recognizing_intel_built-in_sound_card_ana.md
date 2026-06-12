---
title: "ALSA not recognizing intel built-in sound card analog output (only HDMI)"
date: 2016-09-04
forum: Hardware
---

### Post by abdo88 on 2016-09-04
Hi,

I am having trouble getting sound to work on my all-in-one HP envy computer. If I am not mistaken, I managed to narrow down the problem to alsa not recognizing my sound card analog output. I am running Ubuntu 16.04 LTS with kernel 4.4.0-36-generic.

In **pavucontrol**, the configuration tab, I only have HDMI output (unplugged).

This is the output of **aplay -l**:

> 
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


This is the output of **aplay -L**

> 
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions


I tried installing dkms and oem-daily-* but the result was my card not being recognized at all. I also tried reinstall --purge alsa-base alsa-source alsa-utils pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils pulseaudio-module-gconf pulseaudio-module-zeroconf.

This is the audio entry of lspci -k:

> 
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
	DeviceName: Onboard Audio
	Subsystem: Hewlett-Packard Company Sunrise Point-H HD Audio
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


This is the output of alsa-info.sh [http://www.alsa-project.org/db/?f=70614b6b148cefa5fa13a2991c010a3798301602](http://www.alsa-project.org/db/?f=70614b6b148cefa5fa13a2991c010a3798301602)

Any help is appreciated.

---

