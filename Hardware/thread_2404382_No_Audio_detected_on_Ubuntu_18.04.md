---
title: "No Audio detected on Ubuntu 18.04"
date: 2018-10-23
forum: Hardware
---

### Post by closequarters8 on 2018-10-23
This is a new Build that I have, with ASUS Prime x470 Motherboard with AMD Ryzen-7. This is with UBUNTU 18.04
It seems the ASUS Motherboard comes with the Realtek HD Audio, But with my Pulse Audio Volume Control I do not see this detected.. Nor am I able to hear any default sounds as well here ? Completely Unsure on what needs to be installed, 

Giving the Output of the relevant Commands 

**aplay -L**

```

default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Hardware device with all software conversions
sysdefault:CARD=Generic
    HD-Audio Generic, ALC1220 Analog
    Default Audio Device
front:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    Front speakers
surround21:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    Direct sample mixing device
dmix:CARD=Generic,DEV=1
    HD-Audio Generic, ALC1220 Digital
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=1
    HD-Audio Generic, ALC1220 Digital
    Direct sample snooping device
hw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC1220 Digital
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC1220 Analog
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC1220 Digital
    Hardware device with all software conversions

```

**lspci -v | grep Audio** --> this Output does not show the Realtek audio ? 

```

09:00.1 Audio device: NVIDIA Corporation GP102 HDMI Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. GP102 HDMI Audio Controller
0b:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Family 17h (Models 00h-0fh) HD Audio Controller

```


**PulseAudio Volume Controller Images are attached to check those configurations**

---

### Post by closequarters8 on 2018-10-26
Solved Using Pulse Audio Controller and Alsamixer mostly. Fiddled around it for a long time till there was output , plugged in the output to a speaker system .

---

