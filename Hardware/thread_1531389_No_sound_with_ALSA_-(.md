---
title: "No sound with ALSA :-("
date: 2010-07-14
forum: Hardware
---

### Post by frenchn00b on 2010-07-14
I boot with /etc/modprobe.d/sound.conf
(avoid pulseaudio, since all rely on alsa and it should be supported somehow by alsa)

 $ cat /etc/modprobe.d/sound.conf
```
# remove this file if you would like to make alsa automatic and not manual
## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
alias snd-card-3 snd-usb-audio

## module options should go here
options snd-hda-intel index=0 model=ref
options snd-usb-audio index=3

```


I get.

> ~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Live
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! [Unknown], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
 
$ lsusb
Bus 002 Device 006: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 002 Device 005: ID 04f3:0216 Elan Microelectronics Corp.
Bus 002 Device 004: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge
Bus 001 Device 004: ID 147a:e017 Formosa Industrial Computing, Inc. eHome Infrared Receiver
Bus 001 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



alsamixer :
  >  &#9474;0  USB camera   &#9474;1  SB Live! [Unknown]  &#9474; 2  SAA7134    &#9474;3  AK5370    &#9474;   enter device name...&#9474;                                                                                            &#9474;&#9474;                                                                                           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;             &#9484;&#9472;&#9472;&#9472;&#9472;&#9472; Sound Card &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                                                                                            &#9474;&#9474;                                                                                           &#9474;-  (default)           &#9474;                                                                                            &#9474;&#9474;                                                                                           &#9474;0  USB camera          &#9474;                                                                                            &#9474;&#9474;                                                                                           &#9474;1  SB Live! [Unknown]  &#9474;                                                                                            &#9474;&#9474;                                                                                           &#9474;2  SAA7134             &#9474;                                                                                            &#9474;&#9474;                                                                                           &#9474;3  AK5370              &#9474;                                                                                            &#9474;&#9474;                                                                                           &#9474;   enter device name...&#9474;                                                                                            &#9474;&#9474;                                                                                           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                                                                                            &#9474;&#9474;                                                                               &#9474;0  USB camera 1  SB Live! [Unknown] &#9474;2  SAA7134   &#9474;3  AK5370  



[B]this is surely not waht I want, because I have no sound first,
and second the card frmo my mother board is not there, so, alsa order again ?

[/B]

[B]
I want at every boots (how can it be done, hwo to evtl.modify sound.conf file):[/B]
0  HDA Intel 
1  SB Live! [Unknown
2  SAA7134 
3  AK5370 
4  USB camera 
  enter device name..

How to do such impossible thing with alsa ?

It should give that :> 
~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC889 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI
    HDMI Audio Output
default:CARD=Live
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! [Unknown], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! [Unknown], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output





Best regards

---

