---
title: "Traktor DJ Audio 2  - Ubuntu 13.10 - No controls"
date: 2013-11-09
forum: Hardware
---

### Post by MikaelHolber on 2013-11-09
Hi,

After reinstalling Ubuntu from 13.04 to 13.10 my **Native Instruments Traktor DJ Audio 2** have stopped working. 

With 12.10 and 13.04 the card worked out-of-the-box with **snd-usb-caiaq**. The same driver is loaded but alsamixer show no controls. 

Any ideas?
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.27.1 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Traktor Audio 2                                F1:  Help               &#9474;
&#9474; Chip: Traktor Audio 2                                F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item:                                                Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                This sound device does not have any controls.

```

```
cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa0610000 irq 47
 1 [TraktorAudio2  ]: snd-usb-caiaq - Traktor Audio 2
                      Native Instruments Traktor Audio 2 (usb-0000:00:14.0-2)
```
```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version k3.11.0-13-generic.
```

```
aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, CS4206 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, CS4206 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions
sysdefault:CARD=TraktorAudio2
    Traktor Audio 2, Traktor Audio 2
    Default Audio Device
dmix:CARD=TraktorAudio2,DEV=0
    Traktor Audio 2, Traktor Audio 2
    Direct sample mixing device
dsnoop:CARD=TraktorAudio2,DEV=0
    Traktor Audio 2, Traktor Audio 2
    Direct sample snooping device
hw:CARD=TraktorAudio2,DEV=0
    Traktor Audio 2, Traktor Audio 2
    Direct hardware device without any conversions
plughw:CARD=TraktorAudio2,DEV=0
    Traktor Audio 2, Traktor Audio 2
    Hardware device with all software conversions
```

---

### Post by tgalati4 on 2013-11-09
Maybe the switches of the module changed slightly:


tgalati4@tpad-Gloria7 ~ $ modinfo snd-usb-caiaq
filename:       /lib/modules/2.6.28-19-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
license:        GPL
description:    caiaq USB audio, version 1.3.8
author:         Daniel Mack <daniel@caiaq.de>
srcversion:     414C0ABA0559D8E2244931C
alias:          usb:v17CCp1915d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp1978d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp0815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp4712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp4711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp1940d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v17CCp1969d*dc*dsc*dp*ic*isc*ip*
depends:        snd-pcm,snd-rawmidi,snd
vermagic:       2.6.28-19-generic SMP mod_unload modversions 586 
parm:           index:Index value for the caiaq sound device (array of int)
parm:           id:ID string for the caiaq soundcard. (array of charp)
parm:           enable:Enable the caiaq soundcard. (array of bool)

---

### Post by MikaelHolber on 2013-11-24
Hi,

It seems like they have changes somewhat:

```
modinfo snd-usb-caiaq
filename:       /lib/modules/3.11.0-14-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
license:        GPL
description:    caiaq USB audio
author:         Daniel Mack <daniel@caiaq.de>
srcversion:     D3E87D99A327CB222A7B523
alias:          usb:v17CCp0808d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp041Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCpBAFFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp2305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp041Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp0839d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp0D8Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp1915d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp1978d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp0815d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp4712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp4711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp1940d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v17CCp1969d*dc*dsc*dp*ic*isc*ip*in*
depends:        snd-pcm,snd,snd-rawmidi
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           index:Index value for the caiaq sound device (array of int)
parm:           id:ID string for the caiaq soundcard. (array of charp)
parm:           enable:Enable the caiaq soundcard. (array of bool)

```

How do you change this?

Kind regards
Mikael

---

