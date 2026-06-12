---
title: "Nvidia Geforce 9800m gts hdmi sound not working"
date: 2009-11-27
forum: Hardware
---

### Post by shiinto on 2009-11-27
I've been reading and trying for about 3 weeks to get my hdmi audio to work. Nothing has worked yet... I've rebuilt AlSA about 3 times now, changed the alsamixer settings a couple of times. 

Currently i'm useing the Nvidia 190.42 driver with the alsa 1.0.21 driver...

Another thing when i do aplay -l i get this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L outputs this:

default:CARD=Intel
    HDA Intel, CONEXANT Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


Any help with this would be much appreciated...

---

