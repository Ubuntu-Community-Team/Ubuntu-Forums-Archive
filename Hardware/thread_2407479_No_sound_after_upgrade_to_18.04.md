---
title: "No sound after upgrade to 18.04"
date: 2018-12-04
forum: Hardware
---

### Post by Polaka on 2018-12-04
(Sorry for my poor English)

I have speakers connected by audio jack and they work fine, but since I installed Ubuntu 18.04 I can only hear de sound effects of the system (no audio player, browser, etc). The same happens when I connect the tv via HDMI: the system recognizes the new audio connection, the screen works ok, but the sound effects sound on the speakers, not on the tv. When I disconnect the speakers and reconnect the tv, nothing works (only the screen).

Alsamixer recognizes the sound card (HDA ATI HDMI, Chip ATI R6xx), but the volume controls don't appear (only "[00] S/PDIF"). If I select HD-Audio Generic card, the bars appear, but the problem continues.

I tried to restart and resintall ALSA and PulseAudio. Nothing.

> ~$ lspci | grep -i audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)


~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevice: 1/1
  Subdevice #0: subdevice #0


~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=Generic
    HD-Audio Generic, ALC887-VD Analog
    Default Audio Device
front:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Front speakers
surround21:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct sample snooping device
hw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Hardware device with all software conversions


~$ speaker-test -D sysdefault

speaker-test 1.1.3

Playback device is sysdefault
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:1052: (snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory

---

