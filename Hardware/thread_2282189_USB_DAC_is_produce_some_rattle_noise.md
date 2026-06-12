---
title: "USB DAC is produce some rattle noise"
date: 2015-06-12
forum: Hardware
---

### Post by surtr4 on 2015-06-12
OK, here is the story. I have a JDS Lab. C5D USB DAC for about a  year, and yesterday I wanted to try Ubuntu 14.04. So, I installed  Ubuntu, did some updates and connected DAC (sudo alsa reload and killall pulseaudio command were been used).

  After I entered in "***Sound settings***" menu and selected Analog Output for C5D, I'm tried test sound. "***Left Front***" and "***Right Front***" sound produced as "***Hrrr Hrrrr***" and "***Hrrrr Hrrrr***". I even tried to play some music and video - same result.

  Maybe it's a DAC problem? So i loaded Windows and then Kali Linux, it's worked perfectly in both. 

  After return to Ubuntu i was trying to see if system recognize DAC properly, so this is output for some command:

```


$ lsusb
Bus 002 Device 004: ID 1532:010d Razer USA, Ltd
Bus 002 Device 008: ID 262a:1120                      <-------------THIS IS C5D
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 004: ID 0480:a207 Toshiba America Info. Systems, Inc.
Bus 001 Device 003: ID 1038:1369 Ideazon, Inc.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DS [Xonar DS], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DS [Xonar DS], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: DAC [C5D Amp DAC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=DS
    Xonar DS, Multichannel
    Default Audio Device
front:CARD=DS,DEV=0
    Xonar DS, Multichannel
    Front speakers
surround40:CARD=DS,DEV=0
    Xonar DS, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DS,DEV=0
    Xonar DS, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DS,DEV=0
    Xonar DS, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DS,DEV=0
    Xonar DS, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DS,DEV=0
    Xonar DS, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DS,DEV=0
    Xonar DS, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DS,DEV=0
    Xonar DS, Multichannel
    Direct sample mixing device
dmix:CARD=DS,DEV=1
    Xonar DS, Digital
    Direct sample mixing device
dsnoop:CARD=DS,DEV=0
    Xonar DS, Multichannel
    Direct sample snooping device
dsnoop:CARD=DS,DEV=1
    Xonar DS, Digital
    Direct sample snooping device
hw:CARD=DS,DEV=0
    Xonar DS, Multichannel
    Direct hardware device without any conversions
hw:CARD=DS,DEV=1
    Xonar DS, Digital
    Direct hardware device without any conversions
plughw:CARD=DS,DEV=0
    Xonar DS, Multichannel
    Hardware device with all software conversions
plughw:CARD=DS,DEV=1
    Xonar DS, Digital
    Hardware device with all software conversions
sysdefault:CARD=PCH
    HDA Intel PCH, ALC889 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=DAC
    C5D Amp DAC, USB Audio
    Default Audio Device
front:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    Front speakers
surround40:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    Direct sample mixing device
dsnoop:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    Direct sample snooping device
hw:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DAC,DEV=0
    C5D Amp DAC, USB Audio
    Hardware device with all software conversions

$ cat /proc/asound/cards
 0 [PCH]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfbff4000 irq 48
 1 [NVidia]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfaffc000 irq 17
 2 [DS]: AV200 - Xonar DS
                      Asus Virtuoso 66 at 0xdc00, irq 16
 3 [DAC]: USB-Audio - C5D Amp DAC
                      JDS Labs Inc C5D Amp DAC at usb-0000:00:1d.0-1.4, full speed

```

So DAC recognized properly. Is it probably ALSA driver?

  Any suggestions friends? And sorry for my bad English ;)

---

### Post by livewirebt2 on 2015-08-03
You should have stated that you also asked a question on [AskUbuntu.]("http://askubuntu.com/q/635535/40581")

---

