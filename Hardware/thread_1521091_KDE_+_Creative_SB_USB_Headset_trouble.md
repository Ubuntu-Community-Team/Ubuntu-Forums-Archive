---
title: "KDE + Creative SB USB Headset trouble"
date: 2010-06-30
forum: Hardware
---

### Post by JohnHeikkila on 2010-06-30
Okay, so I have this Creative SB ARENA USB headset, and I used to prefer booting my Ubuntu (doesn't work anymore :sad: ), and it was easy to switch using to the USB headset, just a few clicks, opening the audio manager thingy and clicked some selections.

That doesn't work on Kubuntu. I can't find the correct settings anywhere, not from the KDE audio mixer, not from the System settings...Nowhere. The sound comes from my laptop's internal speakers and I need to plug the microphone to my audio card for it to work.

**aplay -L:**
```
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
front:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    SB Arena Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```

**System specs:**
```
Acer Aspire 5520
AMD Athlon® 64 X2 dual-core TK-57 (1.9GHz, 2x 256 KB L2 cache/memory)
1407MB Graphics Driver cache/memory
NVIDIA® GeForce® 7000M
4GB DDR2
```

---

### Post by JohnHeikkila on 2010-07-06
Bump.

---

