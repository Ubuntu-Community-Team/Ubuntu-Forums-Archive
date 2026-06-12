---
title: "PLZ HELP tx211nr audio setup"
date: 2008-06-28
forum: Hardware
---

### Post by sgtsquatlow on 2008-06-28
Hi, this is my first post so ill try and keep things simple. I've looked around and havnt as of yet found out how to configure my audio and or find a driver. When i check hp it says im using the Realtek ALC861-VD chip. When i start up grub the speaker button that lights up, is lit up, but when xubuntu loads it turns red or what ever. aplay -l shows:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L: somewhat long

default:CARD=NVidia
    HDA NVidia, ALC861VD Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC861VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

/proc/asound/devices reads:
 0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer

Thanks a ton for your help,
SgtSquatlow

---

### Post by sgtsquatlow on 2008-06-30
I take it no one has had this problem lately. Any suggestions would be appreciated.  Ohh and by the way i miss typed the title its actually for an hp tx2115nr.

---

