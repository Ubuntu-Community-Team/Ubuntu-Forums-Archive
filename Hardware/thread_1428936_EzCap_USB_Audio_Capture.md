---
title: "EzCap USB Audio Capture"
date: 2010-03-13
forum: Hardware
---

### Post by fugazi32 on 2010-03-13
Hi guys, I'm looking at link up my turntables to my PC using EzCAP USB Audio Capture. It has been detected ok, and aplay -l lists:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And aplay -L gives:

```

default:CARD=SI7012
    SiS SI7012, SiS SI7012
    Default Audio Device
front:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    Front speakers
surround40:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Device
    USB PnP Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    USB PnP Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```

How do I configure it so I can capture audio, with something like *sound-recorder* or Audacity? I'm am using Xubuntu 8.10 still.
Any help would be much appreciated!

---

### Post by fugazi32 on 2010-03-15
Problem solved. ;)

---

### Post by emanaton on 2010-05-02
Greetings fugazi32,

Could you share those details with us?  =o)

Regards,

Sean

---

