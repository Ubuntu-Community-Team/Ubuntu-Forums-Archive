---
title: "IEC958 question"
date: 2008-09-22
forum: General Help
---

### Post by lavacano on 2008-09-22
aplay -L
Code:

default:CARD=Audigy2
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)



so is there any way to route all channels of surround51, or any other surround* ro IEC958

-or-

is there any way to make IEC958 behave like surround* (speaker-test -c8 or -c6)
when I use speaker-test -c6 my IEC958 transmits for front left and fron right but ALL other channels do NOT transmit

I dont want to use IEC958 just for AC3 ar a52 upmixing for music
I want to use it for surround sound games in linux this is seriously pissing me off.

---

